---
title: "WALKTHROUGH: Compaq C727 - Broadcom 4311 Setup (HP/Compaq)"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by ibun2 on 2008-04-26
This is for NEW installations of Hardy Heron 8.04 Ubuntu (and its variants: Kubuntu/Xubuntu/Studio/and so on)!

Also, it is an offline installation, no ethernet required!

**INTRODUCTION**
Let me preface by thanking jw5801 for writing *How-To: Dell 1390 WLAN (Broadcom 4311 [14e4:4311]) for Laptops using ndiswrapper* [http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568), as that guide is what this walkthrough is based upon (and written by a much more knowledgeable person than I). I would also like to thank any who contributed to the related WifiDocs article [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff), specifically for the Hardy Heron init script that allows the card to activate on startup.

If you have the know-how to make your way around Windows, you should find following this walkthrough pretty straightforward. I am completely new to Ubuntu myself (~3 hrs and having only used Linux for a couple weeks some years ago), so that is why I emphasized that this walkthrough be followed on new installations, as I do not know my way around the configuration files or what changes you might have made.

**IMPORTANT CONSIDERATIONS BEFORE READING THE WALKTHROUGH**
NOTE: This walkthrough assumes...
1. You know where the 'Home' folder is in Ubuntu (or whichever variant you are using).
2. You have your Windows XP driver in a folder on a usb disk (or some kind of external media such as a cd or external hard disk); your driver only consists of 3 files: bcm43xx.cat, bcmwl5.inf, and bcmwl5.sys (what I am saying is, these are the only 3 files you actually need).
3. You have your Ubuntu 8.04 desktop/alternate install cd
4. You know where the Network Manager is
5. You know your WEP passphrase (a word) or WEP key (a large number combination, mine is 10 digits for example)
6. You know your ESSID (what your network is called)

Right...so I am using a Compaq Presario C727 laptop with a Broadcom 4311 chip on a new installation of Kubuntu 8.04. Let's see if you are successful in typing me back on your own Ubuntu installation :).

[SIZE="7"]WALKTHROUGH[/SIZE]
1. Load up your Ubuntu desktop
2. Plug in your external media that has your driver on it
3. Go to the folder with the WinXP driver and rename it 'wireless-install'
4. Copy folder 'wireless-install' into your 'Home' folder
5. Open up Terminal
5. Copy/paste (or type) into Terminal: lspci -nn | grep 14e4|

~What shows up is the card you have. If you see 'Broadcom' and '[14e4:4311]' anywhere on that line, continue. If not, I do not know that this walkthrough will necessarily work with your hardware.~

6. Copy/paste (or type) into Terminal: echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local
7. Insert your Ubuntu cd
8. Copy/paste (or type) into Terminal: sudo apt-cdrom add -m
9. Copy/paste (or type) into Terminal: sudo apt-get update
10. Copy/paste (or type) into Terminal: sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
11. Copy/paste (or type) into Terminal: cd ~/wireless-install/
12. Copy/paste (or type) into Terminal: sudo ndiswrapper -i bcmwl5.inf
13. Copy/paste (or type) into Terminal: sudo rmmod b43 b44 ssb
14. Copy/paste (or type) into Terminal: sudo modprobe ndiswrapper
15. Copy/paste (or type) into Terminal: sudo modprobe b44|
16. OK, wait about 10 seconds. Now right click on your Network Manager. You should see your own network somewhere on that list, and be able to connect using your WEP passphrase/key if necessary. If you use a key, your Ubuntu install might pop up something saying its keeping the key in a password-protected 'wallet.' Give it a password, and in the future, always let ndiswrapper have access to this 'wallet.'
17. Wait, don't get excited yet! Step number six was the script to make your ndiswrapper module load when you boot up your computer. You are successful if you reboot, and, when you logon, you see the gear of your Network Manager start spinning, and then activate your network connection with signal strength bars.

On Ubuntu, the little wireless button we HP/Compaq users have that glows blue/orange does not seem to actually function (mine always glows blue), so that is not an indication that you were successful. Rather, you want to see the signal strength bars in your system tray.

Hope this helps :)!

---

