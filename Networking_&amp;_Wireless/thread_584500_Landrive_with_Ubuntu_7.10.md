---
title: "Landrive with Ubuntu 7.10"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by mrjkim on 2007-10-21
Hi all
So far, every thing is O.K.  But I have a Landrive (has USB and network support)
I cannot connect to Landrive because I don't know how

I have a windows and mac system. it works very well. but I cannot connect to the Landrive via Landrive. I am searching the possibility through Google. No luck.

Have any one using Landrive in the Linux environment. if know how, Please enlighten me. Thank you.

---

### Post by Whiffle on 2007-10-21
Having no idea what a Landrive is, i googled it.  Looks like what you need is Samba.  Try this:

Hit Alt+F2

type:
smb://addressoflandrive

In theory, it should open up your lan drive (maybe asking for a password).  Once we verify that that works, we can set it up more permanently.

---

### Post by mrjkim on 2007-10-21
it works!.  hank you very much.
However, sometimes I got an error message
"The folder contents could not be displayed. Sorry couldn't display all the contents of "windows Network:Storage[this is my personal network name]"
after that, I hit the reload icon, Then it displays the network folder.

so now How can i set it up permanently?  thank yo and thank you

---

### Post by mlat on 2007-10-26
Hi there, I'm having the same problem. I'm guessing he's talking about the same product I bought (Comstar Landrive) and hes trying to get it running in ubuntu too. I'll give some more information.

After installing it under windows, I noticed that to access the hard drive off a network you needed the hard drive's ID which is a string of characters (it allows you to read the hard drive, the string of characters is similar to a CD key) and optionally, a "key" which permits writing to the hard drive.

---

### Post by lumberg89 on 2007-10-27
I just bought the same drive (320GB)  and can't seem to find it on my network at all.  Does anyone know what IP address it has by default?  I can't see any info on it.

---

### Post by mrjkim on 2007-10-27
Hello
I can tell what I did on my Landrive. 
First of all, I connect Landrive through windows xp/vist. 
and set up the Samba services.  when samba services become available, you have to make a folder that you can read and write. From Ubuntu, I hit "Alt+F2" and write "smb://storage"  then it will show the folder.
I tried to acces Landrive administration function through Firefox, but it has a problem with Firefox. so far I cannot access Landrive administration function via Ubuntu. 
I hope it help you.

---

### Post by mlat on 2007-10-27
There is no admin panel for the landrive I have.

[http://www.ximeta.com/web/products/ndenclosure1_en.php](http://www.ximeta.com/web/products/ndenclosure1_en.php)

One sec theres instructions on the site I didn't see before. I'll try them first then come back here with my findings.

---

### Post by lumberg89 on 2007-10-27
I noticed my landrive was formatted as a windows NT filesystem and I couldn't write to it even with the usb connection.  I think it may need to be VFAT to make it writeable and also so you can configure the sharing via your windows.  I think NTSF writes are still buggy in linux....could be wrong though.

---

### Post by lumberg89 on 2007-10-27
I found a linux driver...and a mac driver which is actually what I was looking for.  Myabe this will help:

[http://www.ximeta.com/web/support/download/linux/index.php](http://www.ximeta.com/web/support/download/linux/index.php)

---

### Post by lumberg89 on 2007-10-28
I got it to work with my mac using the ximeta drivers.  Anyway, it appears there are more useful threads in the ubuntu forums if you search under NDAS.

---

### Post by mlat on 2007-10-28
Ubuntu 7.10 uses the new 3g-ntfs I think, which is stable as far as I know now. NTFS partitions are now writable by default, so I guess its pretty stable.

The ximeta tutorial worked as well, I ignored the vfat instructions and kept it with NTFS, and it runs fine.

I'm just having trouble mounting it on startup without being root. But thats another matter.

---

### Post by mrjkim on 2007-10-28
I think my Landrive is based on Samba protocol but some other products are based on NDAS. My Landrive file system is FAT32 so any operating system can read and write. however it has a drawback(a file cannot be exceed more than 4GB).

---

### Post by mrjkim on 2007-10-28
This might help to understand the different type of landrive

[http://www.macpower.com.tw/products/hdd3/m9/ndasvslan](http://www.macpower.com.tw/products/hdd3/m9/ndasvslan)

---

### Post by On_a_Quest on 2007-11-05
> **mlat said:**
> Ubuntu 7.10 uses the new 3g-ntfs I think, which is stable as far as I know now. NTFS partitions are now writable by default, so I guess its pretty stable.

The ximeta tutorial worked as well, I ignored the vfat instructions and kept it with NTFS, and it runs fine.

I'm just having trouble mounting it on startup without being root. But thats another matter.

I got this to work once, rebooted,  and now can't get it to remount.   Have you found a solution?  I get "mount: special device /dev/ndas-<mynumber>-0p1 does not exist"  When I try to re-enable it I get "Check NDAS device file exists, driver module is loaded and started by administration tool".   I did end up re-formatting in FAT32.

---

### Post by geefour on 2008-03-03
default address: [http://169.254.0.1/](http://169.254.0.1/)
default subnetmask: 255.255.0.0
default username: admin
default password: admin

update to the latest firmware: [http://www.usbex.com/landrive/landrive-FirmwareBasicNAS-48-b1-F.rar](http://www.usbex.com/landrive/landrive-FirmwareBasicNAS-48-b1-F.rar)

---

