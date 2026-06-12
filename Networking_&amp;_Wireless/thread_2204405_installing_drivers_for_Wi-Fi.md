---
title: "installing drivers for Wi-Fi"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by dave williams on 2014-02-08
Hello 
This is the first time that I have posted a thread on the forum so in advance please be patient with me I am a complete beginner with ubuntu.
My question is I have a laptop which for whatever reasons I cannot connect to my broadband wirelessly however I have a good connection with a wired connection. Because it is a laptop I wish to move around my home and use this laptop in a different place where there is no hard wires.
my laptop is a Amilo fujitsu Siemens it has the latest flavour 12.4 ubuntu install. From provisional investigation I now it contains a Wi-Fi card within I also know that numerous people have had problems getting this card to work. I thought rather than get involved with trying to get this card to work I would invest in a Wi-Fi dongle but sadly I cannot seem to get this dongle to work. I have tried to download the drivers etc from the disc sent with the Wi-Fi dongle it is a USB wireless adapter v2.5 as of the moment that is as far as I have got the dongle flashes indicating it has been recognised but sadly I cannot connect to my broadband. Obviously it needs setting up properly to enable it to work could anyone out there give me instructions in on how to get this working I do hope somebody can help me thank you Dave

---

### Post by mörgæs on 2014-02-08
Which Amilo? 

For the wireless problem please begin with the commands in this htread:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by dave williams on 2014-02-08
> **mörgæs said:**
> Which Amilo? 

For the wireless problem please begin with the commands in this htread:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

hello
the laptop I am working on is amilo Li 1818 the Wi-Fi dongle is a ralink v2.5 wireless USB adapter

---

### Post by Vladlenin5000 on 2014-02-08
"ralink v2.5" doesn't tell us which Ralink chipset it has and knowing that is essential in order to give you useful advice.

(Edit: Additional info)

You can do ```
lsusb
```
This will list all your USB devices. One of the lines should contain "Ralink ...". Please post the whole line.

---

### Post by dave williams on 2014-02-08
hello
according to my information the  chipset is v 2.5 that is the information on the outside of the disc supplied with the dongle   thanks

---

### Post by Vladlenin5000 on 2014-02-08
v2.5 is the version of the drivers/software CD. Really not useful. Please read again my previous post (edited)

---

### Post by dave williams on 2014-02-09
hi this is the information from code
id 148f:5327 rilink corp amilo li1818 laptop that is all the information I have managed at the moment I will endeavour to post more information when it becomes available Dave

---

### Post by Vladlenin5000 on 2014-02-09
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/183293](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/183293)

---

### Post by dave williams on 2014-02-15
hi in order to progress this thread I am going to re post the question I have a Fujitsu Siemens amilo li 1818 laptop with a mini card d.802.11 wireless module S I S163 u internally installed. I also have ubuntu 12.4 installed in addition I have a wired connection to my broadband which appears to be working satisfactorily. Because it is a laptop I wish to use this computer in another area of the property wirelessly in order to make this work I need to establish a wireless connection.I have also bought a USB Wi-Fi adapter to plug in so my question is do I attempt to get the  internal card working or do I try to install the USB Wi-Fi adapter from my preliminary investigation it does not appear very easy. Because I am a raw beginner I'm finding this rather difficult  to post the output from the terminal I am aware that the output from the terminal would be immensely helpful to remedy my problem perhaps somebody could give me guidance on how to proceed.

---

### Post by mikewhatever on 2014-02-15
You've said above that the wired connection works, so why not copy/paste the output of **lsusb** and **lspci**?

The former should reveal info about the USB dongle, and the latter about the built in card.

---

### Post by dave williams on 2014-02-15
ok quite right the problem is I don't know how to post the output I have already included most of the information but I will attempt to do it again

---

### Post by dave williams on 2014-02-15
If you could tell me how to cut-and-paste the relevant information I will do so remember I am not very confident presumably there is a way of sending this information from the laptop if I am connected. my best regards

---

### Post by mikewhatever on 2014-02-15
Copy/pasting from a terminal window is no different then copy/pasting any text from anywhere else. Just use a mouse, select some text, copy and paste.
If it's still unclear, google for a howto.

---

### Post by dave williams on 2014-02-15
ok it's getting quite late here now I will attempt to copy and paste in the morning the relevant information with my best intentions Dave

---

### Post by Ptomerty on 2014-02-15
Follow the instructions in this post:
[http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)

---

### Post by varunendra on 2014-02-16
> **Ptomerty said:**
> Follow the instructions in this post:
[http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)

Yup.

Just to make it clear, it won't fix your wifi, only give us relevant info to help us troubleshooting your problem.

Try any of the three ways that suits you best - 1) Attach the report file that the script generates, or 2) copy-paste its contents here in your next post, or 3) copy-paste its contents at [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) and give us the url you get after submitting it.

If copy-pasting the contents here in your next post, make sure to use 'Code' tags to preserve its formatting. Please follow the "Using Code Tags" link in my signature below to see a quick HowTo with screenshots on using Code tags.

---

### Post by dave williams on 2014-02-16
```
davidno2@david-AMILO-Li-1818:~$ lsusb
Bus 001 Device 002: ID 0bf8:100f Fujitsu Siemens Computers miniCard D2301 802.11bg Wireless Module [SiS 163U]
Bus 004 Device 002: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
davidno2@david-AMILO-Li-1818:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
davidno2@david-AMILO-Li-1818:~$
```

---

### Post by dave williams on 2014-02-16
hello I'm good morning 
I hope the information which I have posted will be what you require. I'm sorry I did not realise you could copy and paste in the terminal I have never used the command line and as far as manipulating text etc it is completely foreign to me perhaps now we may progress this thread a little further assuring you of my best intentions Dave

---

### Post by dave williams on 2014-02-17
hello Has anybody any idea where I go from here I've posted the output from the terminal as you can see do you require any more information to troubleshoot this issue.assuring you of my best intention Dave

---

### Post by mikewhatever on 2014-02-17
Hi, the only wireless device in the output is this:
```
Bus 001 Device 002: ID 0bf8:100f Fujitsu Siemens Computers miniCard D2301 802.11bg Wireless Module [SiS 163U]
```

It looks like that's the problematic built in card, but the other one - ralink related doesn't seem to show. Was it connected when you posted the output?

---

### Post by dave williams on 2014-02-17
the USB Wi-Fi was not plugged in when I sent the output from the terminal what would you like me to do now Dave

---

### Post by dave williams on 2014-02-17
davidno2@david-AMILO-Li-1818:~$ lusub
lusub: command not found
davidno2@david-AMILO-Li-1818:~$ lsusb
Bus 001 Device 002: ID 0bf8:100f Fujitsu Siemens Computers miniCard D2301 802.11bg Wireless Module [SiS 163U]
Bus 001 Device 003: ID 148f:5372 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
davidno2@david-AMILO-Li-1818:~$ lspc1
No command 'lspc1' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
lspc1: command not found
davidno2@david-AMILO-Li-1818:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
davidno2@david-AMILO-Li-1818:~$

---

### Post by dave williams on 2014-02-17
ok please find the output from the terminal I believe this is what you have been looking for. I'm sorry to be such a pain don't know my way around  Ubuntu 12.4 but with your help I'm sure I will get there let me know if there is anything else you require with my best regards Dave

---

### Post by mikewhatever on 2014-02-17
Right, so now there is " Bus 001 Device 003: ID 148f:5372 Ralink Technology, Corp. ", and a bit of searching reveals it to be the
 [RT5372 chipset]("https://wiki.debian.org/rt2800usb"). That page also suggests the use of rt2800usb module, so, can you post the output of loding it:
```

sudo modprobe -v rt2800usb
```
Another page suggests the use of a different driver, so I am not sure.
[http://askubuntu.com/a/133913/20054](http://askubuntu.com/a/133913/20054)

---

### Post by dave williams on 2014-02-17
it's getting quite late now I will have a go in the morning am I right in assuming if I type the code in to the terminal it will give me the output which you require regards Dave thank you for your help

---

### Post by Vladlenin5000 on 2014-02-17
From experience, RT5372 based WiFi devices - BTW, the "2" in the model number indicates a 2T2R antennae architecture -> "N300" = 300Mbps maximum speed for both RC and TX - work out-of-the-box in Ubuntu since a few years ago, at least. Also - if I remember it correctly - the default driver was the same rt2800usb and besides being unstable only allowed up to 54Mbps ("g" only).
There are proprietary drivers here - [http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501) - that supposedly can be compiled. I remember doing it once and *IMPORTANT* after blacklisting the default driver it worked with the new driver but was even more unstable although apparently working as "n" device should.

Bottom line: I wouldn't recommend Ralink based dongles for Linux. I use Realtek 8191SU (RLT8191SU) instead and those work flawlessly in any Ubuntu version as far as I can remember, just by plugging it and waiting a few seconds only(note: It was probably in Ubuntu 11.04 I started using such dongles so not that long ago but still...)

---

### Post by varunendra on 2014-02-18
> **Vladlenin5000 said:**
> There are proprietary drivers here - [http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501) - that supposedly can be compiled.

IIRC, it can't be compiled on the latest kernels (3.11 and later). It needed a patch even on 3.8 kernel but that patch is no more helpful on the latest kernels.

@ Dave,
We can still use a detailed report as I suggested in post #16.

---

### Post by dave williams on 2014-02-18
Hi good morning it would seem even if I do get this Wi-Fi adapter to work it will not be very reliable?I will have a look and see what other devices are available preferably one which will work by simply plugging it in. In addition I will have a look and see if it is possible to fit a new card inside the laptop I am sure that there are some cards or USB devices which will work could any of you recommend which cards or adapters will work best. With regard to a full report I'm not sure I am competent to do that perhaps you could tell me exactly how to do that. May I take this opportunity to thank all of you who have responded to this requestyou probably will have guessed by now that I am slightly out of my depth but although 75 years young I am prepared to learn from others with greater knowledge than myself with my very best regards Dave keep up the good work

---

### Post by varunendra on 2014-02-18
> **dave williams said:**
> With regard to a full report I'm not sure I am competent to do that perhaps you could tell me exactly how to do that.

Please follow the suggested link. The linked post explains in very detail (yet short and easy) how to download and how to run the script. Then how to post the report it generates.

It is the same link as the "Wireless Script" link in my signature below. :)

---

### Post by dave williams on 2014-02-18
davidno2@david-AMILO-Li-1818:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2014-02-18 12:21:27--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 107.20.138.135
Connecting to dl.dropbox.com (dl.dropbox.com)|107.20.138.135|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2014-02-18 12:21:28--  [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 50.17.227.107
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|50.17.227.107|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4165 (4.1K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 4,165       --.-K/s   in 0.004s  

Last-modified header missing -- time-stamps turned off.
2014-02-18 12:21:28 (1.04 MB/s) - `wireless_script' saved [4165/4165]

[sudo] password for davidno2:

---

### Post by dave williams on 2014-02-18
I hope the above will suit your requirements not sure but here goes all the best Dave

---

### Post by varunendra on 2014-02-18
> **dave williams said:**
> [sudo] password for davidno2:

When it asked for your password, did you provide it? It is the same password that you use to log in.
While typing the password, you won't see anything on the screen, it is a security feature. Just type in the password correctly and press 'Enter'.

If you already did that, the script would have created a file named "**wireless-info.txt**" or "**wireless-info.tar.gz**" in you Home directory.
(it would have created that file anyway, but if you didn't supply your password, some information would be incomplete).

Either attach this file, or copy-paste its contents in your next post. That is the information we need to analyze.

---

### Post by dave williams on 2014-02-18
have I managed to do it right this time I hope so

---

### Post by dave williams on 2014-02-18
*************** info trace ***************

***** uname -a *****

Linux david-AMILO-Li-1818 3.5.0-45-generic #68~precise1-Ubuntu SMP Wed Dec 4 16:19:28 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

06:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Fujitsu Technology Solutions Device [1734:10c7]
    Kernel driver in use: 8139too

***** lsusb *****

Bus 001 Device 002: ID 0bf8:100f Fujitsu Siemens Computers miniCard D2301 802.11bg Wireless Module [SiS 163U]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** iw reg get *****


***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:03:0D:6E:EB:4F

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.69
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

---

### Post by varunendra on 2014-02-18
> **dave williams said:**
> Bus 001 Device 002: ID **[COLOR="#FF0000"]0bf8:100f[/COLOR]** Fujitsu Siemens Computers miniCard D2301 802.11bg Wireless Module [SiS 163U]

The above is your wireless adapter, on a USB bus. Unfortunately, it seems that no Linux driver exists for it. Our only hope is windows driver with a 'compatibility program' called "ndiswrapper".

If you wish to try that, take a look at comment number #3 on this page : [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/203443](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/203443)

Can you follow those instructions?

I may try to simplify those same instructions and break them in easy-to-follow steps, but be aware that it may take some tinkering/experimenting.

---

### Post by dave williams on 2014-02-18
Thank you for your comments it would seem that this card causes some issues I probably will not proceed down that road I will try and install the USB Wi-Fi adapter that seems like a less complicated route. Any help with that would be appreciated?

---

### Post by varunendra on 2014-02-18
> **dave williams said:**
> I will try and install the USB Wi-Fi adapter that seems like a less complicated route.
Indeed, as long as the adapter you purchase is natively supported.

ThinkPenguin maybe a good choice to purchase the new adapter from. They provide models that are natively supported on Linux, and if a problem is found, it seems they are also good at replacing the purchased model with another working one.

I personally have no experience with USB adapters, but this page should be able to help you in making a choice : [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Read the initial recommendations to get a rough idea, then scroll down to the "**[By Manufacturer]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By_Manufacturer")**" table, and click on the "USB" links against various vendors.
Those links would lead you to related vendor's "User Feedback" table, where you can see users' experience with various models.

Make a list of the models that seem to be good, then, just to be extra sure, search the forums with their names as keywords to see there are no known problems with them (or are easily fixable if there are).

Shortlist the models that either work out-of-box, or can be easily fixed.

Time taking process, but will assure a trouble-free experience. :)

---

### Post by dave williams on 2014-02-19
Sounds like a good plan to me I will investigate which USB Wi-Fi adapter? we can all be wise after the event and perhaps I should have asked for advice before doing anything. However we now have a plan and I will advise as and when I have purchased a USB adapter which will work out of the box with a bit of luck we will establish a wireless connection? my wired connection seems solid I have received a couple of suggestions  _**is there anybody out there who have bought a USB Wi-Fi adapter recently which works out-of-the-box**_ this may save me a great deal of searching assuring you of my best intentions Dave  PS once again thanks to everybody who have tried to help


I have a couple of names already realtek and Penguin at least that is a start. Have a nice day

---

### Post by dave williams on 2014-02-20
It would seem from my investigations that a penguin Wi-Fi adapter is the most favoured adapter? With this in mind has anybody out there purchased one recently I would be pleased to hear how it is performing and price etc. They are available from USA at a price of around £13 if there is anybody out there please contact or reply to this thread very many thanks to everybody for your help. Dave

I can't find anybody in the UK the supplies them

---

### Post by dave williams on 2014-02-20
Had a look around the local PC world  store today sadly they do not have anything compatible This is probably my last throw of the dice I cant believe that somebody has not tried one of these devices out there. If anybody has used a**_ penguin Wi-Fi adapter _**recently in the UK or USA could they please indicate whether it was a success or not I would very much appreciate feedback thank you all have a nice day

---

### Post by varunendra on 2014-02-21
Like I mentioned before, I don't have any personal experience with USB wifi adapters, but a search for keyword "ThinkPenguin" through the "Networking & Wireless" section of the forums turned these up which may help a bit :

[COLOR="#800000"][**IMPORTANT:** Please note that the same model may come with different chips at different times/places. The performance is dependent on the chip inside, not on the brand or model number of the adapter package][/COLOR]
[http://ubuntuforums.org/showthread.php?t=2203759&p=12927630#post12927630](http://ubuntuforums.org/showthread.php?t=2203759&p=12927630#post12927630) (a post showing the response of ThinkPenguin when an adapter was found to be _possibly_ defective)

[http://ubuntuforums.org/showthread.php?t=2175958&p=12795834#post12795834](http://ubuntuforums.org/showthread.php?t=2175958&p=12795834#post12795834) (a few random suggestions with the poster having first hand experience with them)

[http://ubuntuforums.org/showthread.php?t=2161060&p=12723977#post12723977](http://ubuntuforums.org/showthread.php?t=2161060&p=12723977#post12723977) (post suggesting that models with Atheros AR9281 chip work nicely, but lacks feedback about what was the problem and if it ever got solved when it apparently broke after sometime)

[http://ubuntuforums.org/showthread.php?t=2134360](http://ubuntuforums.org/showthread.php?t=2134360) (some interesting suggestions and feedback, make sure to read all the posts in the thread)

[http://ubuntuforums.org/showthread.php?t=2123088](http://ubuntuforums.org/showthread.php?t=2123088) (another interesting thread, worth reading all the posts in it)

I'm sure there must be hundreds of users for whom their USB dongles worked out-of-box and have continued to work so. The problem is that people only come to forums when they have a problem. Those who have no problems with their hardware have no reason to come here and post their feedbacks. Although a few do care to help us with their precious feedbacks, but such posts are extremely rare to find.

---

