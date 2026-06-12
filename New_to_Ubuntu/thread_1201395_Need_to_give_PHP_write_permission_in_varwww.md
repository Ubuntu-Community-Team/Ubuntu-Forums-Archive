---
title: "Need to give PHP write permission in var/www"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by facehead on 2009-07-01
Hi, I apologize if this is the wrong forum for this.

I've recently installed Apache and PHP and have been doing the tutorials over at w3schools for PHP. There is one particular one about uploading files where this error is returned:
[B]
Warning: move_uploaded_file(upload/picture.jpg) [function.move-uploaded-file]: failed to open stream: Permission denied in /var/www/uploadfile.php on line 25[/B]

I can create files and folders in /var/www/ but I have no idea how to give PHP access to do the same thing. Any help?

Here is the code, taken from the tutorial:

> <?php
if ((($_FILES["file"]["type"] == "image/gif")
|| ($_FILES["file"]["type"] == "image/jpeg")
|| ($_FILES["file"]["type"] == "image/pjpeg"))
&& ($_FILES["file"]["size"] < 20000))
  {
  if ($_FILES["file"]["error"] > 0)
    {
    echo "Return Code: " . $_FILES["file"]["error"] . "<br />";
    }
  else
    {
    echo "Upload: " . $_FILES["file"]["name"] . "<br />";
    echo "Type: " . $_FILES["file"]["type"] . "<br />";
    echo "Size: " . ($_FILES["file"]["size"] / 1024) . " Kb<br />";
    echo "Temp file: " . $_FILES["file"]["tmp_name"] . "<br />";

    if (file_exists("upload/" . $_FILES["file"]["name"]))
      {
      echo $_FILES["file"]["name"] . " already exists. ";
      }
    else
      {
      move_uploaded_file($_FILES["file"]["tmp_name"],
      "upload/" . $_FILES["file"]["name"]);
      echo "Stored in: " . "upload/" . $_FILES["file"]["name"];
      }
    }
  }
else
  {
  echo "Invalid file";
  }
?> 

---

### Post by masux594 on 2009-07-01
have u try to give the permission of this folder to your user?

Sysc, A

---

### Post by facehead on 2009-07-01
Yeah, I have permission to that folder, as I've been creating all my PHP files and saving them into that directory.

---

### Post by AlexDudko on 2009-07-01
Try to show the full path to your upload directory "/var/www/upload".
It seems php looks for the directory, which doesn't exist.
Then a line in your code would look like this:
[PHP]move_uploaded_file($_FILES["file"]["tmp_name"],
"/var/www/upload/" . $_FILES["file"]["name"]);[/PHP]
Of course the directory /var/www/upload must be writable - mind permissions.

---

### Post by CyberJack on 2009-07-01
The problem is not that _you_ need write access to the upload directory but that the user which is running the web server needs write access.
If you are running apache2 you need to give the www-data user write access (which is default user to run apache2 under ubuntu).

---

### Post by facehead on 2009-07-01
CyberJack you were totally right! Thanks. I found this thread which gave me an idea of what I had to do:

[http://ubuntuforums.org/showthread.php?t=560592](http://ubuntuforums.org/showthread.php?t=560592)

---

