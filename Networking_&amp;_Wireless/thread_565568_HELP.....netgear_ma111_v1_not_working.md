---
title: "HELP.....netgear ma111 v1 not working"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by 1Xtreeme on 2007-10-02
If I go to network manual config on desktop enviroment it shows WLAN0 and lan0. If I use lsusb it even shows the usb stick (netgear MA111 v1). V1 is the prism2 chip. Its my understanding thus far that v1 is supported by the prism2 drivers its the v2 that is not since it has a diff chip.

If I type iwconfig it says no extensions listed. IE the device is not found?????

I was told ubuntu supported this wifi adaptor out of the box by many people however installing ubuntu on 3 diff boxes all had same effect, exactly the same results on each one. Im not running live cd, its installed on hard drive (initially I though this was the problem).

I only want this pc to do one thing. Be a WAP and router. Thats it. No I dont want a standalone router, dont ask! Had a few and Im tired of their limited firmware and hardware/heat issues. I want a linux pc router and WAP. Thats all. LOL. Can anyone give me advice. Ive read so many guides in past 3 days Im just seeing double now and reading the same old stuff that doesnt help. Crazy, I can do animation, flash cs3, Illustrator cs3, php code, mysql you name it. But alas installing a wifi that is claimed to be supported in this linux distro has me stumped. HELP before I just flat out give up on linux and leave my entire network hardwired.:(

---

### Post by greenstar on 2007-10-02
Have you actually ever seen this card work? It could be DOA. I know I've had more than my share of DOA computer hardware. Check it with a few live CDs. I'd suggest Knoppix, PCLinuxOS, or Puppy Linux as all 3 have great hardware support on the Live CD. If you have access to a PC with the leading commercial OS, you might test it there also.

Greenstar

---

### Post by Lambert on 2007-10-02
Somebody else might need to jump in here who uses a device with this chipset.

What version of ubuntu did you install?
check to see if linux-wlan-ng is installed


```

dpkg -s linux-wlan-ng

```

If it's not installed, this is the driver needed for that chipset.(I believe). With no interface shown with iwconfig, I'm under the opinion there is no driver currently installed or working for that device.

---

### Post by 1Xtreeme on 2007-10-02
greenstar- yep Im certain it works. The win XP box fires it right up and away it goes. I just used it yesterday. However XP doesnt offer WAP or routing I want. Well Softap did but vanished a while back. The xp drivers dont offer master mode? that is needed for WAP. Softap used hacked drivers. THe linux drivers offer it also.


So...onto linux I go heh.:)




Lambert- 

"What version of ubuntu did you install?"

ubuntu-7.04-desktop-i386.iso           I think its called "fiesty?"  

"check to see if linux-wlan-ng is installed"
will do, Ill post back that info here in a few.


Thanks for the help guys!:guitar:

---

### Post by 1Xtreeme on 2007-10-02
I ran that command and it says not installed. Here is what I have 

lsusb
Bus 001 Device 002: ID 0846:4110 NetGear, Inc. MA111 WiFi (v1)
Bus 001 Device 001: ID 0000:0000  

If I go to system>admin>package manager and search hostap (for modules)
IT shows these installed (green box beside them)

Hostapd  1:0.5.5-3.1                             WPA authenticator
Hostap-source  1:0.4.1-1                     Host ap driver for intersil Prism2/2.5/3
Hostap-utils       1:0.4.0-1                     Utility programs for hostap driver for intersil prism2/2.5/3
kismet                 2006.04.R1-1.1         wireless 802.11b monitoring tool

Isnt that the right driver? Im confused (obviously LOL)

whats odd is that if I click the network icon in task bar, then manual config it shows the Wlan0 and my ethernet, both with IP I set static (diff IP's of course). Does that mean the driver is working or simply that linux sees the hardware but isnt talking correctly to it?


thanks again:)

---

### Post by Lambert on 2007-10-02
> **1Xtreeme said:**
> 

Isnt that the right driver? Im confused (obviously LOL)

whats odd is that if I click the network icon in task bar, then manual config it shows the Wlan0 and my ethernet, both with IP I set static (diff IP's of course). Does that mean the driver is working or simply that linux sees the hardware but isnt talking correctly to it?


thanks again:)

I haven't been around in a while but last I remember was hostap doesn't support usb devices. Not sure if driver has been updated to support usb now. linux-wlan-ng does though.

---

### Post by 1Xtreeme on 2007-10-02
OK that makes sense. Well Im trying the other driver.

Following this guide [ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/README](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/README)

all goes well till this step

- Linux source directory [/usr/src/linux]: 
        The config script will attempt to automagically find your kernel
        source directory.  If found, the kernel source source directory
        will be presented as the default selection.  If the default
        selection is wrong, you may correct it here.
it came up with
```
Linux source directory [/lib/modules/2.6.20-16-generic/build]:
```

I just hit enter and well, it must have found wrong path??? Not sure what to put here. Its a default ubuntu install (if that helps?) After I hit enter it spit this out which doesnt look good heh.

```
get_version.c:7:19: error: stdio.h: No such file or directory
get_version.c: In function ‘main’:
get_version.c:10: warning: incompatible implicit declaration of built-in function ‘printf’
make[1]: *** [get_version] Error 1
./Configure: line 246: scripts/make.opts: No such file or directory

The kernel source tree is version .
WARNING: the current running kernel is actually version 2.6.20-16-generic.
The current kernel build date is Sun Sep 23 19:50:39 2007.
./Configure: line 311: [: too many arguments

./Configure: line 349: scripts/make.opts: No such file or directory
Alternate target install root directory on host []: 

```

so close but so far away.

---

### Post by Lambert on 2007-10-02
Ok, those instructions are to compile and build from scratch. Not necessary as it's already in the ubuntu repositories.

Open up synaptic package manager and do a search for linux-wlan and install from there.

You do need inernet access as I don't see this on the install disk.

If you don't have internet access then you need to download the package from packages.ubuntu.com copy over to ubuntu and install with dpkg.

---

### Post by 1Xtreeme on 2007-10-03
Thank you, thank you, thank you!:guitar: Its working now. I installed all 3 results in package manager that came up for wlan-ng.Now when I type iwconfig it shows wlan0 stats. Woho. I guess it shows how long ago it was I messed with linux. Before I remember having to compile all the drivers. This is great in comparison so much easier to just get the thing to work, and get on with it! Ubuntu has opened my eyes. heh.

OK now its working and recognised. How do I go about WAP on ubuntu. Knowing my luck Ill pick the hard way and get stuck. Any advice on setting it to master mode?

Id like it to use 192.168.0.1 for the IP with normal subnet mask. We have a wii here also and the instructions say it seems to prefer a Access point with that ip.

So basically all I need is ubuntu instructions on this (not general linux ones like I been finding)):P

---

### Post by greenstar on 2007-10-04
You mention enabling WAP in Ubuntu, however wireless encryption uses a form of either WEP (old), WPA(recent), WPA2(newest). There are several variants for each protocol, ie. WPA-PSK, etc.

If you want WEP, it's built into feisty. If you want WPA, you'll need to install wpasupplicant:
```
sudo aptitude install wpasupplicant
```

Greenstar

---

### Post by 1Xtreeme on 2007-10-04
Nobody knows how to setup WAP in ubuntu 7????????????? WoW.:confused:

---

### Post by 1Xtreeme on 2007-10-04
> **greenstar said:**
> You mention enabling WAP in Ubuntu, however wireless encryption uses a form of either WEP (old), WPA(recent), WPA2(newest). There are several variants for each protocol, ie. WPA-PSK, etc.

If you want WEP, it's built into feisty. If you want WPA, you'll need to install wpasupplicant:
```
sudo aptitude install wpasupplicant
```

Greenstar

Actually encryption not needed right now, I live in a remote area with no wifi in range, even the closes road is too far away to pickup my wifi. Im just trying to get it working first. I want a WAP. Wireless Access Point. Not WPA. heh. 

reason is- After having 3 wifi boxes Im tired of them. First was WRT54g which finally died. It needs reset twice a day the wifi overheats and locks up, rest of router is fine. Bad thing is it was the best wifi I ever had. Replaced with netgear, that piece of junk lasted 2 days-overheats and shuts off ($30 what do you expect). They wanted $20 shipping to fix it, what a load. So I got a 3rd one. New Linksys, and well-not impressed with it either Vista OS refuses to get net over it, new IP protocall incompat with the firmware. Linksys wont even reply to support mail. Its a well documented issue, just linksys dont care after they got your $60 (way to go). so sold it, it only half works now and got rid of it before it dies like rest LOL! So I need a Software Wireless Access Point to replace these horrible things till wifi gets off the ground (more then just work, but is dependable). It will be years before I purchase another wifi router box.:(

---

### Post by Lambert on 2007-10-04
> **1Xtreeme said:**
> Nobody knows how to setup WAP in ubuntu 7????????????? WoW.:confused:

I've never done it can't offer much accept links to articles for linux in general.

[http://www.linux.com/articles/55617](http://www.linux.com/articles/55617)
[http://www.ibm.com/developerworks/linux/library/l-wap.html](http://www.ibm.com/developerworks/linux/library/l-wap.html)


The right person might not have seen this yet. Consider starting a new thread with different title.

---

### Post by 1Xtreeme on 2007-10-04
That first link mentions Ubuntu and looks promising. Ill give that one a go. If I can tfigure it out Ill take your advice and start a new thread. THanks again for the help.:)

---

### Post by britrb on 2007-10-09
Ok, I have the same wireless adaptor (MA111 v1) and am going to load Feisty onto my old lappy with a view to using wireless. Could someone please givea complete set of instructions as to "How to get it to work" in one easy to read (with pictures for noobs) post. I am a complete Linux NOOB, and want to learn, but we all start from basics so I aplogise for my inexperience with Linux.

Thanks all, Brian :)

Lappy specs:
CPU: AMD Athlon XP-M 2400+ @ 1800mhz.
RAM: 256mb DDR.
HDD: 5200rpm 20gb.
GPU: 64mb VIA (?thingy?)

(Also if anyone can tell me if Feisty will run on here that would be great too. Thanks guys :) )

---

### Post by gali98 on 2007-10-09
Okay after several hours of messing around, I finally also got something in iwconfig or whatever, but did you actually get on the internet with it, because I'm still having no luck with it.

---

### Post by gali98 on 2007-10-09
okay scratch that. I just rebooted and it works. This is so sweet. All this time (several months) i've been having to download and carry junk. AUUGHHHHH I'm seriously shaking. wow..... okay let's see if I can help others. Not all this is needed, but I don't know what it was that actually did it. I installed the linux-wlan-ng. Next follow this tutorial.
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111")
I know it's old, but it worked. All I really did was paste the 
"wireless_mode managed
     wireless_essid your_essid"
part on the bottom of /etc/network/interfaces because we have no encryption.
I also installed ndiswrapper. I installed the ma111.inf file from the driver download.
Then I did:
ndiswrapper -m
ndiswrapper -ma
ndiswrapper -mi

That's it. I rebooted and it worked. Hope it works for you too!
Kory

---

### Post by tormod on 2007-10-17
If you follow the link from that tutorial to [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb) most of your answers will be answered.

---

### Post by gali98 on 2007-10-18
Thanks for the link. So I figured out that to use the link all you have to do is install linux-wlan-ng.
That was it. And I think you had to put those two lines I showed above like the tutorial said. It helps to have a wifi assistant such as "wireless assistant" because it does not automatically detect networks when you plug it in. Just load the program up and connect. That's pretty easy right? Okay now for a question...
I am compiling my own kernel and the prism2 module does not come in the source.  I looked in the config file of the generic kernel that came with ubuntu and the module is listed under "ubuntu wireless drivers"
So I guess what I'm asking is how the monkey do I get the prism2 module working with my own kernel? Thanks for any help...
Kory

---

### Post by tormod on 2007-10-18
You don't need those two lines if you use NetworkManager. You can also set them using the Network Admin GUI instead of manual edits.

If you use a non-Ubuntu kernel you can install the linux-wlan-ng-source package and run:
```
sudo module-assistant build linux-wlan-ng
```
It will produce a kernel-specific package with the prism2 modules, which you then simply install with dpkg -i.

---

