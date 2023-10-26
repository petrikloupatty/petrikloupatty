<header class="top-navbar">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="home.php">
          <img src="images/logo6.png"width="150" height="120" alt="" />
        </a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbars-host" aria-controls="navbars-rs-food" aria-expanded="false" aria-label="Toggle navigation">
          <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbars-host">
          <ul class="navbar-nav ml-auto">
            <li class="nav-item"><a class="nav-link" href="index2.php">Home</a></li>
            <li class="nav-item active"><a class="nav-link" href="boking.php">Boking</a></li>
            <li class="nav-item dropdown">
              <a class="nav-link dropdown-toggle" href="inbo.php" id="dropdown-a" data-toggle="dropdown">Info Boking</a>
              
            </li>
        
          </ul>
          <ul class="nav navbar-nav navbar-right">
                        <li><a class="hover-btn-new log" href="logout.php"><span>Logout</span></a></li>
                    </ul>
        </div>
      </div>
    </nav>
  </header>
 
<?php
                     $SQL = "SELECT * FROM data_boking natural join data_user WHERE username=username";
                     $QUERY = mysqli_query($konek,$SQL);
                     while($data=mysqli_fetch_array($QUERY,MYSQLI_BOTH)){
                       $username = $data['username'];
                       $harga = $data['harga'];
                       $id= $data['id_boking'];
                   ;}  
                 ?>
<div class="all-title-box">
  <div class="container-scroller">
    <br>
      <div class="content d-flex align-items-center auth px-0">
        <div class="row w-100 mx-0">
          <div class="col-lg-4 mx-auto">
            <div class="auth-form-light text-center py-5 px-4 px-sm-5">
              <div class="brand-logo">
           
              </div>
              <div class='alert alert-info'>Pesanan Anda sedang kami proses<br>Silahkan Lakukan Pembayaran dan Upload Bukti Bayar Disini!</div>
    <br><br>
    <img src="images/logobni.png" width="250" height="150" >
    <br><br>
    <h2>A/N Waiheru Sport Center</h2>
    <h2>0768176175</h2>
    
    <form method="POST" enctype="multipart/form-data">
    <div class="form-group">
                 <label ><strong>Username : </strong></label>
      <input type="text" name="username" class="form-control" value="<?php echo $username;?>" readonly>
                     </div>
                     <div class="form-group">
                 <label ><strong>Harga : </strong></label>
      <input type="text" name="harga" class="form-control" value="<?php echo $harga;?>" readonly>
                     </div>
                     <div class="form-group">
                          <label><strong>Bukti Bayar :</strong></label>
                          <input type="file" name="gambar" class="form-control" size="37">
                        </div>
                <div class="mt-3">
                  <button type="submit" class="btn btn-block btn-success btn-lg font-weight-medium auth-form-btn" name="update">
                    Kirim
                  </button>
                </div>
                <div class="mb-2">
                  <a class="btn btn-block btn-danger btn-lg font-weight-medium auth-form-btn" href="index2.php">Close</a>
                </div>
              
              </form>
              
            </div>
        
          </div>
        </div>
        
      </div>
    
      <!-- content-wrapper ends -->
    </div>
    <!-- page-body-wrapper ends -->
  </div>
  <!-- container-scroller -->

  <?php
if(isset($_POST['update'])){
    $username =$_POST['username'];
    $harga =$_POST['harga'];

    $nama_gbr = isset($_FILES['gambar']);
    $file_gbr = $_POST['gambar']."".".jpg";
   $sql = "INSERT INTO bukti(username,harga,gambar) VALUES('$username','$harga','$file_gbr')";
    
  $query = mysqli_query($konek,$sql) or die(mysqli_error());

  
if($query){
  copy($_FILES['gambar']['tmp_name'],"./buktibyr/".$file_gbr);
  echo "<script language='javascript'>swal('Selamat...', 'Proses Berhasil', 'success');</script>" ;
  echo '<meta http-equiv="refresh" content="3; url=index2.php">';
  }else{
  echo "<script language='javascript'>swal('Gagal...', 'Proses Gagal', 'error');</script>" ;
  echo '<meta http-equiv="refresh" content="3; url=proses.php">';
  }
}

?>

  <!-- plugins:js -->
  <script src="main/vendors/base/vendor.bundle.base.js"></script>
  <!-- endinject -->
  <!-- inject:js -->
  <script src="main/js/off-canvas.js"></script>
  <script src="main/js/hoverable-collapse.js"></script>
  <script src="main/js/template.js"></script>
  <!-- endinject -->
  <script src="https://unpkg.com/sweetalert/dist/sweetalert.min.js"></script>
  <!-- endinject -->
  <script src="http://code.jquery.com/jquery-3.0.0.min.js"></script>
</body>
<footer class="footer">
        <div class="container">
            <div class="row">
                <div class="col-lg-4 col-md-4 col-xs-12">
                    <div class="widget clearfix">
                        <div class="widget-title">
                            <h3>About US</h3><br>
                            <ul class="footer-links-soi">
            
            <li><a href="https://m.facebook.com/profile.php?id=100039517803804"><i class="fa fa-facebook"> </i></a></li> &nbsp;&nbsp;
            <li><a href="https://www.instagram.com/waiheru.futsal/"><i class="fa fa-instagram"></i></a></li><br>
                        call center : +(0911) 346789
                </div><!-- end col -->

        
            </div><!-- end row -->
        </div><!-- end container -->
    </footer><!-- end footer -->
</html>



<?php include '../konek.php'; ?>
<title>Tambah User</title>
  <!-- Google Font: Source Sans Pro -->
  <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Source+Sans+Pro:300,400,400i,700&display=fallback">
  <!-- Font Awesome Icons -->
  <link rel="stylesheet" href="plugins/fontawesome-free/css/all.min.css">
  <!-- overlayScrollbars -->
  <link rel="stylesheet" href="plugins/overlayScrollbars/css/OverlayScrollbars.min.css">
  <!-- Theme style -->
  <link rel="stylesheet" href="dist/css/adminlte.min.css">
  <div class="sidebar">
      <!-- Sidebar user panel (optional) -->
      <div class="user-panel d-flex">
        <div class="image">
      
        </div>
        <div class="info">
    
        </div>
      </div>
  <!-- Main Sidebar Container -->

 
      <!-- SidebarSearch Form -->
      

      <body class="hold-transition dark-mode sidebar-mini layout-fixed layout-navbar-fixed layout-footer-fixed">
<div class="wrapper">

  <!-- Preloader -->
  <div class="preloader flex-column justify-content-center align-items-center">
    <img class="animation__wobble" src="dist/img/AdminLTELogo.png" alt="AdminLTELogo" height="60" width="60">
  </div>

  <!-- Navbar -->
  <nav class="main-header navbar navbar-expand navbar-dark">
    <!-- Left navbar links -->
    <ul class="navbar-nav">
      <li class="nav-item">
        <a class="nav-link" data-widget="pushmenu" href="#" role="button"><i class="fas fa-bars"></i></a>
      </li>
      <li class="nav-item d-none d-sm-inline-block">
  
      </li>
        </ul>

    <!-- Right navbar links -->
    <ul class="navbar-nav ml-auto">
      <!-- Navbar Search -->
   

   
      <li class="nav-item">
        <a class="nav-link" data-widget="fullscreen" href="#" role="button">
          <i class="fas fa-expand-arrows-alt"></i>
        </a>
      </li>
      <li class="nav-item">
        <a class="nav-link" data-widget="control-sidebar" data-slide="true" href="#" role="button">
          <i class=""></i>
        </a>
      </li>
    </ul>
  </nav>
  <!-- /.navbar -->
<!-- Main Sidebar Container -->
<aside class="main-sidebar sidebar-dark-primary elevation-1">
    <!-- Brand Logo -->
     <div class="sidebar">
      <!-- Sidebar user panel (optional) -->
      <div class="user d-flex">
        <div class="image">
        <img src="dist/img/logo6.png"width="80" height="80">
        </div>
        <div class="info">
          <a href="#" class="d-block">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Waiheru Sport <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Center</a>
        </div>
      </div>

    <!-- Sidebar -->
    <div class="sidebar">
      <!-- Sidebar user panel (optional) -->
      <div class="user-panel d-flex">
        <div class="image">
      
        </div>
        <div class="info">
    
        </div>
      </div>
  <!-- Main Sidebar Container -->

 
      <!-- SidebarSearch Form -->
      

      <!-- Sidebar Menu -->
      <nav class="mt-2">
        <ul class="nav nav-pills nav-sidebar flex-column" data-widget="treeview" role="menu" data-accordion="false">
          <!-- Add icons to the links using the .nav-icon class
               with font-awesome or any other icon font library -->
               <li class="nav-item ">
            <a href="index.php" class="nav-link">
              <i class="nav-icon fas fa-tachometer-alt"></i>
              <p>
                Dashboard
               
              </p>
            </a>
         
          <li class="nav-item">
            <a href="tampil_user.php" class="nav-link">
              <i class="nav-icon fas fa-fw fa-user"></i>
              <p>
                Data User
                  </p>
            </a>
          </li>
          <li class="nav-item">
            <a href="tampil_lapangan.php" class="nav-link active">
              <i class="nav-icon fas fa-table"></i>
              <p>
               Data Lapangan
              </p>
            </a>
             </li>
             <li class="nav-item">
            <a href="tampil_boking.php" class="nav-link">
              <i class="nav-icon fas fa-columns"></i>
              <p>
                Data Boking
              </p>
            </a>
          </li>
          <li class="nav-item">
            <a href="tampil_invoice.php" class="nav-link">
              <i class="nav-icon fas fa-book"></i>
              <p>
               Invoice
              </p>
            </a>
</li>        
          <li class="nav-item">
            <a href="tampil_pesan.php" class="nav-link">
              <i class="nav-icon far fa-envelope"></i>
              <p>
                Pesan
               
              </p>
            </a>
           
          </li>
          <li class="nav-item">
            <a href="logout.php" class="nav-link">
              <i class="nav-icon far fa-envelope"></i>
              <p>
              Logout
               
              </p>
            </a>
           
          </li>
       
       
          
        </ul>
      </nav>
      <!-- /.sidebar-menu -->
    </div>
    <!-- /.sidebar -->
  </aside>

  <!-- Content Wrapper. Contains page content -->
  <div class="content-wrapper">
    <!-- Content Header (Page header) -->
    <div class="content-header">
      <div class="container-fluid">
        <div class="row mb-2">
          <div class="col-sm-6">
          
          </div><!-- /.col -->
      
        </div><!-- /.row -->
      </div><!-- /.container-fluid -->
    </div>
    <!-- /.content-header -->

    <section class="content">
      <div class="container-fluid">
        <div class="row">
          <!-- left column -->
          <div class="col-md-6">
            <!-- general form elements -->
            <div class="card card-success">
              <div class="card-header">
                <h3 class="card-title">Tambah Pengguna</h3>
              </div>
              <!-- /.card-header -->
              <!-- form start -->
              <form method="POST" enctype="multipart/form-data">
                <div class="card-body">
                <div class="form-group">
                    <label>Username : </label>
                    <input type="text" class="form-control" name="username" value="">
                  </div>
                  <div class="form-group">
                    <label">Nama  : </label>
                    <input type="text" class="form-control" name="nama" value="">
                  </div>
                  <div class="form-group">
                    <label>alamat : </label>
                    <input type="text" class="form-control" name="alamat" value="">
                  </div>
                  <div class="form-group">
                    <label">Jenis Kelamin  : </label>
                    <select name="jekel" id="" class="form-control">
                    <option value="Laki-Laki">Laki-Laki</option>
          <option value="Perempuan">Perempuan</option>
                  </select>
                  </div>
                  <div class="form-group">
                  <label>Email : </label>
                    <input type="text" class="form-control" name="email" value="">
                  </div>
                  <div class="form-group">
                    <label">No Tlp  : </label>
                    <input type="number" class="form-control" name="telepon" value="">
                  </div>
                  <div class="form-group">
                    <label>Password : </label>
                    <input type="text" class="form-control" name="password" value="">
                  </div>
                  <div class="form-group">
                    <label>Hak Akses : </label>
                    <select name="hak_akses" class="form-control">
          <option value="User">User</option>
          <option value="Admin">Admin</option>
        </select>
                  </div>
                  </div>
                
                <!-- /.card-body -->

                <div class="card-footer">
                  <button type="submit" class="btn btn-success" name="simpan">Simpan</button>
                  <a class="btn btn-danger"  href="http://localhost/futsal/demo/tampil_user.php">Batal</a>
              
                </div>
              </form>
            </div>

 <?php
if(isset($_POST['simpan'])){
  $username = $_POST['username'];
  $nama = $_POST['nama'];
  $alamat = $_POST['alamat'];
  $jekel = $_POST['jekel'];
  $email = $_POST['email'];
     $telepon = $_POST['telepon'];
  $password = $_POST['password'];
  $hak_akses = $_POST['hak_akses'];
    $sql = "INSERT INTO data_user (username,password,hak_akses,nama,jekel,alamat,email,telepon) VALUES ('$username','$password','$hak_akses','$nama','$jekel','$alamat','$email','$telepon')";
  $query = mysqli_query($konek,$sql);

  if($query){
    echo "<script language='javascript'>swal('Selamat...', 'Ubah Berhasil', 'success');</script>" ;
    echo '<meta http-equiv="refresh" content="3; url=tampil_user.php">';
    }else{
    echo "<script language='javascript'>swal('Gagal...', 'Ubah Gagal', 'error');</script>" ;
    echo '<meta http-equiv="refresh" content="3; url=tampil_user.php">';
