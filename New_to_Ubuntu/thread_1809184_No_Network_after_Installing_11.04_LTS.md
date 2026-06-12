---
title: "No Network after Installing 11.04 LTS"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by NCMS on 2011-07-21
I am very new to Ubuntu and just downloaded and installed 11.04 LTS
 
Ubuntu 11.04 - LTS (Long Term Support) (32-bit) ....
 
but I have noticed that the Ethernet and Wirless are NOT wokring !!
 
The instllation done on **HP Pavilion dv6** LAPTOP.
 
 
Any suggestion can help me with this..
 
Thanks,

---

### Post by jjex22 on 2011-07-21
will this help?
 
[https://wiki.ubuntu.com/HP_Pavillion_dv6000_%28dv6604nr%29]("https://wiki.ubuntu.com/HP_Pavillion_dv6000_%28dv6604nr%29")

---

### Post by mikechant on 2011-07-21
NB 11.04 is not LTS as stated, 10.4 is LTS and 12.04 will be.

---

### Post by NCMS on 2011-07-22
[FONT=&quot]THANKS... **The problem SOLVED for the Ethernet, now I have to fight to solve the Wireless Problem **in another thread :popcorn:
 
 [/FONT]
  [FONT=&quot]**[COLOR=SandyBrown]MY SYSTEM DETAILS;[/COLOR]**
**cat /etc/issue**
Ubuntu 10.04.2 LTS

[B]sudo lspci | grep Ethernet
[/B]03:00.0 Ethernet controller:  **Realtek **Semiconductor Co., Ltd. RTL8111/**8168B** PCI Express Gigabit Ethernet controller (rev 03)
 
 [/FONT]
  **[FONT=&quot]uname  -a[/FONT]**
  [FONT=&quot]2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux[/FONT]
  [FONT=&quot] [/FONT]
  **[FONT=&quot]lscpu[/FONT]**[FONT=&quot]
i686                 32-bit,  64-bit              GenuineIntel[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]
**[COLOR=Red]Here are the 5 steps I took;[/COLOR]**
**1.** followed the instructions in (thanks to **rvdavid**)
_[COLOR=blue][http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/](http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/) [/COLOR]_[/FONT]
  [FONT=&quot]

**2.** Downloaded the file **r8168-8.024.00.tar.bz2   **from
_[COLOR=blue][http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)  [/COLOR]_

      Driver for Linux kernel 2.6.x and 2.4.x   - Version 8.024.00 

**3.** ran   [/FONT]**sudo update-initramfs -u**[FONT=&quot]
in my case I must ran it because even though I removed the incompatible default driver **r8169** & putting it in the blacklist file, the driver still gets loaded and I don't see the newly installed driver r8168 after a reboot; 
**# sudo  rmmod r8169**

**/etc/modprobe.d/blacklist.conf**:
  #blacklist r8169 driver [/FONT]
  [FONT=&quot]  blacklist r8169[/FONT]
  [FONT=&quot]
    (thanks to [/FONT][[FONT=&quot]patchwork[/FONT]]("http://ubuntuforums.org/member.php?u=982585")[FONT=&quot]  from  _[COLOR=blue]http://ubuntuforums.org/showthread.php?t=1434757[/COLOR]_  )[/FONT]
  
  **4. **REMed/hashed the  127.0.1.1 line in  [B]/etc/hosts
[/B]and I have these two lines in hosts file;
  127.0.0.1              localhost              ncms-laptop
  #127.0.1.1           ncms-laptop


  [COLOR=Blue]_[http://www.imminentweb.com/technologies/ubuntu-network-error-ignoring-unknown-interface-eth0eth0](http://www.imminentweb.com/technologies/ubuntu-network-error-ignoring-unknown-interface-eth0eth0)_[/COLOR]
 



   
**5.** rebooted the laptop twice


  [B]
[/B]

---

