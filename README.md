//<?php
if (isset($_FILES["file"]["name"])) {

    $name = $_FILES["file"]["name"];
	$newName = "vidur_name";
	$ext = "png";
    $tmp_name = $_FILES['file']['tmp_name'];
    $error = $_FILES['file']['error'];

    if (!empty($name)) {
		//Path to folder to which file will upload
        $location = "D:\\xampp\\htdocs\\chetan\\vidur\\bharti\\11\\";

		if(!is_dir($location)){
			mkdir($location,0777, true);
		}
		
		if ($_FILES["file"]["size"] > 500000) {
			echo "Sorry, your file is too large.";
			exit();
		}
		
		$target_file = $location . basename($_FILES["file"]["name"]);
		$imageFileType = strtolower(pathinfo($target_file,PATHINFO_EXTENSION));
		if($imageFileType != "jpg"  && $imageFileType != "png" && $imageFileType != "jpeg"
			&& $imageFileType != "gif" ) {
		echo "Sorry, only JPG, JPEG, PNG & GIF files are allowed.";
		exit();
		}
		
		
		
        if  (move_uploaded_file($tmp_name, $location."$newName.$ext")){
			echo $tmp_name;
			echo $location.$name;
            echo 'Uploaded';
        }

    } else {
        echo 'please choose a file';
    }
}
?>

<html>
   <body>
      
      <form action="" method="POST" enctype="multipart/form-data">
         <input type="file" name="file" />
         <input type="submit"/>
      </form>
      
   </body>
</html>
