---
title: "Dell Wireless 1505"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by mlyons16 on 2008-02-12
Hi,

I'm a returning Ubuntu user so I have a little bit of technical competence. I need some assistance with my wireless.

It seems this is a pretty widespread issue, and of course there 101 ways to approach it. I have a Dell XPS M1330 with the Dell Wireless 1505 Draft 802.11n WLAN Mini-Card. The driver is provided by Broadcom and its file name is: BCMWL6.sys

So, how do go about getting this thing working. Right now I'm just testing out Ubuntu on a Live CD. I wanna get this working first on the Live CD if possible. It doesn't even show that I have a wireless connection available. On the top bar there is only Wired connection option, so its as if there is no wireless capabilities. However in Windows there is full wireless available. This has all led me to deduce that Ubuntu doesn't have the appropriate driver for my Wireless network adapter.

Can someone help??

---

### Post by mlyons16 on 2008-02-12
> Section 1 - Gnome / XFCE

1. Download one of the installers. It is easiest to save this file to your home folder but it doesn't really matter where you put it:

    * Online (0.3.2) installer
    * Offline (0.3.2)Installer - (Not all kernels supported)
    * If there is a problem downloading the offline installer, please use the alternate link at the end of this post and send me a PM so I can fix it.


2. Right click the .tar.gz file and click Extract Here. It should extract into its own directory.

3. Go into the bcm43xx-gtk-installer-* folder and double click the installer.py file and click the Run button when prompted.

4. The installer should detect which installation method is appropriate for you.

5. Click the install button to install the appropriate driver.

6. Now enter your password and press the Enter key.

The driver should now be installed. Note that you may have to restart your system depending on which method you chose.

So would this pretty much be the instructions for correcting this?

---

### Post by mlyons16 on 2008-02-12
bump

---

