---
title: "Not seeing my external hard drive"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by nyxm on 2009-12-26
I used something called Wubi to download and install Ubuntu on my 1TB external hard drive and I guess I thought it would kind of be like a second computer. The only problem is, the filesystem shows that I have only 10GB free and it also shows my internal hard drive that had Vista on it. I just can't find my 985GB that I should have free. I say 985 because when I look in Vista, it says that Ubuntu is only 14.somethingGB. HELP!!!

---

### Post by Howie Spitz on 2009-12-26
Places>Computer  "Browse all local and remote disks accessible from this computer" So no external disk here? I have 9.10 so System>Administration>Disk Utility shows a nice overview of my partitions and drives.
You could run in terminal ```
 sudo fdisk -l 
```  but I'm not sure that will show the host drive using Wubi.
You could also install PySDM in ubuntu ```
 sudo apt-get install pysdm 
```and work to sort it out from there.  System > Administration > Storage Device Manager

---

### Post by nyxm on 2009-12-26
I can find it in disk utility, but I can't do anything with it. I was trying to access it through Places. Still only shows the internal drive. Should I just uninstall and try to make the external hard drive bootable? I really have no idea what to do. Here I have 1TB of storage that I can only use in Windows. :confused:

---

### Post by avtolle on 2009-12-26
Some general observations. When installing using Wubi, the Ubuntu installation is literally contained within the Windows partition, and all Ubuntu files, etc., will be, as I understand it, saved to that partition (in your case, the internal HDD within the space that was initially allocated for the WUBI install). Thus, AFAIK, the installed Ubuntu will not see the external for additional storage. IIRC, it having been quite a while since I used a Wubi install, there is a way to create additional "partitions" under such an install. Perhaps using a search on Google for Wubi installer could help you sort this all out.

What I would suggest, if you are willing to give it a go, is to set up a true "dual boot" installation, and use the external for storage accessible from either OS. There are a plethora of "how-tos" in this forum and otherwise on the web concerning the way to do this. Good luck with whatever course you elect.

---

### Post by Howie Spitz on 2009-12-27
> **nyxm said:**
> I can find it in disk utility, but I can't do anything with it. I was trying to access it through Places. Still only shows the internal drive. Should I just uninstall and try to make the external hard drive bootable? I really have no idea what to do. Here I have 1TB of storage that I can only use in Windows. :confused:
  File System. I would just partition part of your external drive with FAT ( so both windows and linux would be able to use it) Can you "use" it now?
 You don't divulge many details, (how is this drive connected, USB...etc...? Which version of Ubuntu are you using? 
use GParted:[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by presence1960 on 2009-12-27
> **Howie Spitz said:**
> File System. I would just partition part of your external drive with FAT ( so both windows and linux would be able to use it) Can you "use" it now?
 You don't divulge many details, (how is this drive connected, USB...etc...? Which version of Ubuntu are you using? 
use GParted:[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

why use FAT? You can use NTFS! Fat has a 4 GB limit on filesize.

Also lets see what the OP actually has on that machine. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with the external disk plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by nyxm on 2009-12-29
I ended up unistalling Ubuntu through windows, reformatted the external, created about a 440GB partition on it, and installed Ubuntu on it. I put the boot menu in the external also, so I'm thinking I can now use it at any computer.

---

