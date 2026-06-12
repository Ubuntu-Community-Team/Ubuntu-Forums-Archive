---
title: "Problems with php/GD on Apache2 Ubuntu 8.04"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by chrisdee on 2009-05-14
I have problems running the script below. My server's url is posted to the browser rather than the image. Other than with GD PHP works just fine. Any ideas how to fix this ?

[PHP]
<?php
header ('Content-type: image/png');
$im = @imagecreatetruecolor(120, 20)
      or die('Cannot Initialize new GD image stream');
$text_color = imagecolorallocate($im, 233, 14, 91);
imagestring($im, 1, 5, 5,  'A Simple Text String', $text_color);
imagepng($im);
imagedestroy($im);
?>
[/PHP]

---

### Post by chrisdee on 2009-05-14
To be precise it outputs the following in the browser :

[http://www.myhostname.com/test.php](http://www.myhostname.com/test.php)


Note the above is not my actual url, it's just to illustrate what the script does.

---

### Post by chrisdee on 2009-05-15
Could it be some problem with the GD library ?

---

### Post by chrisdee on 2009-05-15
Solved. I did not have GD enabled. This worked for me :

[http://ubuntuforums.org/showthread.php?p=6226611#post6226611](http://ubuntuforums.org/showthread.php?p=6226611#post6226611)

---

