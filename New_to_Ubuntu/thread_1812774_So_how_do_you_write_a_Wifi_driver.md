---
title: "So how do you write a Wifi driver"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by Da Flo-rid-eee-an on 2011-07-26
So the instructions in my ASUS 802.11n Network Adapter (USB-N13) Readme file are way over my head, I was wondering if anyone did the instructions in English or something like that. maybe a video? Any help is welcome

---

### Post by westie457 on 2011-07-26
> **Da Flo-rid-eee-an said:**
> So the instructions in my ASUS 802.11n Network Adapter (USB-N13) Readme file are way over my head, I was wondering if anyone did the instructions in English or something like that. maybe a video? Any help is welcome

I take it that you cannot use it at the moment. What version of Ubuntu are you trying to use this with?

---

### Post by Da Flo-rid-eee-an on 2011-07-26
I am using 11.04 Natty

---

### Post by doas777 on 2011-07-26
this thread may be of use in getting your nic running. 
[http://ubuntuforums.org/showthread.php?t=1419504](http://ubuntuforums.org/showthread.php?t=1419504)

as for writing a driver (as in actually writing code to do the job), it is rather involved even for many programmers, and involves a lot of knowledge of the inner workings of the linux kernel. not a small endeavor.

Edit:
this is a shorter more concise breakdown of the thread above.
[http://vinodseb.blogspot.com/2010/03/asus-usb-n13-ubuntu-driver.html](http://vinodseb.blogspot.com/2010/03/asus-usb-n13-ubuntu-driver.html)

---

### Post by salehahmed985 on 2011-07-26
i'm sorry to interrupt. i'm new here. i want to ask a question abt dependency problem in natty. how can i ask it in forum? please help me...

---

### Post by Da Flo-rid-eee-an on 2011-07-26
:confused: the thread doesnt help

---

### Post by doas777 on 2011-07-26
> **Da Flo-rid-eee-an said:**
> :confused: the thread doesnt help

ok, long story short, these days you have a good shot of getting your wifi running with no intervention, but when that doesn't happen, the answer is always a bit technical.

is there a specific problem you have with the thread? I don't have that nic, but I can try to walk you through the threads instructions if you like.

---

### Post by Da Flo-rid-eee-an on 2011-07-26
> **doas777 said:**
> 

Edit:
this is a shorter more concise breakdown of the thread above.
[http://vinodseb.blogspot.com/2010/03/asus-usb-n13-ubuntu-driver.html](http://vinodseb.blogspot.com/2010/03/asus-usb-n13-ubuntu-driver.html)

this one gets me to editing the makefile in gedit, but then when i save it, terminal says the directory in not there or something like that

---

### Post by doas777 on 2011-07-26
> **Da Flo-rid-eee-an said:**
> this one gets me to editing the makefile in gedit, but then when i save it, terminal says the directory in not there or something like that
ok, so you have extracted the file, and cd'ed into the extracted directory, right?
type:
```
ls -al
```
after you have run 'cd ~\Desktop\2009'
and we'll see what is going on.

---

### Post by gandaran on 2011-07-27
> **Da Flo-rid-eee-an said:**
> So the instructions in my ASUS 802.11n Network Adapter (USB-N13) Readme file are way over my head, I was wondering if anyone did the instructions in English or something like that. maybe a video? Any help is welcome
before you try to compile drivers you should first find out the wireless device chipset, you can do that by typing in terminal
```
lspci
```
for internal devices, and for usb devices
```
lsusb
```
post the output on this thread.
once you know the chipset brand you can use it to search the forum especially the networking and wireless section, I'm sure you will find many threads from users with the same problem and possibly the fix for the wireless in one of them.

---

### Post by amjjawad on 2011-07-27
> **salehahmed985 said:**
> i'm sorry to interrupt. i'm new here. i want to ask a question abt dependency problem in natty. how can i ask it in forum? please help me...

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by amjjawad on 2011-07-27
> **gandaran said:**
> before you try to compile drivers you should first find out the wireless device chipset, you can do that by typing in terminal
```
lspci
```for internal devices, and for usb devices
```
lsusb
```post the output on this thread.
once you know the chipset brand you can use it to search the forum **especially the networking and wireless section, I'm sure you will find many threads from users with the same problem and possibly the fix for the wireless in one of them**.

+1

I think even:

```
sudo lshw -C network

```will do the job!

---

### Post by Da Flo-rid-eee-an on 2011-07-27
@doas777, I have no idea what "cd'ed" means ATM. I did run 
ls -al

and got this 

 jacob@jacob-OptiPlex-GX620:~$ ls -al  
  total 412  
  drwxr-xr-x 35 jacob jacob   4096 2011-07-26 21:33 .  
  drwxr-xr-x  3 root  root    4096 2011-07-25 17:53 ..  
  drwxr-xr-x  2 jacob jacob   4096 2011-07-25 22:30 .acetoneiso  
  drwx------  4 jacob jacob   4096 2011-07-26 18:10 .adobe  
  drwx------  3 jacob jacob   4096 2011-07-25 22:32 .appdata  
  -rw-------  1 jacob jacob    645 2011-07-27 21:59 .bash_history  
  -rw-r--r--  1 jacob jacob    220 2011-07-25 17:53 .bash_logout  
  -rw-r--r--  1 jacob jacob   3353 2011-07-25 17:53 .bashrc  
  drwx------ 11 jacob jacob   4096 2011-07-26 21:41 .cache  
  drwx------  3 jacob jacob   4096 2011-07-25 20:07 .compiz  
  drwxr-xr-x 14 jacob jacob   4096 2011-07-25 22:30 .config  
  drwx------  3 jacob jacob   4096 2011-07-25 18:05 .dbus  
  drwxr-xr-x  4 jacob jacob   4096 2011-07-26 21:42 Desktop  
  -rw-r--r--  1 jacob jacob     78 2011-07-26 21:33 .dmrc  
  drwxr-xr-x  2 jacob jacob   4096 2011-07-25 18:05 Documents  
  drwxr-xr-x  2 jacob jacob   4096 2011-07-25 18:12 Downloads  
  -rw-------  1 jacob jacob     16 2011-07-25 18:05 .esd_auth  
  -rw-r--r--  1 jacob jacob    179 2011-07-25 17:53 examples.desktop  
  drwxr-xr-x  2 jacob jacob   4096 2011-07-25 19:58 .fontconfig  
  drwx------  4 jacob jacob   4096 2011-07-26 21:33 .gconf  
  drwx------  2 jacob jacob   4096 2011-07-27 21:56 .gconfd  
  -rw-r-----  1 jacob jacob      0 2011-07-25 19:08 .gksu.lock  
  drwx------  7 jacob jacob   4096 2011-07-26 18:52 .gnome2  
  drwx------  2 jacob jacob   4096 2011-07-25 18:11 .gnome2_private  
  drwx------  3 jacob jacob   4096 2011-07-26 21:33 .gnupg  
  drwxr-xr-x  4 jacob jacob   4096 2011-07-25 19:06 GNUstep  
  drwxr-xr-x  2 jacob jacob   4096 2011-07-25 22:35 .gstreamer-0.10  
  -rw-r--r--  1 jacob jacob    137 2011-07-26 21:33 .gtk-bookmarks  
  dr-x------  2 jacob jacob      0 2011-07-26 21:33 .gvfs  
  -rw-------  1 jacob jacob   1496 2011-07-26 21:33 .ICEauthority  
  drwxr-xr-x  2 jacob jacob   4096 2011-07-25 18:10 .icons  
  drwxr-xr-x  3 jacob jacob   4096 2011-07-25 18:05 .local  
  drwxr-xr-x  3 jacob jacob   4096 2011-07-25 22:32 .macromedia  
  drwx------  4 jacob jacob   4096 2011-07-25 22:16 .mozilla  
  drwxr-xr-x  2 jacob jacob   4096 2011-07-25 18:05 Music  
  drwxr-xr-x  2 jacob jacob   4096 2011-07-25 18:05 .nautilus  
  drwxr-xr-x  2 jacob jacob   4096 2011-07-25 22:30 Pictures  
  -rw-r--r--  1 jacob jacob    675 2011-07-25 17:53 .profile  
  drwxr-xr-x  2 jacob jacob   4096 2011-07-25 18:05 Public  
  drwx------  2 jacob jacob   4096 2011-07-26 21:33 .pulse  
  -rw-------  1 jacob jacob    256 2011-07-25 18:05 .pulse-cookie  
  drwx------  2 jacob jacob   4096 2011-07-25 22:19 .ssh  
  -rw-r--r--  1 jacob jacob      0 2011-07-25 19:08 .sudo_as_admin_successful  
  drwxr-xr-x  2 jacob jacob   4096 2011-07-25 18:05 Templates  
  drwxr-xr-x  2 jacob jacob   4096 2011-07-25 18:10 .themes  
  drwx------  4 jacob jacob   4096 2011-07-25 18:10 .thumbnails  
  drwxr-xr-x  2 jacob jacob   4096 2011-07-25 18:05 Videos  
  -rw-r--r--  1 jacob jacob    834 2011-07-25 22:24 .xscreensaver-getimage.cache  
  -rw-------  1 jacob jacob  14996 2011-07-27 22:00 .xsession-errors  
  -rw-------  1 jacob jacob 216054 2011-07-26 21:31 .xsession-errors.old  
  jacob@jacob-OptiPlex-GX620:~$ ^C  
  jacob@jacob-OptiPlex-GX620:~$

---

### Post by Da Flo-rid-eee-an on 2011-07-27
@gandaran, I ran lspci and got this 

jacob@jacob-OptiPlex-GX620:~$ lspci  
 00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)  
 00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)  
 00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)  
 00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)  
 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)  
 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)  
 00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)  
 00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)  
 00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)  
 00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)  
 00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)  
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)  
 00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)  
 00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)  
 00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)  
 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)  
 02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)  
 jacob@jacob-OptiPlex-GX620:~$  
 

in a different terminal i ran lsusb and got 

jacob@jacob-OptiPlex-GX620:~$ lsusb  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 003: ID 413c:2010 Dell Computer Corp.  
 Bus 003 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 009: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter  
 Bus 001 Device 008: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub  
 Bus 001 Device 005: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 flash drive  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 jacob@jacob-OptiPlex-GX620:~$

---

### Post by Da Flo-rid-eee-an on 2011-07-27
@amjjawad, I ran sudo lshw -C network and got 

jacob@jacob-OptiPlex-GX620:~$ sudo lshw -C network  
 [sudo] password for jacob:  
   *-network                
        description: Ethernet interface  
        product: NetXtreme BCM5751 Gigabit Ethernet PCI Express  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 01  
        serial: 00:12:3f:65:86:f2  
        capacity: 1Gbit/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5751-v3.44a latency=0 link=no multicast=yes port=twisted pair  
        resources: irq:16 memory:fe8f0000-fe8fffff  
   *-network DISABLED  
        description: Wireless interface  
        physical id: 1  
        bus info: usb@1:8  
        logical name: wlan0  
        serial: f4:6d:04:b1:68:87  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-10-generic firmware=0.12 link=no multicast=yes wireless=IEEE 802.11bgn  
 jacob@jacob-OptiPlex-GX620:~$

---

### Post by uRock on 2011-07-27
> **Da Flo-rid-eee-an said:**
> So the instructions in my ASUS 802.11n Network Adapter (USB-N13) Readme file are way over my head, I was wondering if anyone did the instructions in English or something like that. maybe a video? Any help is welcome
Check Additional Drivers or Hardware Drivers under the System Administration menu. There should be a driver there for the Asus card.

---

### Post by Da Flo-rid-eee-an on 2011-07-27
one blaring thing i see in the "sudo lshw -C network" is that it says my "*-network" is disabled yet the OS recognizes that I have a wireless interface

---

### Post by Da Flo-rid-eee-an on 2011-07-27
Where do I find the System Admin menu?

---

### Post by uRock on 2011-07-27
Enter additional drivers in the search box for Unity.

---

### Post by Da Flo-rid-eee-an on 2011-07-27
says the no proprietary drivers are in use on the system

---

### Post by anewguy on 2011-07-27
This thread is for getting your exact device working - see down a little where there are things posted in blue.

[http://ubuntuforums.org/showthread.php?t=1419504&page=4]("http://ubuntuforums.org/showthread.php?t=1419504&page=4")

EDIT:  just saw I copied the URL for the fourth page - you'll need to start at the beginning.

Also, if at all possible, temporarily hard-wire your PC to the router, then repeat the additional drivers probe - it may take a while since it will be checking the net.  Wait for it all to finish, then if a driver shows on the page but it says it is not in use or not enabled, be sure to mark the box to enable the driver.

---

### Post by doas777 on 2011-07-28
> **Da Flo-rid-eee-an said:**
> @doas777, I have no idea what "cd'ed" means ATM. I did run 
ls -al

and got this 
...

Ok, that explains it

in the terminal, the command cd is used to change directories. for instance, lets say you have a file at ~\Desktop\folder1\File1

to copy that file to your desktop you need to either:
1) cp ~\Desktop\folder1\File1 ~/Desktop
OR
2) cd ~\Desktop\folder1
    cp File1 ~/Desktop

notice how after "cd'ing" I am able to just call the file 'File1' without specifying the full path?

if you ever want to know what directory you are currently in, use the command 'pwd'

the instructions in that link instruct you to download a driver, and extract it onto your desktop.
after it is extracted, they ask you to cd into the directory. based on the output of your ls -al, you did not cd into the directory, so the rest of the instructions fail (file not found).

does that make sense?

---

### Post by Da Flo-rid-eee-an on 2011-07-28
Yes, so I should copy the file in the folder I extracted onto my desktop?

---

### Post by doas777 on 2011-07-29
> **Da Flo-rid-eee-an said:**
> Yes, so I should copy the file in the folder I extracted onto my desktop?

if you like. if you want to follow the directions verbatim, copy the folder to your desktop and rename it '2009'. you don't have to, but if you don't then you have to replace your folder path with with the one the thread is using (eg: ~\Desktop\2009)

---

### Post by Da Flo-rid-eee-an on 2011-08-02
When following my directions I get to the line of "gedit os/linux/config.mk"  and then I get this message in the terminal 

"jacob@jacob-OptiPlex-GX620:~$ cd ~/Desktop/2009   jacob@jacob-OptiPlex-GX620:~/Desktop/2009$ sudo su  
 [sudo] password for jacob:  
 root@jacob-OptiPlex-GX620:/home/jacob/Desktop/2009# gedit os/linux/config.mk  
 

 (gedit:2570): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.4HITZV': No such file or directory  
 

 (gedit:2570): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or director"


But gedit opens up config.mk, but I cannot save the file

---

### Post by doas777 on 2011-08-02
try this command instead:
```
gksu gedit gedit ~/Desktop/2009/os/linux/config.mk
```

---

