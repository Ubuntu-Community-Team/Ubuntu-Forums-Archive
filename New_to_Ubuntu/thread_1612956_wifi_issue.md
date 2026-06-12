---
title: "wifi issue"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by 007casper on 2010-11-03
I am trying to go online.  On the wireless settings, I get a window... it says 
> 
Enter Password for Keyring 'default' to unlcok

An application wants access to the keyring 'default', but it is locked

the unlock password is incorrect

Password:

(filled in) Lock this keyring when I log out

(empty circle) Lock this keyring after -----(minutes)

(empty circle) Lock this keyring if idle after ---- (minutes)

Cancel, OK

what is the keyring?  How can I find it?  It is not user login password.

thank you

---

### Post by alang184 on 2010-11-03
The keyring is just the superuser password, isn't it?

---

### Post by 007casper on 2010-11-04
thats what I thought but it doesnt work

---

### Post by Quackers on 2010-11-04
Try clicking on OK or whatever it is leaving the password blank - you may not have set one up, I didn't.

---

### Post by Wtower on 2010-11-04
Keyring is a part of Gnome to let user securely store a collection of passwords, certificates, etc. [http://live.gnome.org/GnomeKeyring]("http://live.gnome.org/GnomeKeyring")

It has got nothing to do with root. It might have got nothing to do with your login password either. First time it allows you to enter a new separate password, under which several other passwords are stored, including the wifi psk's. It might be blank as well, it depends on what you had entered there first time.

Regards

---

### Post by 007casper on 2010-11-04
well I thought it was superuser password. I have tried that it didnt work.  Then, I have tried blank, it still doesnt work.

I go to system > preferences > network connections to set up wireless.  However, when I go to top icon, it states wireless is disabled ???

It doesnt accept the keyring anyways.  Even, if I leave it blank.  

I got this cheap Dell inspiron 1525

Thank you

---

### Post by anewguy on 2010-11-04
If you right-click on the network manager icon, can you click the "Enable Wireless" then try again?

Also - you should be able to remove the existing keyring password (might also remove the keyring, I'm not sure) via (I think) System/Preferences/Passwords and Encryption Keys.  I know the old way of deleting the keyring entirely, but it looks like some of that has changed now.

Dave ;)

---

### Post by beew on 2010-11-04
I had that problem when I first installed 10.04, I had no idea what "password" keyring wanted.  It wasn't my login password and it wasn't blank and I never set a keyring password! It is probably a bug,--but I don't remember encountering this problem in my 10.10 installation, so it might have been fixed.

So you need to reset the password or basically disable it.   Go to Places, open Home and choose "Show Hidden Files" . Then open the folder .gnome2 and simply delete the folder "keyrings"  

Next time when you try to edit network connection again it will ask you to make a new password. If you just leave it blank it will give you a warning about unsafe password storage or something like that, just press OK and it won't bother you anymore. I don't really need that much "security". One password is good enough for me, it is not like I am CIA or anything. (otherwise you can of course choose another password or use your login password)

---

### Post by 007casper on 2010-11-05
When I right-click on the network manager icon, I cannot click the "Enable Wireless".  It was disabled.

chose "Show Hidden Files" then open the folder .gnome2 and simply delete the folder "keyrings".  Tried again.  No luck.

I right click on the network manager icon again, I still cannot "Enable Wireless"

However,this time I was able to insert wireless information without keyring prompt - system > preferences > network connections

Now, checked it again. Enable Wireless is checked.  However, I still dont get wireless connection.

---

### Post by anewguy on 2010-11-05
Open a terminal window (Apppications/Accessories/Terminal) and type:

lspci <press enter>

lshw -C network <press enter>

ifconfig <press enter>

Copy the output from those and post it back here.

Dave ;)

---

### Post by waynefoutz on 2010-11-06
This may sound like a dumb suggestion, but trust me, I've sat up all night pulling my hair out trying to figure out what was wrong, and it came down to this: are you sure the external switch  that turns the wifi adapter on and off is set to on? I've never used the 1525, but some Dells have a slider switch on the side, some of them have a small button next to the power button.


I've also spent hours after reinstalling the OS on a Toshiba notebook trying to figure out why I couldn't get sound to come out of the speakers, then gave up, handed the laptop back to the owner with an sincere apology, only to watch her boot it up, turn up the volume knob on the side I had no idea was there, and listen to the startup sound.

---

### Post by 007casper on 2010-12-10
> 
www@www-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

> 
www@www-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:eb:ee:73
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=192.168.1.100 latency=0 multicast=yes
       resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe7fc000-fe7fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:23:4d:12:a4:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

> 
www@www-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:eb:ee:73  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:9bff:feeb:ee73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47060979 (47.0 MB)  TX bytes:36691010 (36.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)


In linksys the laptop shows up when I check the dhcp table.  However, it just cant go online, it states wireless networks - device not ready, even though it shows up on linksys router.  When I plug the ethernet cable back to the computer, I am able to check wireless enabled, then click on the icon on the top kickbar, it states wireless networks device not ready again.

please,advise.

thank you

---

### Post by anewguy on 2010-12-10
Your wireless is the Broadcom 4312.  Did you ever intentionally install a driver for it?  If not, try the following:

- if you can hard wire a cable to your router
[LIST]
[*]connect a hard wire between your PC and the router
[*]open a terminal window and type sudo apt-get update <press enter>
[*]wait for that to finish
[/LIST]

- go to System/Administration/Additional Drivers - does a driver show for your wireless?  Is it enabled?  It may take a while for this to come up, particularly if the hard wire is connected (don't purposely disconnect it for this step!).  If a driver is seen, enable it.

- if you had a hard-wire cable plugged in, physically disconnect it

- right-click on network manager and see if "Enable Wireless" shows now and if it is enabled - if not enabled, enable it.

Remember, all the "rules" regarding MAC filtering and encryption at the router still apply for the connection you attempt.  If the network is hidden (the router is not broadcasting the ESSID) then you must go through network manager/Connect To Hidden Network and manually enter everything.

Dave ;)

---

