---
title: "Setting up file server"
date: 2014-03-10
forum: Networking &amp; Wireless
---

### Post by junkman8650 on 2014-03-10
I am about ready to give up on Linux and go back to windows! PLEASE HELP ME!

I  am trying to setup a basic file server for backups with Ubuntu 12.04  server LTS. I was following this video  [http://www.youtube.com/watch?v=ndAYZ0DJ-U4](http://www.youtube.com/watch?v=ndAYZ0DJ-U4)

I am having a heck of a  time setting up a file server with Ubuntu and networking in Linux in  general. I am not able to make it past setting up a static IP address, I   go in to "vi etc/network/interfaces" and put in static and all the IP  address and try to restart the network using his command (/etc/init.d  networking restart) that fails so I reboot the entire server then it  fails to do "sudo apt-get update".

Is there an easier way to setup a server? I just need place to dump files for backups from Windows and Linux PC's.

It's a fresh install on a 1U Intel SR1550AL Server Dual Xeons 5130's 4GB 250GB RAID 1.

---

### Post by Martinjo84 on 2014-03-10
Basis

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

---

### Post by junkman8650 on 2014-03-11
I followed this and now I can access the share on my network and log in but I am not able to write any files. I get a access deined error? Any ideals?

[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!]("https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way")

---

