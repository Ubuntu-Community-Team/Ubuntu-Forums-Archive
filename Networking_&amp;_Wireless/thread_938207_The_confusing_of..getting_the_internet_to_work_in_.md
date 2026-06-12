---
title: "The confusing of..getting the internet to work in ubuntu"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by .Kai on 2008-10-04
I unintalled xbuntu and moved on to ubuntu 8.10(least beta.) 
and yeah I'm a new user to this type of OS I've been using Windows for awhile now...

I've been trying to get my NETGEAR WG311v3 to work.

and I've seen to have no luck. most of the things I saw confused me.

anyone know any simple steps to installing this driver in Ubuntu 8.10 beta?
thanks.
and I'm a complete noob to this as you can already tell.. =/

Edit:
Also it needs some kind of WEP key to connect to the gateway as well.

---

### Post by cariboo on 2008-10-04
It is not really recommended for someone that has so little user experisnce to use Intrepid, as ther are a lot of things broken that have yet to be fixed. With little or no experience with any linux distribution you might have a hard time getting things to work properly. That being said, you should direct nay guestion concerning Intrepid here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

There are a lot of people habing out there that would be more than happy to help

You can start by entering in a Applications-->Accessories-->Terminal:

```
lspci
```

and pasting the output in your next post.

Jim

---

### Post by .Kai on 2008-10-05
> **cariboo907 said:**
> It is not really recommended for someone that has so little user experisnce to use Intrepid, as ther are a lot of things broken that have yet to be fixed. With little or no experience with any linux distribution you might have a hard time getting things to work properly. That being said, you should direct nay guestion concerning Intrepid here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

There are a lot of people habing out there that would be more than happy to help

You can start by entering in a Applications-->Accessories-->Terminal:

```
lspci
```

and pasting the output in your next post.

JimThanks for the link I will try to learn a lot from you guys. I might go download 8.04 later today. for now I want to see how to internet works on here.

here's the info you needed.
[SIZE="1"]
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
02:04.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)[/SIZE]

---

### Post by .Kai on 2008-10-05
Bump anyone? : P

---

### Post by iponeverything on 2008-10-05
it looks like it will work ndiswrapper

see:

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

---

### Post by .Kai on 2008-10-05
Okay I got ndiswrapper installed.
And the driver I think...
I type in some kind commened and it says
"Error WG311v3 is an invalid driver" or something like that any way to fix that?

thanks!

---

### Post by .Kai on 2008-10-06
Bump! Anyone?  sorry for being annoying. >_<

---

### Post by Bucky Ball on 2008-10-06
Yep, you are using the wrong driver by the looks. Have you got windoze installed on this machine also? If so, check to see what driver that is using for wireless and use that one with ndiswrapper. You could load this onto a usb dongle and then load into ubuntu. :)

This is old but might help:

[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

... And this thread guides you from start to finish ...

[http://ubuntuforums.org/showthread.php?t=474306](http://ubuntuforums.org/showthread.php?t=474306)

---

### Post by .Kai on 2008-10-06
Yes I have XP + Ubuntu
On the [https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k) link you gave me I don't get the 

mkdir mrv
cd mrv
wget -c [http://www.cafuego.net/stuff/mrv.zip](http://www.cafuego.net/stuff/mrv.zip)
unzip mrv.zip
sudo ndiswrapper -i mrv8335.inf
sudo ndiswrapper -m
cd ..
rm -rf ./mrv

part it looks like it's trying to get the file from the internet how to fully install it? o.O

I'm trying other things right though though..(Need to restart my computer on Ubuntu right now.

---

### Post by Bucky Ball on 2008-10-07
```
wget -c [http://www.cafuego.net/stuff/mrv.zip](http://www.cafuego.net/stuff/mrv.zip)
```Yes, it is trying to access the net. If you have a wired connection to get the wireless happening it would be convenient. If not, follow what I said before. You need to use the same driver your XP install is using to get wireless up with ndiswrapper.

If you can access your XP drives from Ubuntu, find the driver, make a copy of it and place it somewhere you are going to be able to get at it from Ubuntu. Plop the copied driver folder on to the desktop or wherever you need in Ubuntu, then follow the ndiswrapper procedure.

You need to check on XP that "WG311v3 is an invalid driver". If it is the right driver, the one XP is using, that driver probably won't work with ndiswrapper or you have made a mistake along the way. Easy to do. :)

---

### Post by .Kai on 2008-10-08
Hey guys I removed Ubuntu(the files..)and reinstalled/Redownloaded  it and I clicked "Install inside windows" and then it looks like it's trying to download something it didn't do that last time.

And I was trying to get Ubuntu 8.04 and it did all of that.
I don't know why I removed that other file of it I downloaded. >_<

anyway anyone know where to get the file that downloads everything on ubuntu?

Sorry for being kinda off the main topic I just didn't want to have more then one thread. =p

also I'm trying to do this first before I try out the internet thingy.

---

### Post by .Kai on 2008-10-15
Alright I got Ubuntu 8.04 installed and I still can't seem to get the network to work. I got the screenshot of it so you might be able to help me out more:
[[IMG]http://img357.imageshack.us/img357/4520/screenshotgj0.th.png[/IMG]](http://img357.imageshack.us/my.php?image=screenshotgj0.png)[[IMG]http://img357.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)
can anyone help? this is confusing me. >_<

---

### Post by .Kai on 2008-10-15
Any I get some help? thanks! : )

---

### Post by Bucky Ball on 2008-10-16
Read my previous posts and this:

[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

Again, you need to get into Windoze, find the wireless drivers it is using for your Marvell wireless card, make a copy of the driver folder, boot Ubuntu and use the drivers in the copied folder with ndiswrapper. Good luck with it. :)

---

### Post by itsjareds on 2008-10-16
I really suggest installing it inside Windows, this is pretty much the same as installing on another partition, with a few differences. I'm using XP with Ubuntu 8.04 (Ubuntu installed with Wubi - Windows UBuntu Installer) and it's pretty good. If I ever had to uninstall the Heron, I could use the Windows Add and Remove programs.

But if you insist on installing on a new partition that is fine :P

I recommend talking to [Pytheas22]("http://ubuntuforums.org/member.php?u=358340"), I think he has the same wireless card as you do.

---

### Post by .Kai on 2008-10-16
> **Bucky Ball said:**
> Read my previous posts and this:

[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

Again, you need to get into Windoze, find the wireless drivers it is using for your Marvell wireless card, make a copy of the driver folder, boot Ubuntu and use the drivers in the copied folder with ndiswrapper. Good luck with it. :)
Lol I'm stupid I'll try it. >_< 
@itsjareds If all doesn't go well I'll try talking to him thanks.

---

### Post by .Kai on 2008-10-19
Uhh still very confusing for me.

---

### Post by pytheas22 on 2008-10-20
I don't actually have this same wireless card, but I did help itsjareds get it working over the summer.  With WPA it's very difficult, but if you only need to use WEP it shouldn't be that hard.

Try running the following commands (you will need to be online first somehow, so plug into ethernet if possible; if that's totally impossible, let me know):
```

sudo ndiswrapper -r wg311v3
wget http://www.avengergear.com/upload/WG111v3.tar.bz2
tar xjvf WG111v3.tar.bz2
cd WG111
sudo ndiswrapper -i WG111v3.inf
```

Then reboot and you should be able to see networks and connect using Network Manager.  If not, please post the output of:
```

ndiswrapper -l
uname -m
dmesg | grep -e ndis -e wg111 -e wlan
lsusb
```

---

### Post by .Kai on 2008-10-20
Yeah it's kinda impossible since I'm not allowed to play around with the ethernet thingy.

---

### Post by pytheas22 on 2008-10-20
It's alright if you can't get ethernet; you'll just need to do a little extra work.

First, download [this file]("http://www.avengergear.com/upload/WG111v3.tar.bz2") and save it to a USB stick or CD.  From there, transfer it to your Ubuntu machine, and save it on the desktop there.

Next, run these commands:
```

sudo ndiswrapper -r wg311v3
cd ~/Desktop
tar xjvf WG111v3.tar.bz2
cd WG111
sudo ndiswrapper -i WG111v3.inf
```

Then reboot.  If things still don't work, please post the output of:
```

ndiswrapper -l
uname -m
dmesg | grep -e ndis -e wg111 -e wlan
lsusb
```

---

### Post by .Kai on 2008-10-21
Well I think I got it installed right but it didn't work when I rebooted. :( 
here's the needed info
[size=1]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000 
[/size]

---

### Post by pytheas22 on 2008-10-21
Please post the output of all of the following commands (make sure your WG111v3 is plugged in before you run the commands):
```

ndiswrapper -l
uname -m
dmesg | grep -e ndis -e wg111 -e wlan
lsusb
```

If you want, you can save the output to a text file (Applications>Accessories>Text Editor), put it on a USB stick, then transfer it to a computer with Internet access so that you can post all of the output here, without having to type it out by hand.

---

### Post by .Kai on 2008-10-21
I didn't post them all at once but this is what I get.
wg111v3 : driver installed
i686
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000

---

### Post by pytheas22 on 2008-10-21
Was the wireless card plugged in when you ran those commands?  It looks like the card is not connected at all.  It may help to try plugging into a different USB port--perhaps the one that the card is in now is damaged for some reason.

Also, you're sure that the card itself definitely works, right?  Have you used it in any other computers recently?

Please try using a different USB port, then post the output of the following commands again:
```

ndiswrapper -l
dmesg | grep -e ndis -e wg111 -e wlan
lsusb
```

---

### Post by .Kai on 2008-10-21
I just found out I installed the wrong driver. I'm really using NETGEAR WG311v3 and not wg111v3

---

### Post by pytheas22 on 2008-10-21
Sorry, that may have been my fault for reading your post too quickly.

Either way, the files that you need are available [here]("ftp://downloads.netgear.com/files/wg311v3_1_0.zip").  Unfortunately the download is really really slow, but I'm downloading them now and can upload them to a faster server, and give you line-by-line instructions on what you need to do to get the right drivers installed into ndiswrapper.

However, I'm still wondering why your 'lsusb' output doesn't mention the presence of the wireless card.  It's a USB card, right?  If so, when you type 'lsusb' with the card plugged in, you should see a line pertaining to your card.  So far, the output you've given only mentions a Microsoft mouse; that's why I think you should try plugging the wireless card into a different USB port and typing 'lsusb' again, just to make sure the system recognizes that the card exists.

I'll post back in a few hours with updated instructions when the download finishes.

EDIT: the download went from 2Kb/s to 300, so I got the file.  Follow these instructions to install it:

1. download [this file]("http://burnthesorbonne.com/files/WG311v3.tar.gz"), save it to a USB stick, and transfer it to your Ubuntu machine.  Save it to the desktop there.

2. run:

```
sudo ndiswrapper -r wg111v3
cd ~/Desktop
tar -xzvf tar -xzvf WG311v3.tar.gz
cd Windows\ 2000/
sudo ndiswrapper -i WG311v3.INF
```

Then reboot.  If things still don't work, please post the output of:

```
ndiswrapper -l
dmesg | grep -e ndis -e wg111 -e wlan
lsusb
```

---

### Post by .Kai on 2008-10-22
Weird it still doesn't work when I change the place of the driver and the output is still the same.

---

### Post by pytheas22 on 2008-10-22
What do you mean by 'change the place of the driver' and what is the output now of:

```
ndiswrapper -l
dmesg | grep -e ndis -e wg111 -e wlan
lsusb
```

I'm not sure exactly what you mean.

---

### Post by .Kai on 2008-10-24
Sorry for taking so long to post..

Well I mean I moved the wireless router to another place in my computer. and it still shows the same output when I type that same commend. and yeah I tried installing that driver on ubuntu and rebooted and it still doesn't connection to the internet and is it because the main ethernet needs some kind of WEP key?

---

### Post by pytheas22 on 2008-10-25
I'm not sure what's going on.  It would be really good to see the output after a reboot of:
```

ndiswrapper -l
dmesg | grep -e ndis -e wg111 -e wlan
lsusb
ifconfig
```

---

### Post by .Kai on 2008-10-27
This is all I get:

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000

---

### Post by pytheas22 on 2008-10-27
Sorry we still haven't been able to make any concrete progress here, but the problem appears still to be that the system does not see a USB wireless device attached at all.  This wireless card is a USB dongle, right?  If so, I suspect either a problem with the card itself, or with your USB ports.  Does the card work in other computers?  Did you try moving it to a different USB port?

---

### Post by .Kai on 2008-10-29
Yeah I tried that it still didn't work..

---

### Post by pytheas22 on 2008-10-29
The only thing I can think of is hardware failure.  Unless this wireless card works in other computers, I'd conclude that it's just broken, as Ubuntu doesn't seem to be able to see that it exists at all.

It's possible that dmesg would say something about the hardware being broken.  If you unplug the card, plug it back in, and then run the following command, what's the output:
```

dmesg | tail
```

---

### Post by .Kai on 2008-11-02
Sorry some things came up. that's why it toke awhile for me to post again sorry here's the needed info.
dmesg | tail

[   59.768477] Bluetooth: RFCOMM ver 1.8
[   61.468534] [drm] Initialized drm 1.1.0 20060810
[   61.498214] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 20
[   61.498552] [drm] Initialized r128 2.5.0 20030725 on minor 0
[   61.500089] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   61.500428] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   61.500451] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   75.767161] NET: Registered protocol family 10
[   75.767976] lo: Disabled Privacy Extensions
[   75.768873] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by pytheas22 on 2008-11-02
Unfortunately, it doesn't look like it's seeing a USB device being plugged in at all.  Usually it would say something, whether the device is working or not.  Are you sure that this wireless card works in other computers?  Did you try it in Windows?  Based on everything I've seen, the only conclusion I can draw is that your wireless card is broken.

---

### Post by .Kai on 2008-11-04
It works just fine in Windows. I don't know why It wont work in Ubuntu I guess it's because something is missing from the network thingy. [http://i34.tinypic.com/35cissk.jpg](http://i34.tinypic.com/35cissk.jpg) (That's in red.)

---

### Post by pytheas22 on 2008-11-04
ohhhhhhhh it's a PCI card.  I thought that it was a USB stick for some reason.  This explains a lot.  What is the output of:
```

lspci -nn
lshw -C Network
```

---

### Post by .Kai on 2008-11-07
Here's the info you needed:

Network

00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 05)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 05)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 05)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 05)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage 128 Pro Ultra TF [1002:5446]
02:04.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)

I'll try replying faster.

---

### Post by pytheas22 on 2008-11-08
Thanks for the information.  Please try following these steps:

1. download [this file]("http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip") and save it to your desktop

2. run these commands:

```
cd ~/Desktop
unzip ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip
cd V1.10/DRIVER/Windows\ XP/
sudo ndiswrapper -i Mrv8000c.inf
echo ndiswrapper | sudo tee -a /etc/modules
sudo ndiswrapper -r wg311v3
sudo ndiswrapper -r WG111v3
```

Then reboot.  If the wireless doesn't work after a reboot, please post the output of:
```

lshw -C Network
ndiswrapper -l
sudo iwlist scan
dmesg | grep -e ndis -e wlan
```

---

### Post by .Kai on 2008-11-08
Still didn't seem to work. D:

Here's the info needed:

[SIZE="1"]WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=66
  *-network:1
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:08:02:36:47:fb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes

This is the other stuff it have:

mrv8000c : driver installed
	device (11AB:1FAA) present
wg311v3 : invalid driver!

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

[/SIZE]

---

### Post by pytheas22 on 2008-11-08
Please run:
```

sudo ndiswrapper -r wg311v3
```

Please also post the output of:
```

dmesg | grep -e wlan -e ndis
lsmod | grep ndis
```

It thinks that you have the right driver now (according to 'ndiswrapper -l'), so we're making progress.

---

### Post by .Kai on 2008-11-08
This is all I get:

dmesg | grep -e wlan -e ndis
lsmod | grep ndis

couldn't delete /etc/ndiswrapper/wg311v3: No such file or directory

---

### Post by pytheas22 on 2008-11-08
It looks like the ndiswrapper module is not being loaded...

What is the output of these commands (in this order):
```

sudo modprobe ndiswrapper
dmseg | grep -e ndis -e wlan
sudo iwlist scan
```

---

### Post by RobOrr on 2008-11-09
This is exactly how i installed my WG111v3 USB adaptor on 8.04 Hardy Heron Ubuntu:
I couldnt easily find the .inf file that you need, so if you have windows or wine installed, run the setup.exe that comes either on the driver CD with the WG11v3 or search on google for "drivers WG111v3". you'll be able to get the setup file. run the installer, and in windows the file you need is "C:\windows\inf\WG111v3.inf" or in ubuntu
 "/home/.wine/drive_c/windows/inf/WG111v3.inf". in wine, the installation will not complete successfully, but it still puts the inf file here, so its ok. remove all the files from the installation afterwards and keep this inf file safe.(just replace home with your actual home name - its your ubuntu username, e.g. jeff, steve etc)

once you have that file found, run Synaptic Package manager, ensure that in the options you have the multiverse and universe repositories enabled, and use the search button to locate ndisgtk. install this package, and it'll show up in your System>Administration>Windows Wireless Drivers menu. run that, and click install driver. browse to the WG111v3.inf file you've looked after and select it. This can be done without the adapter plugged in. Once the adapter is plugged in, open Terminal and run lsusb. If there isn't a device shown with Netgear in it's name, try a different USB port (turns out one on my computer is broken, that gave me headaches for a while) but you shouldnt have issues here. if it is there in the list, then you should get some monitor shaped icons on your panel. click them, and you should get your list of networks that your adapter can find!

---

### Post by .Kai on 2008-11-24
Sorry I formated my computer so I'll have to re install everything it might be awhile..
@RobOrr Doesn't work, I tried it way before I had to reformat it.

---

### Post by pytheas22 on 2008-11-24
> Sorry I formated my computer so I'll have to re install everything it might be awhile..

That's alright, but I'm still happy to try to get this solved when you have time, so please keep us updated.

---

### Post by .Kai on 2008-11-27
Got everything re installed faster then I thought lol.

Here's the info needed from last time:

[SIZE="1"]sudo modprobe ndiswrapper
dmseg | grep -e ndis -e wlan
sudo iwlist scan


kyo@ubuntu:~$ sudo modprobe ndiswrapper
[sudo] password for kyo: 
kyo@ubuntu:~$ dmseg | grep -e ndis -e wlan
bash: dmseg: command not found
kyo@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

kyo@ubuntu:~$[/SIZE]

---

### Post by pytheas22 on 2008-11-28
Thanks for the information.  Unfortunately, ndiswrapper still doesn't seem to be bringing up the interface.  Did you install the Windows drivers and everything?  What is the output of:
```

dmesg | grep -e ndis -e wlan
ndiswrapper -l
lshw -C Network
```

---

### Post by .Kai on 2008-11-28
Yeah I think I got everything installed. 
Here's the info: 
[SIZE="1"]kyo@ubuntu:~$ dmesg | grep -e ndis -e wlan
kyo@ubuntu:~$ ndiswrapper -l
kyo@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=66
  *-network:1
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:08:02:36:47:fb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:81:63:dc:b4:1d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/SIZE]

---

### Post by pytheas22 on 2008-12-01
It doesn't look like there's any Windows driver loaded into ndiswrapper.  Please try following these steps to get the right one installed:

1. download [this file]("http://www.3com.com/products/en_US/result.jsp?selected=6&sort=effdt&sku=3CRGPC10075&order=desc") and transfer it to your Ubuntu computer (you will need to agree to some stuff before you can begin the download).  Save it on your desktop there.

2. run these commands:
```

cd ~/Desktop
unzip 3CRGPC10075_08_18_2005.exe
cd Driver/Win2kXP
sudo ndiswrapper -i mrv8335x.inf
echo ndiswrapper | sudo tee -a /etc/modules
```

If it's not too much work, please post the output of those commands so that I can check to make sure they all go as planned.

After that, reboot, and things should work.  If they don't, what is the output of:
```

dmesg | grep -e ndis
lshw -C Network
lsmod | grep ndis
uname -m
```

---

### Post by .Kai on 2008-12-01
finaly  I got it to working!! thank you for all your help and sorry I forgot to copy down the output of them but all of them went through with no errors in them at all. :) and thank you again!!! now I can enjoy ubuntu even more now!! :)

---

### Post by pytheas22 on 2008-12-02
Glad to hear it's finally solved :)

---

### Post by stooshbunutu on 2008-12-09
If you're still stuck I have written a tutorial on how to use an encrypted WG111v3

see my tutorial:
[On My Website]("http://helpbuntu.mstrutt.co.uk/wireless.html")
[On Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=732827&highlight=wg111v3")

Hope you get it sorted

---

