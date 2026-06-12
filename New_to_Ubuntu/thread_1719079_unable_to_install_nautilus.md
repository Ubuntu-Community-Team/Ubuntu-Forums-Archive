---
title: "unable to install nautilus"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by zaafar on 2011-04-01
hi , i ve recently migrated to ubuntu10.10 and was looking for a software to make some jgp image size small. i heard of nautilus , but for some reason i am unable to install it , pls help , btw  i have already tried this method (found on a website)
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by TonKi on 2011-04-01
Nautilus is the default filemanager in Ubuntu - Nautilus Elementary (the ppa you added is an enhanced version of it and will install as an update. (you need to run 'sudo apt-get upgrade' to have the updates installed)

Do you want to change just the image-file-size or the image resolution?

---

### Post by zaafar on 2011-04-01
actually i m trying to upload some jpg images but the size is too large for my internet connection , and i read somewhere that nautilus can make image size small .

---

### Post by Enigmapond on 2011-04-01
> **zaafar said:**
> actually i m trying to upload some jpg images but the size is too large for my internet connection , and i read somewhere that nautilus can make image size small .

As TonKi stated, nautilus is just a file manager. If you are looking to re-size a .jpg, use an app like gthumb, GIMP or any other graphics app prior to uploading. You can also get a script that will allow nautilus to re-size.

---

### Post by Phil D. on 2011-04-01
Found my real account :)

[http://www.makeuseof.com/tag/linux-68-useful-extensions-to-improve-nautilus-functionality/]("http://www.makeuseof.com/tag/linux-68-useful-extensions-to-improve-nautilus-functionality/")
See the above link for nautilus extensions, number 4 is the image-converter.
Can be installed with 'sudo apt-get install nautilus-image-converter'

h2h

---

### Post by zaafar on 2011-04-01
thanx , worked really well :-)

---

### Post by sea_dawg on 2011-04-01
A quick and dirty way to down size images for uploading.  

1 - Display the image in any software you choose.  Double clicking an image on my system opens it in Eye of GNOME

2 - Open Accessories / Take Screenshot and choose "Select Area to Grab"

3 - Select the part of the image you want, save it and your're done!

This works because it creates a new image using your screen resolution rather than your camera's resolution.  You can also crop the image by selecting only the area you wish to upload.

For example I just used this on an original image of 3.4MB and got it down to 615KB in those 3 easy steps.  If I needed to take it down to < 100KB then I would have to use GIMP or another image editing application.

Variations of this method work in Windows and Mac OS as well.

---

### Post by zaafar on 2011-04-01
nice ,but as i found out nautilus method is better for multiple pics resizing.

---

