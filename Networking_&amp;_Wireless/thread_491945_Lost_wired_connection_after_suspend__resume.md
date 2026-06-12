---
title: "Lost wired connection after suspend / resume"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by DavidFourer on 2007-07-04
After about 6 or 8 suspend/resume cycles or about 24 hours, I can't access any web pages or get my email on a wired connection (firefox & Thunderbird) NetworkManager says I'm still connected to the wired internet. Currently I re-boot to fix because the usual ways of resetting the connection don't work.  I try System>Admin>Network or just using NetworkManager.  I don't know how to troubleshoot this. I suspect I don't have to worry about suspend but just make a simple fix each time I loose access. I don't know much about networks or internet connection.

Here is a whole lot of information:

From NetworkManager (while connection is working):
Active Connection Information:
   Interface --- Wired Ethernet (eth0)
   Speed 100 Mb/s
   Driver b44

   IP address 192.168.254.104
   Broadcast Addr 255.255.255.255
   Subnet Mask 255.255.255.0
   Default Route 192.168.254.254
   Primary DNS 192.168.254.254
   Secondary DNS 0.0.0.0
   Hdwr Addr 00:14:22:DA:6F:E2

From Network Tools
   Network device loopback interface (lo)
   IP information
       protocol-IPv4 IP Address-127.0.0 Netmask/prefix-255.0.0.0
       protocol-IPv6 IP Address-- ::1 Netmask/Prefix-128 Scope-host

Network Manager--Active Connection Information
After resume, when fault occurs:

Interface: wired Ethernet (eth0)
Speed 100 Mb/s
Driver b44

IP Adress 0.0.0.0
Broadcast Address 0.0.0.0
Subnet Mask 0.0.0.0
Default Route 0.0.0.0
Primary DNS 0.0.0.0
Secondary DNS 0.0.0.0
Hardware Address 00:14:22:DA:6F:E2

The whole of dmesg output, when fault occurs, and then after reboot, when network is connected, is located here:  [https://home.comcast.net/~davidfourer/dmesg.txt](https://home.comcast.net/~davidfourer/dmesg.txt)   (I don't know how to upload the file)
(I don't understand any of this)


/etc/network/interfaces looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# The primary network interface
iface eth0 inet dhcp
iface eth1 inet dhcp
wireless-essid linksys
auto eth1
auto eth0

Output of lspci

david@davidf:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
david@davidf:~$

---

### Post by jazzgossen on 2007-07-05
i'm having the same kind of problem. Wired connection isn't working after resume, but it works after a reboot. What I do is 
"sudo ifdown eth0; sudo ifup eth0"
And then it all works again. This behaviour started about two weeks ago. FWIW, I'm connecting through a router. Are you?

---

### Post by kevdog on 2007-07-05
If the above solution doesnt work, also try

sudo /etc/init.d/dbus restart

This happens to me too sometimes!

---

### Post by DavidFourer on 2007-07-05
> **kevdog said:**
> also try
sudo /etc/init.d/dbus restart
This worked.  the output is:
david@davidf:~$ sudo /etc/init.d/dbus restart
Password:
 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Starting network connection manager NetworkManager                    [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 
david@davidf:~$ 

When I have some time I'll try to learn what dbus is.    

This is a lot faster than reboot.  I can possibly figure out the next --- which is I think---  Can I do this with a small executable file (a shell script executed by root) and an icon on my toolbar?  Then I would have a one-click solution that takes a few seconds.  

I've seen some explanations on starting a file with "sh", making it executable, putting it in the right directory.  Will I have to type my password every time?  I don't do this every day.  Thanks if you can help.

David

---

### Post by jazzgossen on 2007-07-06
I think the proper way to do this (running a script on resume) is to create a file with the following contents:
```
#!/bin/sh
/etc/init.d/dbus restart
```
naming it something like 99-dbus_restart.sh, and putting it in /etc/acpi/resume.d. Then, the command should be executed automatically when you resume, and you won't have to type a password.

However, I've tried doing that, and for me the scripts in /etc/acpi/resume.d aren't executed when I resume, as I think they should be. But you can try and see if this solution works for you.

---

### Post by DavidFourer on 2007-07-06
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/8584](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/8584) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The solution that worked for me above caused more trouble than it's worth. 
```
/etc/init.d/dbus restart
```   
Power Manager shuts down unexpectedly, and I have to re-set the options.  
The initial problem - loss of wired connection - seems to happen more often.  
I mysteriously lost my Thunderbird Mail program, though I don't know if this was related.  Very strange.  I found it listed in Synaptic Package Manager as "Not Installed" so I reinstalled it.  The new Thunderbird couldn't find my address book and mail files ,which I eventually found.

*dbus restart* shuts down and restarts lots of stuff--see my output above.  Maybe I need to use a lighter touch.  For now I'm back to reboot.  

Maybe it will get fixed with Ubuntu 7.10.  After all, it started with 7.04.

---

### Post by jazzgossen on 2007-07-08
What about ifup/ifdown? Does that help?

---

### Post by DavidFourer on 2007-07-08
> **jazzgossen said:**
> What about ifup/ifdown? Does that help?
I tried it once and it didn't work.  I have to wait till the mysterious unpredictable problem happens, maybe a day.  Then I have to fix it before I can send email.

---

### Post by DC@DR on 2007-07-10
I found one simple way that works perfectly for me, regarding to this issue, just like this:
```

sudo vi /etc/defaults/acpi-support

```
modify this line: 
```
STOP_SERVICES=""
```
to be:
```
STOP_SERVICES="networking"
```
Actually, in my case, it looks like this:
```
STOP_SERVICES="mysql networking"
```
Hope this helps :-)

---

### Post by DavidFourer on 2007-07-11
in /etc/default/acpi-support I found STOP_SERVICES="mysql " with the blank before close-quote.
I changed it to STOP_SERVICES="networking"   This did not help.
Maybe it's not reading the file.  I commented out LOCK_SCREEN=true
       
       # Comment this out to disable screen locking on resume
       #LOCK_SCREEN=true

That worked once and then the password window came back.
.  
Do I need to put STOP_SERVICES="mysql "back in there?  Should I use "mysql networking"?
I tried every combination.

I really don't know if mysql is running or what it does (I thought sql is a database).  Perhaps you can explain.

Thanks for the help.

---

### Post by hornblower on 2007-07-11
I'm having this same problem on my ibm t42 laptop. after a few suspend/resume cycles (it varies), the network just won't reconnect and i have to reboot. the network manager applet acts like its connecting to the wired network but then it just stops and starts over again.

i'll give the suggestion to restart the dbus service a try. i can confirm that this is a regression (for me) in 7.04.

---

### Post by gerkin on 2007-07-16
Hi, check out my post here it might help:

 [http://ubuntuforums.org/showthread.php?p=3030748#post3030748](http://ubuntuforums.org/showthread.php?p=3030748#post3030748)

---

### Post by folkdevil on 2007-07-26
> **DC@DR said:**
> I found one simple way that works perfectly for me, regarding to this issue, just like this:
```

sudo vi /etc/defaults/acpi-support

```
modify this line: 
```
STOP_SERVICES=""
```
to be:
```
STOP_SERVICES="networking"
```
Actually, in my case, it looks like this:
```
STOP_SERVICES="mysql networking"
```
Hope this helps :-)


Just for the record, I had a similar problem with my wireless connection not coming up after a resume.
Having tried various things to solve the problem, the solution quoted above has worked for me.

Thanks!

---

### Post by yukonho on 2007-07-26
> **DC@DR said:**
> I found one simple way that works perfectly for me, regarding to this issue, just like this:
```

sudo vi /etc/defaults/acpi-support

```
modify this line: 
```
STOP_SERVICES=""
```
to be:
```
STOP_SERVICES="networking"
```
Actually, in my case, it looks like this:
```
STOP_SERVICES="mysql networking"
```
Hope this helps :-)

Just commenting that this fix also worked on a Thinkpad T40 with a Cisco Aironet 350 card.  Thanks!

---

### Post by DavidFourer on 2007-08-08
> **walkerk said:**
> I had a similar problem in Ubuntu using network-manager. This is a known issue. My fix was to install [WICD]("http://wicd.sourceforge.net")
A very easy solution that worked for me, found here: [3157403]("http://ubuntuforums.org/showthread.php?p=3157403#post3157403").  Uninstall Network-Manager and install [WICD]("http://wicd.sourceforge.net/").

---

### Post by Copter on 2007-08-24
Hi!

Ive got similar problem but now it works just fine.
```

sudo su
cd /etc/acpi/resume.d/

nano 95-my-net.sh
        #!/bin/sh
        ifdown wlan0
        ifup wlan0 &
        ifdown eth0
        ifup eth0 &

nano 99-dbus_restart.sh 
        #!/bin/sh
        /etc/init.d/dbus restart

cd /etc/default/
nano acpi-support 
        ...
        POST_VIDEO=.
        ...
        STOP_SERVICES="mysql "
        ...
```
Now suspend to ram works like a charm. Thanks for solving this!
Using: Xubuntu 2.6.20-16-generic, LG GS50 laptop, DWL 650+ PCMCIA (cardbus, acx100) wifi (wlan) card.

copter :]

---

### Post by jude01 on 2007-10-12
> **DC@DR said:**
> I found one simple way that works perfectly for me, regarding to this issue, just like this:
```

sudo vi /etc/defaults/acpi-support

```
modify this line: 
```
STOP_SERVICES=""
```
to be:
```
STOP_SERVICES="networking"
```
Actually, in my case, it looks like this:
```
STOP_SERVICES="mysql networking"
```
Hope this helps :-)

Worked perfectly for me!! Thanks!

using: Lenovo 3000 V100 laptop, Broadcomm wireless card, Kubuntu 7.10 Gutsy beta

now if I can only figure out how to get my volume Fn keys working :)

edit: maybe I spoke too soon, seemed to work at home but after letting the laptop sleep all night and resuming it at school, I have problems connecting to the school's wireless network...hopefully its just because the school's network has a lot of traffic at the moment

---

