---
title: "[SOLVED] Dell 1505 Wireless"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by ToyotaGuy23 on 2008-12-05
I searched...  =)
I am in need of assistance getting my wireless to function.  

My System:
Dell Insprion 1721
2.0 Ghz AMD TL60
2.0 GB DDR2
250 GB HDD (5400)
Ubuntu 8.10 Intrepid ONLY (no dual boot for me)
Broadcom 440x 10/100 network controller
Dell 1505 draft 802.11n WLAN mini card

There is (was) a driver used called "wl" but it wouldn't work, so i disabled it.  I have also installed something called **ndiswrapper**, which put a new option under System > Administration > Windows Wireless Drivers.  This will allow me to run a windows driver for my networking needs.  I went to support.dell.com, and downloaded the driver, but it was a windows EXE file, and this ndiswrapper is looking for an INF file extension. 

My biggest problem is that I have tried many fixes, and chased SO MANY links, that I just need some help.  Clicking a link that points to four more links has been so hard to follow!  

I'm trying, but I need help!
Thanks!

---

### Post by HotShotDJ on 2008-12-06
> **ToyotaGuy23 said:**
> I went to support.dell.com, and downloaded the driver, but it was a windows EXE file, and this ndiswrapper is looking for an INF file extension.That EXE file is just a self-extracting zip archive. Right click on the EXE file, choose "Open with Archive Manager" -- Extract the file... you will find your required INF file under the DRIVER directory.

---

### Post by newbee70 on 2008-12-06
> **ToyotaGuy23 said:**
> I searched...  =)
I am in need of assistance getting my wireless to function.  

My System:
Dell Insprion 1721
2.0 Ghz AMD TL60
2.0 GB DDR2
250 GB HDD (5400)
Ubuntu 8.10 Intrepid ONLY (no dual boot for me)
Broadcom 440x 10/100 network controller
Dell 1505 draft 802.11n WLAN mini card

There is (was) a driver used called "wl" but it wouldn't work, so i disabled it.  I have also installed something called **ndiswrapper**, which put a new option under System > Administration > Windows Wireless Drivers.  This will allow me to run a windows driver for my networking needs.  I went to support.dell.com, and downloaded the driver, but it was a windows EXE file, and this ndiswrapper is looking for an INF file extension. 

My biggest problem is that I have tried many fixes, and chased SO MANY links, that I just need some help.  Clicking a link that points to four more links has been so hard to follow!  

I'm trying, but I need help!
Thanks!

plug into your network <cable>

Go into system Administration

then into hardware drivers check and see if your drive is enabled.

if is not enabled enable it.

---

### Post by ToyotaGuy23 on 2008-12-06
Thanks for the replies.  

I have taken your suggestions, and when I opened the exe, I found the inf file.  (bcmwl6.inf)

I went to System > Administration > Windows Wireless Drivers and selected bcmwl6.inf and it says "Invalid Driver!" with a big red [color=red][SIZE="4"]X[/SIZE][/color]

I think we are getting close though.  
What is a Broadcom 440x 10/100 Integrated Controller?  
Is it functioning?  Do I need a driver for it too?

What should I try next? 

Thanks again, you all are very helpful.

---

### Post by newbee70 on 2008-12-06
> **ToyotaGuy23 said:**
> Thanks for the replies.  

I have taken your suggestions, and when I opened the exe, I found the inf file.  (bcmwl6.inf)

I went to System > Administration > Windows Wireless Drivers and selected bcmwl6.inf and it says "Invalid Driver!" with a big red [color=red][SIZE="4"]X[/SIZE][/color]

I think we are getting close though.  
What is a Broadcom 440x 10/100 Integrated Controller?  
Is it functioning?  Do I need a driver for it too?

What should I try next? 

Thanks again, you all are very helpful.


Ok, have you installed the ubuntu restricted drivers?

---

### Post by ToyotaGuy23 on 2008-12-06
> **newbee70 said:**
> Ok, have you installed the ubuntu restricted drivers?

Mmm I don't believe so.  
How can I check?

There are only 2 drivers showing up in System > Admin > Hardware Drivers
"wl" and one for ATI video....

---

### Post by newbee70 on 2008-12-06
> **ToyotaGuy23 said:**
> Mmm I don't believe so.  
How can I check?

There are only 2 drivers showing up in System > Admin > Hardware Drivers
"wl" and one for ATI video....

go into applications

add/remove

check all available applications 

in the search box type in ubuntu << should be the first thing up in the list>>

install them < you need internet access on the laptop >>

---

### Post by ToyotaGuy23 on 2008-12-06
OK I found it.  

Now, I'm downloading this pack...50 files of it!
After this, I'll try that driver again, I guess, in System > Admin > Windows Wireless Driver

---

### Post by newbee70 on 2008-12-06
> **ToyotaGuy23 said:**
> OK I found it.  

Now, I'm downloading this pack...50 files of it!
After this, I'll try that driver again, I guess, in System > Admin > Windows Wireless Driver

I think your original problem was just the driver wasn't enabled.

but once you do it may want to go out and upload the broadcom driver and wadcutter for it.

---

### Post by ToyotaGuy23 on 2008-12-06
Still says wrong driver.  

Wonder what I should do now?
Will I need to enable what I just downloaded?

---

### Post by ToyotaGuy23 on 2008-12-06
I got the broadcom driver, but i have no idea what a wadcutter is.

---

### Post by newbee70 on 2008-12-06
> **ToyotaGuy23 said:**
> Still says wrong driver.  

Wonder what I should do now?
Will I need to enable what I just downloaded?

let me bring my laptop up. brb

---

### Post by newbee70 on 2008-12-06
ok got my laptop up what do you show under administration/
 hardware drivers?

---

### Post by ToyotaGuy23 on 2008-12-06
2 drivers 

"wl" and an ati video card one

---

### Post by newbee70 on 2008-12-06
> **ToyotaGuy23 said:**
> 2 drivers 

"wl" and an ati video card one

I forgot 1 very important question; what disto are you using "I'm using 8.04.1


strange mine shows 

ati
broadcom b43 wireless
broadcom sta wireless

I'm have the broadcom b43 enabled

oh hold on you don't have the ati enabled do you, I seem to remember it stopped me and I had to re-install.

---

### Post by ToyotaGuy23 on 2008-12-06
> **newbee70 said:**
> I forgot 1 very important question; what disto are you using "I'm using 8.04.1


strange mine shows 

ati
broadcom b43 wireless
broadcom sta wireless

I'm have the broadcom b43 enabled

oh hold on you don't have the ati enabled do you, I seem to remember it stopped me and I had to re-install.

I'm using 8.10 Intrepid
ATI is enabled, I'll disable, and try again.

---

### Post by ToyotaGuy23 on 2008-12-06
At what point does broadcom come into play?

---

### Post by newbee70 on 2008-12-06
> **ToyotaGuy23 said:**
> I'm using 8.10 Intrepid
ATI is enabled, I'll disable, and try again.



we may have to get some who uses 8.10 to help you. different distro, different kernel, different drivers.

so solutions to problem may be different.

i will see if I can find a wireless tutorial for 8.10

---

### Post by newbee70 on 2008-12-06
> **ToyotaGuy23 said:**
> At what point does broadcom come into play?

broadcom b43 is the wireless driver used in 8.04.1

---

### Post by newbee70 on 2008-12-06
all I could find right now is this.

7. Include the output from the following commands from Terminal (all case sensitive). They help identify your hardware, so provide further detail to potential helpers. If necessary, just copy and paste the text into a text file and upload from a different computer.

Code:

lspci
lsusb
lshw -class network

go ahead and run those and post the results and maybe a guru will help us out on this.

I'll still work on it with you until we get it done. <or fall asleep trying>

---

### Post by ToyotaGuy23 on 2008-12-06
Sure.

lspci-
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

lsusb:
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:af:31:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.102 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:33:52:f7:00:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Hope this is what we need!

---

### Post by ToyotaGuy23 on 2008-12-06
An important tidbit:

I AM using the laptop right now with a wired connection.

---

### Post by newbee70 on 2008-12-06
> **ToyotaGuy23 said:**
> An important tidbit:

I AM using the laptop right now with a wired connection.

great!

try this info I tracked down.


Using Windows Wireless Drivers

Ubuntu supports a system known as NDISWrapper. This allows you to use a Windows wireless device driver under Ubuntu.

 

 1. Obtain the Windows Driver for your system and locate the file that ends with .inf.
  
 2. Install ndisgtk (System &#8594; Administration &#8594; Synaptic Package Manager).
 
 3. Open ndisgtk (System &#8594; Administration &#8594; Windows Wireless Drivers).
  
 4. Select Install new driver.
  
 5. Choose the location of your Windows .inf file and click Install.
  
 6. Click OK.

---

### Post by ToyotaGuy23 on 2008-12-06
Thanks,
I have followed all the steps you've mentioned.  

It still says "invalid driver" after I install "bcmwl6.inf"

I got this driver from support.dell.com and entering my service tag number.  On the drivers and downloads page it set me up with an EXE file, which I opened with package manager, and the ONLY inf file in there was this bcmwl6.  

These steps make sense, seems like it should work.

---

### Post by ToyotaGuy23 on 2008-12-06
maybe a broadcom problem?

---

### Post by newbee70 on 2008-12-06
> **ToyotaGuy23 said:**
> Thanks,
I have followed all the steps you've mentioned.  

It still says "invalid driver" after I install "bcmwl6.inf"

I got this driver from support.dell.com and entering my service tag number.  On the drivers and downloads page it set me up with an EXE file, which I opened with package manager, and the ONLY inf file in there was this bcmwl6.  

These steps make sense, seems like it should work.

out of curiousity if you left click on the network icon in the upper right toolbar what does it say?

---

### Post by Idefix82 on 2008-12-06
It's the same wifi card as mine and I got it working with ndiswrapper. First question: is your Ubuntu 32 or 64 bit? If you are not sure, post the output of
```
uname -a
```
here.

---

### Post by newbee70 on 2008-12-06
Hey toyotaguy I found some more things to try.


Download:

Get the latest version of the ndiswrapper sources from

[http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper) and extract it to home folder.

Open terminal:
We need system software to compile a source code.
Type:
sudo apt-get install build-essential

Go to the ndiswrapper folder using cd command.

cd ndiswrapper-1.53

make distclean

make

Now become root.Type

sudo su

u will be asked for login(root) password.

Type:

make install

Now u have installed ndiswrapper.

Now identify ur wireless card.

Type:

lspci

Name of ur card will be dispalyed.

Now go to this link and find your card from the list and download the windows driver.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

now unpack the driver with command:

unzip filename.exe

Now u have 2 ways to get things done.

The easy way is :

Terminal type:

sudo apt-get install ndisgtk

Now open windows wireless drivers.

In ubuntu open System->Administration->windows wireless drivers

Click install driver.

Now locate .inf file in the folder.Look for hint in the LIST to find the .inf file.

If driver is installed,then reboot.Again take: open System->Administration->windows wireless drivers. click configure network.If u find wireless under connection tab in network.Every thing worked fine and u are lucky u need not use the console(type many command).

If u are a Unlucky Guy.Type in terminal:

ndiswrapper -i filename.inf

Now to check installation type:

ndiswrapper -l

I got this:

netw4x32 : driver installed

device (8086:4222) present (alternate driver: iwl3945)

Where ‘present’ means that you have a card that can be used with the driver installed.If you see ‘cannot locate lspci. Unable to see if hardware is present’, you need to install the pciutils package.

Type:

sudo apt-get install pciutils

depmod -a

modprobe ndiswrapper

To verify that module is loaded type:

dmesg

Make sure it starts at boottime ndiswrapper to

sudo nano /etc/modules

Add

ndiswrapper

Now

cltr +O to write to file

Now reboot.

If u find wireless under connection tab in network.

Every thing worked fine.To make wifi to work better.Enable Backports.

Go System&#8594;Administration&#8594;Software Sources.

Go to the Updates and enable the Hardy Backports repository.Close then click Reload button.Now open a termianl and type:

sudo apt-get install linux-backports-modules-hardy-generic

Now reboot.If u use dell laptop with the wifi catcher opition.Disable it bios by pressing F2 will booting.Wifi catcher will cause a conflict with the driver.

This worked for me.Hope u to get it right!!!


my thanks for who ever wrote this write up.


I have to crash now, and will be back on later good luck.

---

### Post by Idefix82 on 2008-12-06
newbee70, there is absolutely no reason to compile ndiswrapper from source. Also, this instruction seems to refer to several Hardy packages, while the OP is using Intrepid. And it is not going to work because it is not blacklisting the proprietary driver.

Although ToyotaGuy hasn't told me which architecture he has, he should try the following simple three steps, which worked for me and which might work on either architecture:

[LIST=1]
[*]download this driver: [http://ubuntuforums.org/attachment.php?attachmentid=50636&d=1195424847]("http://ubuntuforums.org/attachment.php?attachmentid=50636&d=1195424847")
[*]Unpack it into the Desktop, say
[*]Now copy the following lines into the terminal:
```
sudo modprobe -r wl ndiswrapper
cd Desktop/drivers
sudo ndiswrapper -i bcmwl5.inf
sudo modprobe ndiswrapper

```
[/LIST]
This should get your wireless card working. If it does then the following two lines (plus unchecking the proprietary driver under System->Administration->Hardware drivers) will make the solution permanent:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist
echo "ndiswrapper" | sudo tee -a /etc/modules
```

Hope this helps. If you want to know what each line of code is doing, feel free to ask.

---

### Post by ToyotaGuy23 on 2008-12-06
Sorry folks! 

I use the 32 bit version.  
My processor will support 64 bit, but a user on here recommended the 32 bit version to me.  (For now, anyway)

---

### Post by newbee70 on 2008-12-06
> **ToyotaGuy23 said:**
> Sorry folks! 

I use the 32 bit version.  
My processor will support 64 bit, but a user on here recommended the 32 bit version to me.  (For now, anyway)


Have you got it up and running then?   :D

---

### Post by Idefix82 on 2008-12-06
> **ToyotaGuy23 said:**
> Sorry folks! 

I use the 32 bit version.  
My processor will support 64 bit, but a user on here recommended the 32 bit version to me.  (For now, anyway)

Have you tried the solution anyway? It's reported to also work for 32 bit.
On a side note: how much RAM do you have?

---

### Post by ToyotaGuy23 on 2008-12-06
Sorry to mislead in my previous post. 

My wireless is not working, and has not worked yet.  

IDEFix, when I tried to run your commands, I was asked for a sudo password.  Is there a way I can login as an admin?

I'm still trying here, I haven't given up.  
I will mark this topic SOLVED when we're done.

Thanks again so much for your replies.

---

### Post by ToyotaGuy23 on 2008-12-06
> **newbee70 said:**
> out of curiousity if you left click on the network icon in the upper right toolbar what does it say?
[B]
Wired network is grayed out
Auto eth0 is marked with a dot

VPN connections > Configure VPN
Under wireless tab, I have created 'wireless connection 1' 
This is where I typed in my ssid, and WPA code[/B]

> **Idefix82 said:**
> 
Although ToyotaGuy hasn't told me which architecture he has, he should try the following simple three steps, which worked for me and which might work on either architecture:

[LIST=1]
[*]download this driver: [http://ubuntuforums.org/attachment.php?attachmentid=50636&d=1195424847]("http://ubuntuforums.org/attachment.php?attachmentid=50636&d=1195424847")
[*]Unpack it into the Desktop, say
[*]Now copy the following lines into the terminal:
```
sudo modprobe -r wl ndiswrapper
cd Desktop/drivers
sudo ndiswrapper -i bcmwl5.inf
sudo modprobe ndiswrapper

```
[/LIST]

**In terminal, it asks for sudo password, but won't accept ANY INPUT from the keyboard... no matter which key is pressed.**

> **Idefix82 said:**
> Have you tried the solution anyway? It's reported to also work for 32 bit.
On a side note: how much RAM do you have?

[b]2 GB RAM
Should be plenty, right?[/b]

---

### Post by newbee70 on 2008-12-06
ToyotaGuy;

here is another link to the broadcom issue.

it talks about driver conflicts, maybe thats what we are facing.

**gotta say you have more patience than I do, by now I would have done a clean install and started from scratch. **

[http://ubuntuforums.org/showthread.php?t=963978](http://ubuntuforums.org/showthread.php?t=963978)

crossing my fingers for ya.


maybe some of the guru's will get into this thread.

---

### Post by ToyotaGuy23 on 2008-12-06
> **Idefix82 said:**
> 

[LIST=1]
[*]download this driver: [http://ubuntuforums.org/attachment.php?attachmentid=50636&d=1195424847]("http://ubuntuforums.org/attachment.php?attachmentid=50636&d=1195424847")
[*]Unpack it into the Desktop, say
[*]Now copy the following lines into the terminal:
```
sudo modprobe -r wl ndiswrapper
cd Desktop/drivers
sudo ndiswrapper -i bcmwl5.inf
sudo modprobe ndiswrapper

```
[/LIST]
This should get your wireless card working. If it does then the following two lines (plus unchecking the proprietary driver under System->Administration->Hardware drivers) will make the solution permanent:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist
echo "ndiswrapper" | sudo tee -a /etc/modules
```


OK, I figured out the password thing (thanks sirjoebob) 
NOW i can get as far as cd Desktop/drivers

Terminal says: 
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

I DO have the drivers folder on the desktop.
That INF file IS in that folder.

---

### Post by Idefix82 on 2008-12-06
> **ToyotaGuy23 said:**
> NOW i can get as far as cd Desktop/drivers

Terminal says: 
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

I DO have the drivers folder on the desktop.
That INF file IS in that folder.

Sorry, my bad. You have to use the full path:
```
sudo ndiswrapper -i ~/Desktop/drivers/bcmwl5.inf
```
The rest is as before.

---

### Post by WinterMadness on 2008-12-06
the exe is good, get WINE  through synaptic. youll get an error message but it wont matter.

MAKE SURE THE DRIVER IS A WINDOWS XP DRIVER.

good luck  :)

---

### Post by ToyotaGuy23 on 2008-12-07
OK, the inf and sys files were actually in Desktop > drivers > drivers, so that put me behind a little bit.  

Terminal says bcmwl5.inf is installed 
It does NOT however show up in System > Admin > Hardware drivers... Should it?

I have gone into Network Connections and under the wireless tab setup "wireless connection 1" and put in my ssid.  I was wondering if the whole wpa key thing was getting in the way, so I have also reset the router.  The router is a linksys wrt160n, ssid is 'linksys', and no pw right now.  

What are the steps taken to connect over wireless NORMALLY?  
You get to the coffee shop, boot up, and go to .... ??

Thanks

---

### Post by Idefix82 on 2008-12-07
> **ToyotaGuy23 said:**
> 
Terminal says bcmwl5.inf is installed 
It does NOT however show up in System > Admin > Hardware drivers... Should it?
No, it shouldn't. Can you do me a favour and post here the output from
```
lshw -C network
```

You have followed the steps I have given you through to the end, right? If the driver is installed and recognises the card then you should just be able to see the available wireless networks by left clicking on the network manager icon. To connect to one you should only have to click on it and enter the password if asked for it.

---

### Post by ToyotaGuy23 on 2008-12-07
> **Idefix82 said:**
> No, it shouldn't. Can you do me a favour and post here the output from
```
lshw -C network
```

You have followed the steps I have given you through to the end, right? If the driver is installed and recognises the card then you should just be able to see the available wireless networks by left clicking on the network manager icon. To connect to one you should only have to click on it and enter the password if asked for it.

**Yes, I have followed all the steps you've provided.  The only exception was the blacklist commands, because you wanted me to run them "if this works," and since it didn't, I didn't continue with those blacklist commands. **

here is what terminal said:
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:af:31:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:e3:60:87:89:50
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
[B]
Do you need to know anything about my network/ISP/hardware?
Just in case, Road Runner, Router WRT160N by Linksys, Modem issued by ISP.  

When terminal says WARNING: you should be a super user, should I have run a sudo command?  or login as root somehow?  or just ignore that..?[/B]

---

### Post by newbee70 on 2008-12-07
ToyotaGuy:

I just converted my laptop to 8.10 to see what problems I could help you with.

unfortunately after 597 updates.

installed apt on cd and made an ISO so if everything went to crap I didn't have to spend over an hour of updating.

I went into the administration / hardware drivers

activated the b43 driver.

rebooted my system.

during reboot I unplugged the wired network.

when booted up I went to the network icon clicked on it and it had found my linksys 54g.

told it to connect. it put up a wep desplay 
<here it had wep<48/128> as default **changed to 128.**


** added this from my laptop **

it came back and asked for the router pass phrase **entered it and went right online.**


Maybe you should do a clean install and try this.
to end your frustration.

---

### Post by ToyotaGuy23 on 2008-12-07
Is there another fix other than reinstalling the OS?

---

### Post by newbee70 on 2008-12-07
> **ToyotaGuy23 said:**
> Is there another fix other than reinstalling the OS?

Probably, if you look long enough or the right person helps. 
You must have the patience of job. I would be ](*,)  by now,

The bright side is ** Your learning alot about Ubuntu, terminal, installation, and troubleshooting wifi / drivers.**

where are you at now on the problem?

---

### Post by ToyotaGuy23 on 2008-12-08
> **newbee70 said:**
> Probably, if you look long enough or the right person helps. 
You must have the patience of job. I would be ](*,)  by now,

The bright side is ** Your learning alot about Ubuntu, terminal, installation, and troubleshooting wifi / drivers.**

where are you at now on the problem?
[B]
I'm thinking about buying an ethernet cable about 5 miles long, and running it from my router to the coffee shop!

Should we post this in the networking section of the board?

Also, I noticed this at linuxwireless...[/B]
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
[B]
It says there is no support for the pci id 4328 (which is what I have) (I think)  [/B]

---

### Post by newbee70 on 2008-12-08
> **ToyotaGuy23 said:**
> [B]
I'm thinking about buying an ethernet cable about 5 miles long, and running it from my router to the coffee shop!

Should we post this in the networking section of the board?

Also, I noticed this at linuxwireless...[/B]
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
[B]
It says there is no support for the pci id 4328 (which is what I have) (I think)  [/B]




here is the word I had messed up ** b43-fwcutter**

**have you already done this?**

** If you have already done this then there is little more we can do but ask that it be moved to the main board thread **



Originally Posted by slocumkaroff View Post

In thread first step was to enter line "sudo / usr/... I entered password as directed. Was told command not accepted
No offence, but you have to read entire threads to get the context - had you done that, you would have seen that the command failed for that other chap as well because he didn't have b43-fwcutter installed. Now, because I feel generous and insomniac, I shall summarise that entire thread for you here:

Hook your computer up to a wired connection. Make sure you have internet access (by browsing to a website or whatever). Go to Applications -> System -> Administration -> Synaptic.

There make sure that in "Settings - Repositories" you have ticked all tickable boxes in the "Ubuntu software" section, i.e. you should have ticked all the boxes next to "main, universe, restricted, multiverse". Deselect the CD-rom.

Then, in Synaptic click on the button that says: "Reload". After that, use synaptics search function (not "quick search", but the proper search) and look for "b43-fwcutter". It'll take a moment. Once it's found, right click the package and choose "Mark for installation" and then click the "Apply" button in the upper left hand corner in the Synaptics window. Once b43-fwcutter is installed, try running:

Code:

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

That should work and do everything automatically for you (if it worked, reboot).

If that fails, you'll just have to install the firmware manually. Do the following in a terminal (keep the same terminal window open).

Code:

wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

This will download the firmware.

Code:

tar xjf broadcom-wl-4.150.10.5.tar.bz2

This will unpack it.

Code:

cd broadcom-wl-4.150.10.5/driver

This will put us in driver directory.

Code:

sudo b43-fwcutter -w /lib/firmware wl_apsta_mimo.o

This will cut and install the firmware. Check that you have a directory called "b43" in your /lib/firmware - if everything went correctly, it should be there and contain a bunch of files.

Next run:

Code:

sudo rmmod b43 [press enter]
sudo modprobe b43

Check network manager. You should now be able to pick up APs/Wireless routers.

---

### Post by newbee70 on 2008-12-08
Your right; I must have been in a brain-freeze.

** quote from post 41 **

here is what terminal said:
WARNING: you should run this program as super-user.
*-network
description: Network controller
product:** BCM4328 802.11a/b/g/n**
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0b:00.0


** From Linux Wireless **

unsupported

    * The 802.11a part of the 4309 and 4312 is not supported.
    * BCM 4310 USB - This device has an LP PHY. We think that means low power. In any case, previous code does not work. The reverse engineers have translated a great deal of the code and are currently generating specs for the code writers. Note: This card uses the PCI buss, despite its name.
    * BCM 4322 802.11a/b/g/n (Has PCI-ID 0x432B) - This device has an N Phy. There is no support for any Draft 802.11n features. We are working on it.
 **   * BCM 4321 (Has PCI-IDs 0x4328 and 0x4329) - These devices have N Phys. There is no support for any Draft 802.11n features. We are working on it. **


so yeah, I think you should put it on the main boards.

Sorry I couldn't help ya with it.

---

### Post by newbee70 on 2008-12-08
Hey ToyotaGuy;

maybe a ray of hope.

here is a link I just found.

See if this makes sense to you.

I realize it is for a different unit but read the article, and it's instructions.


**[http://wiki.archlinux.org/index.php/Broadcom_BCM4312](http://wiki.archlinux.org/index.php/Broadcom_BCM4312) **

---

### Post by Idefix82 on 2008-12-08
> **ToyotaGuy23 said:**
> 
It says there is no support for the pci id 4328 (which is what I have) (I think)

It simply means that you have to use ndiswrapper and that there is no driver in the kernel which can handle the card. Reinstalling the OS is not a fix at all. We would get it fixed within half an hour if you stayed online when I come on and replied promptly.

What has happened now is that another inbuilt driver has taken over instead of ndiswrapper. So you have to kick that out as well and hope that this time ndiswrapper takes over. You will have to repeat this until the output from lshw -C network shows that the driver used for the card is ndiswrapper. Your last output shows that after wl is gone, b43-pci-bridge takes over. So please type in
```
sudo modprobe -r wl b43-pci-bridge
sudo modprobe ndiswrapper
```

---

### Post by ToyotaGuy23 on 2008-12-08
**OK I ran these:**
```
sudo modprobe -r wl b43-pci-bridge
sudo modprobe ndiswrapper
```

**I got this:**
matt@matt-laptop:~$ sudo modprobe -r wl b43-pci-bridge
[sudo] password for matt: 
FATAL: Module b43_pci_bridge not found.
matt@matt-laptop:~$ sudo modprobe ndiswrapper
matt@matt-laptop:~$ 

**I ran lshw -C network and got:**
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:af:31:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.102 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:10:f4:ab:b6:9e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A

---

### Post by Idefix82 on 2008-12-09
Can you try
```
sudo modprobe -r wl b43 b43legacy bcm43xx
sudo modprobe ndiswrapper
```
Go ahead with the second line regardless of any errors that you may get from the first, but let me know what sorts of errors you got.
Basically, I hope you got the idea: keep throwing out modules that prevent ndiswrapper from taking over (the first line throws out several modules that I suspect might be in the way, but I'm only guessing since we have different Ubuntu versions) and then start ndiswrapper. The lshw... command will show you which driver is currently in charge. I will be very surprised if that doesn't work out eventually. I will be away today and tomorrow but will come back in about 48 hours time and see how you are doing. If we don't get it then, I might just download 8.10 and try to do the whole procedure while booting from the Live CD.

---

