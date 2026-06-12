---
title: "Installing Plusecom Wireless USB Adaptor"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by blackjet on 2008-12-30
Hello,

This is my first post here and I'm new to Ubuntu and indeed Linux so please be patient with me! I'm trying to install the drivers for a wireless USB dongle (Pulsecom WU-ZD1211B). I gather from the readme supplied with the drivers I have to use a tar.gz file, I've had a look through the forum for information on how to install a tar.gz correctly but nothing seems to quite fit my situation.

What I have done so far:

1) Copied the tar.gz to my desktop.
2) given myself read write permissions on the file using gksu nautilus ~/Desktop (for some reason when i copied it from the CD I didn't have permissions to edit/delete the file :confused:)
3) did the following at the terminal:

drew@advent7081:~$ cd Desktop
drew@advent7081:~/Desktop$ ls
ZD1211LnxDrv_2_22_0_0.tar.gz
drew@advent7081:~/Desktop$ tar zxvf ZD1211LnxDrv_2_22_0_0.tar.gz
tar: ZD1211LnxDrv_2_22_0_0.tar.gz: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error exit delayed from previous errors
drew@advent7081:~/Desktop$ 

As you can see for some reason the tar zxvf command didn't work. I would be very grateful if someone could suggest what I should try next, I have attached the read me that came with the driver, I don't understand it very well but maybe someone with a little more experience will.

Many thanks

~blackjet

---

### Post by wolfen69 on 2008-12-30
all you have to do is right click the file and "extract here".

---

### Post by blackjet on 2008-12-30
Hi wolfen69, thanks for the reply! I have a further problem, i dont have an extract here option in the right click context menu. Do you know why this might be?

Thanks

~blackjet

---

### Post by flyingsliverfin on 2008-12-30
im only 12, but have done a lot using zipped files in ubuntu (I hardly know anything advanced like installing your driver,  unless there is a .deb file. don't ask me anything else except for this, I can't help otherwise) . First, what version of ubuntu do you have? And, (if its a newer version) the tar.gz icon should appear as a box. when you open it, there should be a button on the top bar along with the 'add folder' ect. try pressing it. It should make a pop-up asking you of the location of the extraction.

---

### Post by flyingsliverfin on 2008-12-30
oh yes, try searching for the driver online, and get it as a .deb file. Then right-click it and say open with g...something. The install should be automatic then.

---

### Post by balloooza on 2008-12-30
post, I will help in a second, just need to switch computers.

---

### Post by blackjet on 2008-12-30
thanks for all the replies guys! I'm now searching for a .deb driver online.

I'v also managed to coppy the stuff in the the tar.gz file to the desktop and have tried running the make command but it hasn't worked either, see below:

drew@advent7081:~$ cd Desktop
drew@advent7081:~/Desktop$ ls
apdbg.c    Makefile  scripts  Winevl_iface
config.in  Menudbg   src      ZD1211LnxDrv_2_22_0_0.tar.gz
drew@advent7081:~/Desktop$ make
Makefile:15: .config: No such file or directory
Makefile:16: .config: No such file or directory
make: *** No rule to make target `.config'.  Stop.
drew@advent7081:~/Desktop$ 


thanks again :)

---

### Post by balloooza on 2008-12-30
I think all you need to do is

```
sudo modprobe zd1211rw
```

---

### Post by blackjet on 2008-12-30
> **balloooza said:**
> I think all you need to do is

```
sudo modprobe zd1211rw
```

i tried that command and this happened:

drew@advent7081:~$ cd Desktop
drew@advent7081:~/Desktop$ ls
apdbg.c    Makefile  scripts  Winevl_iface
config.in  Menudbg   src      ZD1211LnxDrv_2_22_0_0.tar.gz
drew@advent7081:~/Desktop$ sudo modprobe zd1211rw
[sudo] password for drew: 
drew@advent7081:~$

which command should I be running next?

@ everyone -  i cant find a driver online :(

---

### Post by balloooza on 2008-12-30
Well now it should be working, just restart, and look at the network icon in the top corner of the screen. The network icon kinda works like the one on vista, eccept to enable networking and wiresess, RIGHT click it and you will se boxes, to go to a certain network left click it and you will see a list, somtimes it takes a  second to update (searching for networks wil not be shown, but it is still serching)

I hope this works

---

### Post by flyingsliverfin on 2008-12-30
cuold you post the contents of the tar.gz (as a tar.gz) on a post here on the forum? I could try experimenting with it. (I need the files so I know what kind of .   they are. ) **or could you post the names of the files online (this would be a bit safer since if you post the contents of the tar.gz then it could be illegal)**

is there a .deb or a .exe file in the tar.gz? if there is a .exe you could try getting wine ([www.winehq.com](www.winehq.com))

that might work

---

### Post by blackjet on 2008-12-30
ok so i restarted and now I have some new options; "create new wireless network" and "connect to other wireless network".

when i select the "connect to other wireless network" option and enter the name of the network and the WEP key it seems to connect (well at least the network name appears under "wireless connections") but the signal strength is 0%. This is even the case when I'm right next to the router.

my brothers computer can connect no problem to the same router but it is running windows. would there be any merit in trying this usb dongle on a windows machine to check it's working?

Seeing as i have these options do we think that the install is ok, or may there still be issues with the driver instillation? I have listed the contents tar.gz file as requested earlier.

Thanks

~blackjet

[LIST]
[*]makefile
[*]config.in
[*]apdbg.c
[*]Winevl_iface (folder)
[*]src (folder)
[*]scripts (folder)
[/LIST]

---

### Post by balloooza on 2008-12-30
Sory for the delayed responses, but I was watching the first page, but I can conclude that you have a working driver, because those options would only be available if you had a network card, and this is the most suported chipset on the market, do you see the network in the list, and what are the EXACT security settings (you can look at your brothers connection info on vista or xp)

also can you connect (once you have verified that it is  indee WEP, and not WPA) to the network again, and even if you do not have internet, or there is no signal strenth,, can you right click the icon and click "connection information" and tell me what driver you are using (one  of the statistics, under the speed)

There is no reason this should not work, is the switch on on the dongle?

---

### Post by blackjet on 2008-12-30
Hi balloooza,

No problem, I'm just happy to have someone helping me out! :)

My network is not displayed in the network list. I've seen people using ubuntu before and have seen where the available wireless networks are listed but i cannot see mine. So at that point i just selected "Connect to Other Wireless Network" and input the details.

I logged into the router (using a wired connection) and turned off all encryption, even when i do this I cannot connect to the router.

I think something is wrong because the router *is* set to broadcast the network's SSID but as I said, it is not showing up in the Wireless networks list.

any ideas on what to do next?

Edit - there is no physical switch on the usb dongle

Edit again - the exact settings are:
WEP (64bit)
Authentication Type: Automatic
broadcast SSID = true

---

### Post by flyingsliverfin on 2008-12-31
sorry, ill keep watching this thread to see if there is anything else that I can help with,but now this is out of my area. 

Good Luck!!!!

---

### Post by balloooza on 2008-12-31
I hope you are still watching this, can you post the output of
```
lspci
```

and 
```
sudo lshw -C network
```

I should have done this erlier.

---

### Post by blackjet on 2009-01-01
i am, thanks for getting back to me, i was away from home most of today and yesterday, ill run those and post back asap!

---

### Post by NightmareShadow on 2009-01-01
> **blackjet said:**
> i tried that command and this happened:

drew@advent7081:~$ cd Desktop
drew@advent7081:~/Desktop$ ls
apdbg.c    Makefile  scripts  Winevl_iface
config.in  Menudbg   src      ZD1211LnxDrv_2_22_0_0.tar.gz
drew@advent7081:~/Desktop$ sudo modprobe zd1211rw
[sudo] password for drew: 
drew@advent7081:~$

which command should I be running next?

@ everyone -  i cant find a driver online :(
Hey, Did you entered your password when it asked you to?

---

### Post by blackjet on 2009-01-01
here ya go, don't think it matters but i wasn't in range of the wireless network in question when I did this:

drew@advent7081:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter




drew@advent7081:~$ sudo lshw -C network
[sudo] password for drew: 
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:14:2a:dc:da:a5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.0.14 latency=64 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1a:ee:01:60:46
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g

---

### Post by blackjet on 2009-01-01
> **NightmareShadow said:**
> Hey, Did you entered your password when it asked you to?

i did indeed, i think the usb device is now installed as i have wireless connection options, i just cant connect to the router, the network isn't even listed, its a little weird :confused:

---

### Post by flyingsliverfin on 2009-01-03
I don't know if this is the same as a internal wireless, because I know how to do it then, but, you might need to put roaming mode on.

go to system -> administration-> networking. Then you will see three options: wireless, wired connection, and (if you have a modem) point to point connection.

double click the wireless, then in the top left click 'roaming mode'. Actually, this might be very different for you, because this laptop is very bad at detecting wireless networks. (It never  has)#

---

### Post by blackjet on 2009-01-03
hay man, thanks for the idea but roaming mode was already enabled :(

---

### Post by flyingsliverfin on 2009-01-05
oh

sorry, i don't know what else you could do :(

---

