---
title: "Finding files on hardrive within windows"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by single.coil on 2009-03-24
hello everyone, first time poster, havent used ubuntu since 7.10, its changed a bit, looks nice runs even better. just wondering, all my music is on my other partition (or what ever you want to call it when you install ubuntu from within windows) and i want to access it, how do i do it?

---

### Post by eilios on 2009-03-24
Put your files on some sort of hosting site(Megaupload, Rapidshare, etc) as a .zip file and open it with 7zip.
OR
Use a usb jump drive and put your files on there, then put it back in on Ubuntu.

---

### Post by single.coil on 2009-03-24
i could do that, but i dont want to keep wasting HD space. As im duel booting windows vista at the moment. And ya i know Microsoft is the devils dick, but i dont have much of a choice with school currently

---

### Post by mikechant on 2009-03-24
According to this:
[http://ubuntuforums.org/archive/index.php/t-914358.html](http://ubuntuforums.org/archive/index.php/t-914358.html)

Your windows drive should be accessable as /host in the Ubuntu filesystem.

---

### Post by thehouseofho on 2009-03-24
If you installed Ubuntu inside of Windows using wubi, you can access all of the files within Windows by going to the /host directory.  Ubuntu will be able to read from that directory (as well as all of your other Windows files).

If you installed Ubuntu on a seperate partition, you would need to create a mount point and mount your NTFS partition the same way an external hard drive would be mounted.  Here's a good reference for you:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by tad1073 on 2009-03-24
go to ad/remove make sure make sure all available applications is selected from the dropdown menu next to (Show) then in the search box type NTFS and select NTFS Confuguration Tool for install. This will allow your vista partition to be automounted.

---

### Post by single.coil on 2009-03-24
got it guys thanks

---

