---
title: "Installing Linux without USB/CD"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by chris1neji on 2010-03-13
Ok so when i first install windows7 i had the ISO file and all i did was extracted with WinRAR. Went trough the installation process and all that and i got windows7 working.

I bough a new HDD so i partition this new HDD 1 for Win7 and other for Linux. My old or current HDD will be used for storage of media/backups and such

So i have a folder with Linux completely extracted *look at capture 1 images*
So i ran Wubi
I got a window *look at size* and i got confused with the Installation Size... What does that mean ??? or will do ? i Already told it to install in L drive which is 34GBs

BTW would this method of installation even work? Keep in mind i am currently running windows 7.

Look at my 2part image 
Basically i had win7 before after this new HDD i added windows7 on new drive (using same method i want to use with Linux)

---

### Post by Old_Grey_Wolf on 2010-03-13
I don't think you can use WUBI to install Ubuntu that way. Here is the WUBI FAQ for installation, [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php).

You probably created an unnecessary Linux partition on your new HDD.

Edit: in the FAQ it tells you that you can use LVPM to transfer your WUBI install to its own partition after you have installed it.

---

### Post by The Real Dave on 2010-03-13
Instead of extracting the ISO, try mounting it using some VirtualCD software? That way the ISO will act just as if it was an actual CD in your CD Drive, it won't know the difference :)

[Here's a VirtualCD Program]("http://www.howtogeek.com/howto/windows-vista/mount-an-iso-image-in-windows-vista/"), but I just Googled it, I've no experience with it :)

---

