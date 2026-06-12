---
title: "How to remove password when access my share folder via Windows"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by pemimpin on 2007-10-31
I have home networking...

The problem is when I use computer with Windows OS - open Network > View Workgroup . It find my ubuntu computer.

But when I click on it to access my ubuntu folder. It keep asking bout username and password. I put my username and password (same as I use to login Ubuntu) but i never work.

Somebody please help me how to remove the asking of username and password?

-sorry for my bad english-:lolflag:

---

### Post by froy02 on 2007-10-31
]Edit your /etc/samba/smb.conf file and add the following lines in the global section:

  workgroup = <your-workname>
   netbios name = <your_ubuntu_net_ bios name>
   security = SHARE 
   wins support = Yes 

Mine is setup as follows:
  workgroup = LAPID
   netbios name = UBUN890B
   security = SHARE 
   wins support = Yes 

Make sure to check that there are no other lines saying otherwise, like some win support=no" somewhere in that file.
Also samba, nfts-3g, ntfs-config are installed.

---

### Post by dukejib on 2007-11-01
> **froy02 said:**
> ]Edit your /etc/samba/smb.conf file and add the following lines in the global section:

  workgroup = <your-workname>
   netbios name = <your_ubuntu_net_ bios name>
   security = SHARE 
   wins support = Yes 

Mine is setup as follows:
  workgroup = LAPID
   netbios name = UBUN890B
   security = SHARE 
   wins support = Yes 

Make sure to check that there are no other lines saying otherwise, like some win support=no" somewhere in that file.
Also samba, nfts-3g, ntfs-config are installed.

Lot of Thanks **Froy02**. I was getting paranoid about why my NTFS Drive Folders were not getting shared. :)  Found out the only culprit was ntfs-config, which i forgot to install.

Thanks anyway!:KS

---

### Post by pemimpin on 2007-11-02
i try but the setting are different from that you wrote. i think the setting you use is for ubuntu 7.04 . Not 7.10 .

---

### Post by froy02 on 2007-11-03
I am using ubuntu 7.10 and those setting work.  Maybe you have a firewall on the ubuntu machine turn on.
It works for me.

---

### Post by SpiritIsReality on 2007-11-03
howdy
I have yet to enjoy dancing the samba, but the beat goes on. haha.
any help here?
[http://ubuntuforums.org/showthread.php?t=528592&highlight=samba](http://ubuntuforums.org/showthread.php?t=528592&highlight=samba)
[http://screencasts.ubuntu.com/SAMBA_Filesharing](http://screencasts.ubuntu.com/SAMBA_Filesharing)
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)
others seem to be able to get it to work. I hope it's catchy.
trails amigos

---

