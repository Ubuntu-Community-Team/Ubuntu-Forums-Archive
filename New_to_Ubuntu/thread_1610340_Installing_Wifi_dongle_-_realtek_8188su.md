---
title: "Installing Wifi dongle - realtek 8188su"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by Panawe on 2010-10-31
Folks,
I have been struggling with this all day!
Backstory - installed Ubuntu 10.10 on new computer, got it working with Windows 7 and all seemed hunky dory until I suddenly lost network access on both platforms. Tracked problen down to mobo LAN connector. Decided to bypass LAN and use a Dynamode wireless 11N USB adapter (which has realtek 8188SU chip).
Got this working with Windows 7 in a few minutes but can't get the f***er to work in Ubuntu.
I have got the linux drivers for this and Googled a bit and I have done the following...
 

[FONT=Times New Roman][SIZE=2]*1) extract the driver from the driver's folder. you can use 'archive manager' or from a command line:*[/SIZE][/FONT]
 
*[SIZE=2][FONT=Times New Roman]$ tar zxvf rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.201006 25.tar.gz[/FONT][/SIZE]*
 
*[SIZE=2][FONT=Times New Roman]2) make 8712 USB driver module (doesn't matter that the chipset is 8188SU), use a terminal window and navigate to the folder you just extracted[/FONT][/SIZE]*
 
*[SIZE=2][FONT=Times New Roman]$ make[/FONT][/SIZE]*
 
*[SIZE=2][FONT=Times New Roman]3) clean the operation environment, I needed to have root permission to get this to work[/FONT][/SIZE]*
 
*[SIZE=2][FONT=Times New Roman]$ sudo ./clean[/FONT][/SIZE]*
 
*[SIZE=2][FONT=Times New Roman]4) insert 8712 USB modules, with root access[/FONT][/SIZE]*
 
*[SIZE=2][FONT=Times New Roman]$ sudo insmod 8712u.ko[/FONT][/SIZE]*
 
*[SIZE=2][FONT=Times New Roman]After that, the blue light came on and the card was able to connect to networks via the NetworkManager applet. Hope this works for you"[/FONT][/SIZE]*

[FONT=Times New Roman]But the hardware still doesn't seem to be installed! [/FONT]
[FONT=Times New Roman]The other steps I had no luck with....[/FONT]

[FONT=Times New Roman][LIST=1]
[*][FONT=Arial][COLOR=black][FONT=Cambria]*[SIZE=2]enable wlan0 interface[/SIZE]*[/FONT][/COLOR][/FONT]
[/LIST][FONT=Arial]*[SIZE=2][COLOR=black][FONT=Cambria]a. [/FONT][/COLOR][COLOR=black][FONT=Cambria]ifconfig wlan0 up[/FONT][/COLOR][/SIZE]*[/FONT][LIST=1]
[*][FONT=Arial][COLOR=black][FONT=Cambria]*[SIZE=2]setup IP address[/SIZE]*[/FONT][/COLOR][/FONT]
[/LIST][FONT=Arial]*[SIZE=2][COLOR=black][FONT=Cambria]a. [/FONT][/COLOR][COLOR=black][FONT=Cambria]ifconfig wlan0 192.168.1.100[/FONT][/COLOR][/SIZE]*[/FONT]


[SIZE=2]Any help gratefully received.[/SIZE]
[SIZE=2]PS Haven't tried ndisgtk yet although I've got hold of the .deb files.[/SIZE]
[SIZE=2]PPS Not confident with Terminal so can you spell out any suggestions[/SIZE][/FONT]

---

### Post by Panawe on 2010-10-31
Have just obtained the following info...
 
```
$ lshw -C network

WARNING: you should run this program as super-user.


  *-network               

       description: Ethernet interface

       product: RTL8111/8168B PCI Express Gigabit Ethernet controller

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:06:00.0

       logical name: eth0

       version: 03

       serial: 1c:6f:65:46:4d:3d

       width: 64 bits

       clock: 33MHz

       capabilities: bus_master cap_list rom ethernet physical

       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes

       resources: irq:48 ioport:9e00(size=256) memory:fd8ff000-fd8fffff memory:fd8f8000-fd8fbfff memory:fd800000-fd81ffff

  *-network DISABLED

       description: Wireless interface

       physical id: 2

       logical name: wlan0

       serial: 24:3c:20:05:bb:ff

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=802.11b/g
```

[FONT=Times New Roman][SIZE=2]Problem seems to be that I can't see the hardware in "additional drivers"![/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]Cheers[/SIZE][/FONT]

---

### Post by Hippytaff on 2010-10-31
Do you need to mode-switch now, so the ubuntu knows its a usb dongle not a storage device.

[http://manpages.ubuntu.com/manpages/maverick/man1/usb_modeswitch.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/usb_modeswitch.1.html)

what does
```

lsusb

```
say

---

### Post by Panawe on 2010-10-31
Okay, this is where I need help...
 
What is the full command I need to type into Terminal?
 
Do I need to be in the same directory I installed the drivers from?
 
Thanks.

---

### Post by Hippytaff on 2010-10-31
Before you go to the length of mode-switchingm you can check if you need to do it by typing

```

lsusb

```
into the terminal, directory does'nt matter. It should come back with the usb device and some kind of description, ie wireless adapter or storage device. If it's the latter then you'll have to do the mode-switch thing, if not the problem lies elsewhere

---

### Post by uRock on 2010-10-31
Have you tried running **sudo apt-get install linux-firmware-nonfree**? This worked perfectly for getting my external wireless NIC to work.

---

### Post by Panawe on 2010-10-31
Here's the output...
 
```
$ lsusb

Bus 007 Device 003: ID 046d:c045 Logitech, Inc. Optical Mouse

Bus 007 Device 002: ID 1c4f:0002 SiGma Micro 

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 002: ID 059b:0032 Iomega Corp. Zip 250 (Ver 2)

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 001 Device 002: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
 
[SIZE=2]No, haven't tried apt-get yet. Don't I need to be on-line to use it?[/SIZE]
[SIZE=2]Thanks[/SIZE]

---

### Post by Hippytaff on 2010-10-31
Thats not the issue then, it's recognised as a WLAN thing.

If you can connect via ethernet you can do what Urock suggested.

Otherwise, right click the wirless icon on the top panel (looks like a radar thing) make sure everything is enabled. Left click it and check to see if your wireless network appears, if not lucj go to System > Preferences > Network Connections and set up the connection from there. Let me know how it goes

---

### Post by Panawe on 2010-10-31
There isn't a wireless icon on the top panel. Can't connect via LAN at the moment, using Windows 7 to access the 'Net.

---

### Post by Hippytaff on 2010-10-31
Try manually setting up the connection go to System > Preferences  > Network Connections, click the Wireless Tab, Click the Add button  and set up the connection from there

---

### Post by Panawe on 2010-10-31
Tried that so I now have an entry in the Wireless box in Network connections - but it just contains entered details of ID and PW relative to the router. I think the problem is Ubuntu isn't seeing the Dongle for some reason.
Thanks, I've put Downton Abbey on pause for this!

---

### Post by spiky001 on 2010-10-31
Have you tried adding notification area to panel to see if it puts icon back

---

### Post by Hippytaff on 2010-10-31
> **spiky001 said:**
> Have you tried adding notification area to panel to see if it puts icon back

Right click on the top panel, click add to panel and type notifcation and it should be the only option left and click add

---

### Post by Panawe on 2010-10-31
Yes, all there seems to be is the icon of two superimposed monitors with a cross - I think this indicates the non-existent LAN connection.
BTW how do I get the top panel back to how it was now I've messed about with it?

---

### Post by Hippytaff on 2010-10-31
Right-click it, it should say remove from panel

right - need to look into driver conflicts.

Also what does
```

rfkill list

```
return

---

### Post by spiky001 on 2010-10-31
Is a wired connection an option?

---

### Post by Hippytaff on 2010-10-31
> **spiky001 said:**
> Is a wired connection an option?
Nope :-(

do
```

lsmod | grep 8188

```

---

### Post by Panawe on 2010-10-31
Okay, I've got the usage wrong but...
 
```
$ sudo rfkill ls

[sudo] password for phil: 

Usage: rfkill [options] command

Options:

            --version          show version (0.4)

Commands:

            help

            event

            list [IDENTIFIER]

            block IDENTIFIER

            unblock IDENTIFIER

where IDENTIFIER is the index no. of an rfkill switch or one of:

            <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
```
 
[SIZE=2]Any help?[/SIZE]

---

### Post by Hippytaff on 2010-10-31
nope :-)

has to be

```

rfkill list

```should come back with something like this
```

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
...also the lsmod | grep... command earlier should come back with the driver is it is installed.

If the driver isn't installed, maybe try again. If it is (and rfkill is ok) it might be a driver conflict, but bridge cross come to it etc

---

### Post by Panawe on 2010-10-31
Both commands return nothing...
 
$ rfkill list

phil@panawe:~$ sudo rfkill list

[sudo] password for phil: 

phil@panawe:~$ lsmod | grep 8188

phil@panawe:~$ sudo lsmod | grep 8188
 
*[SIZE=2]:([/SIZE]*

---

### Post by Hippytaff on 2010-10-31
I just downloaded the driver from the second mirror here  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188SU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188SU)

There is quite a useful quick install guide (attached) file...might be worth having a good  look at that...I think the driver you tried to install may have been the  wrong one, this one is for this specific chipset as far as I can work  out, so this is the one you'll need.

---

### Post by Hippytaff on 2010-10-31
file:///home/hippytaff/Desktop/RTL8712(8188_8191_8192SU)_usb_quick_installation_guide.ppt

---

### Post by Panawe on 2010-10-31
It's a later file - ending ~00625 instead of ~00226. I'll try it and see what happens, I'm incredibly hacked off with this and wondering if it's not too late to go down the route of using "ndisgtk" and use the windows drivers!

---

### Post by Hippytaff on 2010-10-31
It's always best to use the linux ones of possible. if this driver doesn't work then look into ndiswrapper, but that can be head work as well...I think your more likely to have some luck with this one.

Let me know how it goes :-)

---

### Post by Panawe on 2010-10-31
Extracted th enew file ~00625 and went through the steps outlined at the start of this thread and this time Terminal hung at "*insmod 8712u.ko*"
 
Rebooted Ubuntu but no difference.

---

### Post by Panawe on 2010-11-01
Latest news...
 
[FONT=Times New Roman][SIZE=3]:~[SIZE=2]*$ iwconfig*[/SIZE][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*lo        no wireless extensions.*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT][FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*eth0      no wireless extensions.*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT][FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*wlan0     802.11b/g  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  *[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   *[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*          Retry min limit:7   RTS thr:off   Fragment thr:off*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*          Power Management:off*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*          Tx excessive retries:0  Invalid misc:0   Missed beacon:0*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[SIZE=2]So, Ubuntu not seeing dongle![/SIZE]
[SIZE=2]Need to get this sorted and any suggestions now welcome. Questions;[/SIZE]
[LIST=1]
[*][SIZE=2]Is there such a thing as a wired usb router? Will linux recognise it?[/SIZE]
[*][SIZE=2]If I tried reinstalling Ubuntu from CD is there a chance it would recognise the dongle. Bear in mind I have no LAN connection with this motherboard. I suppose I should return the faulty mobo to the vendor but with the cpu and heat sink attached I guess it would be a week or two before I get back to square one.[/SIZE]
[*][SIZE=2]Can I roll back Ubuntu? I think trying to install one version of the realtek driver overe the top of the earlier one has caused problems. Can I clear both installations out? Fairly easily?[/SIZE]
[/LIST][SIZE=2]I've been using Ubuntu (on my old machine) for a couple of years now and have enjoyed the experience and ther sense of community, despite the occasional bugginess (never got a decent CD burner working - have ended up buying Nero for linux, but that's a minor detail). This business has forced me back on to Windows, which is nice enough but, oh, the advertising and all the crap whenever you look for anything on the web![/SIZE]
[SIZE=2]I appreciate your help and don't mind spending a bit of money to help sort this problem out.[/SIZE]
[SIZE=2]Thanks again.[/SIZE]

---

### Post by Panawe on 2010-11-01
I've found on eBay a second-hand router that claims to use a wired usb connection
 
>>>[SIZE=3]_Netgear DG632_[/SIZE] 
 
 
What do you think?

---

### Post by Hippytaff on 2010-11-01
> 
[SIZE=2]Ubuntu not seeing dongle[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]can you post the output of[/SIZE]
[SIZE=2]```
[/SIZE]
[SIZE=2]lsusb[/SIZE]
[SIZE=2]
```[/SIZE]
[SIZE=2]with the usb dongle plugged in. It should appear. If is does Ubuntu can see it, it just needs to have the driver installed correctly.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Also. your probably better off following the instructions that came with the driver.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I'm not sure about that router, I've never tried one myself, but I know I had issues with a netgear wireless card, but thats something different.[/SIZE]

---

### Post by Panawe on 2010-11-01
Here it is...
 
_[FONT=Times New Roman][SIZE=2]*$ lsusb*[/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2]*Bus 007 Device 003: ID 046d:c045 Logitech, Inc. Optical Mouse*[/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2]*Bus 007 Device 002: ID 1c4f:0002 SiGma Micro *[/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2]*Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub*[/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2]*Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub*[/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2]*Bus 005 Device 002: ID 059b:0032 Iomega Corp. Zip 250 (Ver 2)*[/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2]*Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub*[/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2]*Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub*[/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2]*Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub*[/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2]*Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub*[/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2]*Bus 001 Device 002: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter*[/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]_
_[FONT=Times New Roman][SIZE=2]*Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub*[/SIZE][/FONT]_
[SIZE=2][/SIZE] 
[SIZE=2]I did follow the instructions but got some unexpected results! Will look back and post.[/SIZE]

---

### Post by Hippytaff on 2010-11-01
Ok, so it can be seen...post the unexpected results :-)

---

### Post by Panawe on 2010-11-01
Here it is...
 
[FONT=Times New Roman][SIZE=2]*[EMAIL="phil@panawe:~/Documents/Dongle/625/driver$"]phil@panawe:~/Documents/Dongle/625/driver$[/EMAIL] insmod 8712u.ko*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*insmod: error inserting '8712u.ko': -1 Operation not permitted*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*[EMAIL="phil@panawe:~/Documents/Dongle/625/driver$"]phil@panawe:~/Documents/Dongle/625/driver$[/EMAIL] sudo insmod 8712u.ko*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*phil@panawe:~/Documents/Dongle/625/driver$ ifconfig wlan0 up*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*SIOCSIFFLAGS: Permission denied*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*phil@panawe:~/Documents/Dongle/625/driver$ sudo ifconfig wlan0 up*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*SIOCSIFFLAGS: Resource temporarily unavailable*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*phil@panawe:~/Documents/Dongle/625/driver$ *[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]

 
Sorry about the line!
This is following the "script" which says something about disabling Network Manager! How do I do that?
Cheers.

---

### Post by Hippytaff on 2010-11-01
Apart from uninstalling and reinstalling Network manager, I know of no way to disable it. The only thing I can find about disabling Netwrok manager is this - [https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager).

Also
```

phil@panawe:~/Documents/Dongle/625/driver$ insmod 8712u.ko

```
you might need to do sudo before this?[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]

---

### Post by anewguy on 2010-11-01
Hippytaff, love the signature line about perserveance - reminds of the 70's - some programmer messed something up, but it was me in system support that always got the call first.  I'd go see what the real problem was and see users beating on their terminals.  So, we gave the foam rubber hammers and told them to use them instead of their hands.  Everyone got a big laugh out of it.

Dave ;)

---

### Post by klemes on 2010-11-01
> **Panawe said:**
> Here it is...
 
[FONT=Times New Roman][SIZE=2]*[EMAIL="phil@panawe:~/Documents/Dongle/625/driver$"]phil@panawe:~/Documents/Dongle/625/driver$[/EMAIL] insmod 8712u.ko*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*insmod: error inserting '8712u.ko': -1 Operation not permitted*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*[EMAIL="phil@panawe:~/Documents/Dongle/625/driver$"]phil@panawe:~/Documents/Dongle/625/driver$[/EMAIL] sudo insmod 8712u.ko*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*phil@panawe:~/Documents/Dongle/625/driver$ ifconfig wlan0 up*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*SIOCSIFFLAGS: Permission denied*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*phil@panawe:~/Documents/Dongle/625/driver$ sudo ifconfig wlan0 up*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*SIOCSIFFLAGS: Resource temporarily unavailable*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]*phil@panawe:~/Documents/Dongle/625/driver$ *[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]

 
Sorry about the line!
This is following the "script" which says something about disabling Network Manager! How do I do that?
Cheers.

Then you are all set dude!!!
All you need now for your dongle to work properly is install the [[COLOR="Red"] linux-firmware-nonfree[/COLOR]]("http://packages.ubuntu.com/maverick/all/linux-firmware-nonfree/download") package as uRock suggested and you are done!!!...hopefully....!!!!:popcorn:

---

### Post by Hippytaff on 2010-11-01
Thanks Anewguy, I've found it to be true so far, usually turns out to be me that's not working properly :-)

Klemes - I think that the problem is that there is no ethernet connection, so Panawe can't do what uRock suggested!?

---

### Post by anewguy on 2010-11-01
BTW - if the OP gets too frustrated with this, I can walk them through using ndiswrapper and the gui'd front-end ndisgtk.  Should be fairly simple, but would need to know if the OP has the Windows XP drivers and to match the ubuntu type - 32 or 64 bit as ndiswrapper doesn't work with Windows 7 drivers (unless something has drastically changed, it's always been only with XP drivers).

Either post here or send me a PM if you guys want to try the ndiswrapper route.

Glad to see you're hanging in there with the OP, and I'm glad the OP is willing to try what you ask - it makes things so much easier.  To the OP:  don't give up - believe it or not a LOT of us have been there with getting wireless working.  Some, like myslef, got extremely ticked for a while, but after getting it working it was all worth it!

Dave ;)

---

### Post by Hippytaff on 2010-11-01
I think panawe has the xp (or was it windows 7!?) drivers as far as I am aware...I think this was the last attempt before ndiswrapper, but I'm starting to think we'd both appreciate that Anewguy, :-)

---

### Post by Panawe on 2010-11-01
Thanks to all for your help, I appreciate it, but I've come to a decision - I'm going to send the mobo back to the vendor and get a new one with a working LAN connection.
As I say, thanks to all and I'll be back in Ubuntu before long, but for the time being I'll be off-line with no computer!
Cheers all.

---

### Post by Hippytaff on 2010-11-01
Always a good idea to have ethernet :-) sorry we didn't solve it

---

### Post by A-rap on 2011-02-01
I'm having EXACTLY the same problem with exactly the same dongle. When I hit
sudo ifconfig wlan0 up

I get the same result:
SIOCSIFFLAGS: Resource temporarily unavailable

First i got my dongle installed correctly and anything worked but after machine reboot never got wlan0 up again!

Gotta go back to the windows again :(:( So many times I've tried linux, but always got somewhere stuck :S

Can somebody tell me wtf is SIOCSIFFLAGS? what is their task? what layer of the computer they handle? etc....

---

### Post by Hippytaff on 2011-02-01
you may be better off starting a new thread :-)

---

