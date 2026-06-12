---
title: "Connecting to a router with a laptop"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by halo45121 on 2009-09-27
Hey all! I just installed Ubuntu on my Inspiron 1420. (I think it's 1420, whatever the 14 one is) I'm not very computer saavy and I am having some trouble connecting the laptop to a router. How do I go about scanning for networks and selecting mine? Thanks! 
-Matt

---

### Post by Schendje on 2009-09-27
I'm guessing you're using a wireless network? If Ubuntu finds wireless networks, you can click on the networking-icon in the top taskbar (looks like a red antenna with a few grey bars next to it, I think).

This should show any available networks.

(If it's a different problem, sorry! ;))

---

### Post by halo45121 on 2009-09-27
Okay, I click on the symbol in the top taskbar and it comes up with a menu that says stuff about networks and everything, but the wired network and wireless network options are black and you cant click on them. I don't know what I'm doing, as you can tell, so sorry.

---

### Post by marshmallow1304 on 2009-09-27
Right-click on that same symbol and make sure "Enable Networking" and "Enable Wireless" are both checked.

---

### Post by Schendje on 2009-09-27
Could you provide us with a screenshot showing these black options? If you don't know how, just tell us and we'll explain.

What I *think* it means when the wired connection is black, is that there simply is no cable. But when the wireless connection only shows black, the wireless option on your computer has been turned off.

What kind of computer do you have? Laptop or desktop? What brand and model?

//Edit: marshmallow has a good suggestion, those two options could cause the wireless to be turned off.

---

### Post by halo45121 on 2009-09-27
They are both checked, to reply to Marshmallow's comment.
EDIT: Dell inspiron 1420. So a laptop. The wireless switch and everything are turned on.

---

### Post by soupowl on 2009-09-27
Another thing to check is that your network adaptor works with Ubuntu - they don't all work with it.  Also make sure you install the right drivers for your adaptor.

---

### Post by halo45121 on 2009-09-27
How would I go about checking this and where do I get the drivers?

---

### Post by semitone36 on 2009-09-27
Hi halo

Could you please open a terminal (Applications -> Accessories -> Terminal) and post the output you get from running the command "ifconfig"

---

### Post by halo45121 on 2009-09-27
Okay:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ifmatt@matt-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:f8:9f:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

matt@matt-laptop:~$

---

### Post by semitone36 on 2009-09-29
Alright halo, what that output tells me is that only your ethernet controller is up and running:
> ifmatt@matt-laptop:~$ ifconfig
[COLOR="Blue"]**eth0**[/COLOR] Link encap:Ethernet HWaddr 00:1c:23:f8:9f:bb
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:17


For some reason or another ubuntu isnt loading your wireless card at startup.  Lets next make sure your card is at least recognized by ubuntu.  Type "lshw -C network" into the terminal and post the output for us again.

---

### Post by halo45121 on 2009-09-29
Anybody? A friend of mine told me that I lacked the drivers necessary to have wireless internet, is this true? Where would I get them?

---

### Post by halo45121 on 2009-09-29
Oh. Sorry. Missed your reply. It says command not found.

---

### Post by semitone36 on 2009-09-29
> **halo45121 said:**
> A friend of mine told me that I lacked the drivers necessary to have wireless internet, is this true?

Thats what im trying to find out.  Are you sure you typed the command correctly?  The first letter is an "l" as in "list" not a 1 as in the number.  If the command still doesnt produce anything type this instead: 
```
lspci | grep -net
(again thats an "l" not a "1")
``` and post the output even if it doesnt work.  The "|" symbol should be located right under your backspace key.

---

### Post by halo45121 on 2009-09-29
Oh. I was reading that as an "i". Whoops. #-o
Okay:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

matt@matt-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:f8:9f:bb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:d9:36:65:c0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fe:24:05:3f:f3:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
matt@matt-laptop:~$

---

### Post by semitone36 on 2009-09-30
Haha dont worry it happens.

Okay, from that output I can see that Ubuntu has loaded a driver for your card but it just hasnt activated the interface. Now we are getting somewhere :).

Okay lets try one last set of commands.  Make sure your laptop is within range of your router and then post the output of these commands:
```
sudo ifconfig wlan0 up <press enter, type your login password, and press enter again>
sudo iwlist wlan0 scan
```
This should bring up your wireless interface (wlan0) and then scan for available networks.

---

### Post by halo45121 on 2009-09-30
Okay, it isn't working right. The first time I try to do this after starting up my computer, it allows me to type my password. Then it says no such file or directory. Then it doesn't even let me type my password, just says no such file or directory.
If it makes a difference, it's siocsifflags: no such file or directory.

---

### Post by semitone36 on 2009-09-30
Well that confirms it then.  You dont have a driver for your card loaded.  This goes beyond what I know but I will give you a few links that might help.  First off here is what we know:
> matt@matt-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
*-network
description: Network controller
[COLOR="Red"]product: BCM4311 802.11b/g WLAN
vendor: Broadcom Corporation[/COLOR]
physical id: 0
bus info: pci@0000:0c:00.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: [COLOR="Lime"]driver=b43-pci-bridge[/COLOR] latency=0 module=ssb
The red is your wireless card's make/model and the green is the driver that is currently loaded (but isnt functioning for it). [_Here_]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") is a list of supported wireless cards for linux and the drivers that are known to work with them.  Just click on the Broadcom link on the list by Manufacturer and your card should be the last one on the Broadcom list.  Also, feel free to post another thread in the [_Networking and wireless_]("http://ubuntuforums.org/forumdisplay.php?f=336") section of ubuntu forums, they would know a lot more than I do.  Also be sure to give the "known jaunty wireless workarounds" sticky at the top of the Networking forum a read as well.

Sorry I couldnt get it working for you.  But I have confidence that it will be fixed soon :)

---

### Post by halo45121 on 2009-09-30
Alright, I'll keep playing with it until I get it working. Thanks a lot for all your help! :)

---

### Post by theozzlives on 2009-09-30
Make sure your restricted drivers are activated. Go to System > Administration > Hardware Drivers and if it's black highlight it and click activate.

---

### Post by x C0MMAND0 x on 2009-09-30
Go to System > Administration > Hardware Drivers

See if there is an option for "Broadcom STA wireless driver".  Try enabling that.  Do this while you are connected to a router directly with a cable in case you need to do updates.  You will need to reboot after this.

---

### Post by halo45121 on 2009-09-30
Both of you hit that square on the head. Got it up and running. :)
Thanks to everyone for all of your help!

---

### Post by x C0MMAND0 x on 2009-09-30
If you're referring to me, then you're welcome.  Glad to help!

---

### Post by starcannon on 2009-09-30
The Dell 1420 should run ubuntu very nicely, indeed I bought my Mother the 1420n which is the official Ubuntu variant of the 1420. You can get an official Dell Ubuntu Restore ISO at the following address:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Factory_Recovery_8.04.1_DVD_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Factory_Recovery_8.04.1_DVD_ISO)

Worth looking at for new installs, or for access to drivers or something; I just now finished reading the thread, and see that you have solved the issue. 

GL and HF

---

