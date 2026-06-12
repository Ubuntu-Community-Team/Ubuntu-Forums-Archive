---
title: "Trying to mount a shared folder from my mac : Fstab does not recognise the filetype ?"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by Knightwise on 2007-06-25
I was looking to permanently mount my shared drive on my mac onto my linux system using Fstab. I followed all the right moves but it seems that there is a little hickup with the filesystem of the shared folder not being recognised. 

Machine 1 (my mac server) boasts a shared smb folder on \\192.168.123.3\system (i can access it over samba and afs using my other macs and windows machines)

Now with my linux workstation I would like to connect to this share so I created the folder /media/system and set access rights 700 on them. 
I entered my username password in the .smbcredentials  file

Next I added the following line to my fstab
//192.168.123.3/system    /media/system smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0 

But when I mount-a to reload the fstab i get the following error
mount: wrong fs type, bad option, bad superblock on //192.168.123.3/system,
       missing codepage or other error
       In some cases useful info is found in syslog - try 
       dmesg | tail  or so

Its a strange problem because when i go to PLACES / CONNECT TO SERVER and choose "windows filesharing" I can enter the ip and name of the share and it mounts it on my desktop (so the share is accessable tot the Linux system) But when I try to use the 'classic way' (with FSTAB) it says it does not recognise the filesystem. Am i doing anything wrong ?

---

### Post by HermanAB on 2007-06-25
Try changing 'smbfs' to 'cifs'.

---

### Post by Knightwise on 2007-06-26
Hey Herman, 
Thanx for the quick help, But i'm afraid its to no avial :(

This is what I entered into the Fstab
//192.168.123.3/system    /media/system cifs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0   

and after doing a mount -a this is the reply

mount: wrong fs type, bad option, bad superblock on //192.168.123.3/system,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Knightwise on 2007-06-26
I did a little tail dmesg and this is what the last lines read

utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

---

### Post by Knightwise on 2007-06-26
I found it ! 

I used the original vfat line (with smbfs) BUT i installed the smbfs package with sudo apt-get smbfs ! 
Now it works like a charm

---

