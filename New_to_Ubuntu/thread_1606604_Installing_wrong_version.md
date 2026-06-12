---
title: "Installing wrong version"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by Rickerc on 2010-10-26
My system is Acer Aspire 5720 laptop 2GB ram Intel Core 2 Duo CPU T5250 1.50GHz running Windows 7 x86 OS.


  I’m trying to install Ubuntu 10.04.1 with Wubi; when get to starting the download it try to download the wrong version “Ubuntu 10.04.1-desktop-amd64.iso.torrent” 
  Is anyway to get Wubi to download the right version to run as x86. I would like to use Wubi as I do not have the knowledge to install it manually.


  Are there any problems with running Ubuntu 10.04.1 on my system?


  Thanks
Rick

---

### Post by Hippytaff on 2010-10-26
If you want you could download the iso and burn it to cd and boot from that to see if it works with your setup, if it does you can install ubuntu on a separate partition...there are many tutorials that can walk you through this 
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
heres one

btw welcome :-)

---

### Post by bcbc on 2010-10-26
> **Rickerc said:**
> My system is Acer Aspire 5720 laptop 2GB ram Intel Core 2 Duo CPU T5250 1.50GHz running Windows 7 x86 OS.


  I’m trying to install Ubuntu 10.04.1 with Wubi; when get to starting the download it try to download the wrong version “Ubuntu 10.04.1-desktop-amd64.iso.torrent” 
  Is anyway to get Wubi to download the right version to run as x86. I would like to use Wubi as I do not have the knowledge to install it manually.


  Are there any problems with running Ubuntu 10.04.1 on my system?


  Thanks
Rick
the amd64 works on intel as long as you have a 64bit processor. Wubi checks whether you can run 64 bit before choosing which version to download. You can force it to use 32 bit either by downloading the 32 bit .iso and placing it in the same folder as wubi.exe, or supplying the --32bit command line option.

---

### Post by Rickerc on 2010-10-28
Thanks Bcbc installed at last just need to sort out "No Mic audio" looks like a mind feild...

---

