---
title: "automount cdrom &amp; display issue"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by mobbbx on 2010-01-27
Hi,

I have just installed xubuntu 9.10. There 2 issues i'm facing now. Xubuntu auto detects my screen resolution to 1920x1080 which is the correct resolution. However, the display will be cut off at the corners. So i changed it to 1280x1024. After i reboot, i will not be able to login! 

After i typed in my password, the screen goes black and goes back to the login screen again. 

I tried to solve this by deleting the display.xml located at $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/. It managed to solve my login problem but i wish to be able to fully utilize the screen resolution of my HD monitor. 

Do i need to install any video drivers? in windows to fully utilize the graphic card i need to install the drivers. Is it the same with xubuntu? 

And how can i auto mount my cdrom when a disc is inserted just like windows or mac? I can mount the cdrom manually by typing "sudo mount /media/cdrom0/ -o unhide" at the terminal. But i want xubuntu to automount when a disc is inserted.

thanks!

---

### Post by halitech on 2010-01-27
what video card do you have?
```
lspci
```
paste the results back here

---

### Post by mobbbx on 2010-01-27
My results from "lspci". Apparently, i'm using the built-in video card on the motherboard. 

> 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


thanks!

---

### Post by halitech on 2010-01-27
there is info here that should help 

[http://ubuntuforums.org/showthread.php?t=1364460&highlight=Intel+Corporation+82G33%2FG31](http://ubuntuforums.org/showthread.php?t=1364460&highlight=Intel+Corporation+82G33%2FG31)

look at post 6

---

### Post by mobbbx on 2010-01-27
Thanks halitech! it worked.... but it gave me an error at login window after reboot!

The error states:

> 
Xfce power manager
HAL daemon is not running


How can i solve that? 

thanks soo much!

---

### Post by halitech on 2010-01-27
I'm not sure, can't say I've ever seen that message before. You could try restarting HAL or make sure HAL is installed.

For the auto-mounting, do you have Thunar-volmon installed?

---

### Post by mobbbx on 2010-01-28
what's the command to restart HAL daemon? or making sure HAL daemon is installed...

As for thunar-volman, i'll try it later when i get home..

thanks for the help soo far!

---

### Post by halitech on 2010-01-28
I'm not sure with restarting it, I know they've made changes and you are supposed to use sudo service start or something like that. To make sure it's installed, either check synaptic or run sudo apt-get install hal

---

### Post by mobbbx on 2010-01-28
after i typed "sudo apt-get install hal", i got the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hal is already the newest version.
hal set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

When i typed "sudo service hal restart", i got the following:

```
xxx@ubuntu:~$ sudo service hal restart
hal start/running, process 3192
xxx@ubuntu:~$ sudo service hal stop
hal stop/waiting
xxx@ubuntu:~$ sudo service hal start
hal start/running, process 3261
```

And i've checked on the thunar-volman, it shows thati have it installed already. My cdrom will not load automatically when cd is inserted, but when i insert a USB drive, it mounts automatically. 

Thanks for your patience..

---

### Post by halitech on 2010-01-28
ok, so hal is installed and running so not sure why you are getting that message.

If  you check the settings for Removable Drives and Media, there should be a setting for removable media, make sure it is checked.

---

### Post by mobbbx on 2010-01-28
i've checked the settings for removable media, and they are all checked...

Under storage tab,
everything is checked
 - mount removable drives when hot-plugged
 - mount removable media when inserted
 - browse removable media when inserted
 - auto-run programs on new drives and media
 - auto-open files on new drives and media

 - burn a CD or DVD when blank disc is inserted

Under Multimedia tab,
these options are checked
 - play audio CDs when inserted
 - play video CDs and DVDs when inserted

The cdrom refuses to auto mount with audio CD or CD that contains documents. However, it mounted DVDs automatically.

This is wierd... i'm sure its something to do with the settings since the DVD is able to mount, other discs shouldn't have any problems. 

As for the Hal daemon, i guess i would have to tolerate this bug, i'm too lazy to reinstall...

---

