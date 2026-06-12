---
title: "(WORKS!) Complete How-To for WPN111"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by iWill on 2007-04-19
This is the complete how to that worked for me (im on Feisty btw)
1)Install newest ndiswrapper + build-essential
2)Get the 3 files in the file I attached and drag them to the desktop
3)now install the drivers with ndiswrapper:
```
sudo ndiswrapper -i /home/<username>/Desktop/netwpn111.inf
```
4)Copy and paste this:
```
sudo ndiswrapper load_fw_ar5523 /etc/ndiswrapper/netwpn111/ar5523.bin
```
5)By now the blue light on the netgear usb should light. Now we need to make sure itll work even when we restart:
```
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```
 Add the module to /etc/modules:
```
sudo gedit /etc/modules
```
Copy and paste the following to the bottom of the file. Save it. Close it:
```
ndiswrapper
```

Voila!!!Hope this works for you guys...works great for me :)

---

### Post by FRuMMaGe on 2007-04-19
It's wierd how different this is to the WPN311

I got mine today and it works out-of-the-box, no drivers needed.

After inserting it into the PCI slot, it took me 5 minutes to get connected to the internet :)

---

### Post by sionghua on 2007-04-20
USB wifi will have more problems then others.

---

### Post by Milner_07 on 2007-04-23
That works great! 

Thanks SO much!

TM

---

### Post by capaci on 2007-04-26
the "load_fw_ar5523" step doesn't work for me. any suggestions? i installed the newest ndiswrapper and build-essentials. every other step seems to work, but i've read that this "load_fw_ar5523" step is the most important. i just get the ndiswrapper usage when i do that command line. i've seen some command lines where it's just the "load_fw_ar5523" as the actual command (not ndiswrapper like you have it), but then i get command not found. i need this to work. any help is appreciated. thanks a lot.

---

### Post by capaci on 2007-04-26
so i found out that the ndiswrapper package doesn't even have this "load_fw_ar5523" file with it anymore. the package seems to have dropped it a while ago. i can't build it with the older sources either. is there any way to get this binary so i can load this driver? i really need this to work.

can the original poster of this thread please tell me what version of ndiswrapper you are using? thanks.

---

### Post by iWill on 2007-04-29
> **capaci said:**
> so i found out that the ndiswrapper package doesn't even have this "load_fw_ar5523" file with it anymore. the package seems to have dropped it a while ago. i can't build it with the older sources either. is there any way to get this binary so i can load this driver? i really need this to work.

can the original poster of this thread please tell me what version of ndiswrapper you are using? thanks.

Answered your private message...good luck hope it works i know how fustrating it is to not have this thing work...
For all you other guys i installed ndiswrapper of this website:
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

Good luck to all

---

### Post by iWill on 2007-04-29
> **capaci said:**
> the "load_fw_ar5523" step doesn't work for me. any suggestions? i installed the newest ndiswrapper and build-essentials. every other step seems to work, but i've read that this "load_fw_ar5523" step is the most important. i just get the ndiswrapper usage when i do that command line. i've seen some command lines where it's just the "load_fw_ar5523" as the actual command (not ndiswrapper like you have it), but then i get command not found. i need this to work. any help is appreciated. thanks a lot.

Describe what happens once you type in the "load_fw_ar5523" step

---

### Post by McDusty on 2007-04-29
Hello everyone,

My first post ... I was expecting it to be about me begging for help on this ... but instead I might be able to help. Im posting this from Ubuntu via wpn111. PS. also my first try of linux, so im quite chuffed with myself!

Capaci ... i was having the same problem as you and had to keeping rebooting into windows and back to search for help / files needed.

Basically I had the ndiswrapper-1.42 installed. However this does not come with the load_fw_ar5523. You need to install ndiswrapper-1.6 ... you can find all the versions here ...

[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148)
release notes for 1.6 here ...
[http://sourceforge.net/project/shownotes.php?release_id=374651](http://sourceforge.net/project/shownotes.php?release_id=374651)

However, i tried to install this and the load_fw_ar5523 wouldn't compile because it needed the libusb library's installed, which you can get from here ...

[http://libusb.sourceforge.net/download.html](http://libusb.sourceforge.net/download.html)

Each package has an install/readme txt file which will tell you what to do.

I can't remember command by command what I typed, but hopefully this helps.

Regards
Ash

---

### Post by McDusty on 2007-04-29
damn!

A ubuntu update killed it. I should have paid more attention to what it was updating and told it to leave the ndiswrapper well alone.

but since the update it doesnt work and on boot there is an error on the command line about the ndiswrapper verions 1.6 not matching the driver version 0.

tried uninstalling all ndiswrapper stuff and starting again, but still no joy :(

Nightmare eh

---

### Post by mshen10 on 2007-04-30
i get this when i list my drivers in ndiswrapper

ar5523.bin : invalid driver!
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
netwpn111 : invalid driver!

some help would be great.

---

### Post by McDusty on 2007-05-01
Very strange ... 

Id given up trying to fix this despite my efforts a couple of days back (with the intention of trying another day) since it wasn't working.

Today however I start my comp, with the intention of going into windows, but forget to change grub, so i end up in Ubuntu and notice my WPN111 is flashing ... and indeed here I am ... its working. But no doubt when i next start my comp into Ubuntu it won't work ... seems very erratic/strange.

Anyway ... mshen10 ... are you sure 14E4:431 is a WPN111 ... the code for mine is 1385:5f01 and im sure other people on this board have stated that is their code too.

how many steps from the first post of this thread have you followed? and what happened??

---

### Post by UltimoHedgehog on 2007-05-01
Step 4 doesn't seem to be working. It's the same effect as typing in ndiswrapper in the console. Also, where can I find the dependencies for the build-essential for Fiesty? I'm a brand new Linux user, so I have no clue where to start on this.

---

### Post by McDusty on 2007-05-02
Yo,

You have to type ...

sudo load_fw_ar5523 /etc/ndiswrapper/netwpn111/ar5523.bin

but you may need to get the ndiswrapper 1.6 to get the load_fw_ar5523, which in turn requires the libusb libraries . See my first post in this thread. The build-essential stuff should be on your fiesty CD. Just whack it in, load up the synaptic package manager, make sure the cd is added and it should be there.

---

### Post by opes on 2007-05-07
I've been working on this issue the past few days, and was getting the same error.

I tried the version from apt-get, was experiencing the issue.  (7.04)
Now, I removed ndiswrapper, and went and d/l'ed the tar for the newest version of ndiswrapper. (1.43)
Because 1.42 was the one pulled by apt-get and does not have the load_fw_ar5523 file.

ndiswrapper version 1.43 makes the load_fw_ar5523 file obsolute.

I made headway yesterday with compliing version 1.43.

I got it to recognize wpn111, now I just have to configure it.

It can be done, stick with it.

---

### Post by Petergeek on 2007-05-11
I have got the WPN111 working.  :lolflag: 

If you look at the notes against ndiswrapper version 1.7, it explains why you don't need load_fw_ar5523 any more.

All I did was this:
[LIST=1]
[*]Copy the all the files that are not in any folders from the WPN111 installation disk to the desktop (There are 13 of them and I don't know which ones you need)
[*]Now you install **_TWO_** drivers
[/LIST]
sudo ndiswrapper -i /home/<username>/Desktop/netwpn111.inf
sudo ndiswrapper -i /home/<username>/Desktop/athwpn.inf

You then re-boot, the blue light comes on and once you have gone through System/Admin/Network to set up your network ESSID & encryption, the job's done.

---

### Post by charliemcf on 2007-05-27
i only have 7 files not in folders on my cd. (and not athwpn.inf)

i get

```
* : driver installed
        device (1385:5F01) present
netwg11t : driver installed
netwpn11 : driver installed
        device (1385:5F01) present

```

could someone please attach the two .inf's needed?

thank you, charlie

//new feisty user//

---

### Post by charliemcf on 2007-05-27
some more info:
Dell E521
2gig ram
Ati X1300 pro
Wpn111 
```

charlie@dell:~$ sudo iwconfig wlan0 essid NETGEAR-Advent mode managed key [MY WEP KEY REMOVED FOR SECURITY REASONS :)]  restricted
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.


charlie@dell:~$ sudo ndiswrapper -l
* : driver installed
        device (1385:5F01) present
netwg111 : driver installed
netwg11t : driver installed
netwpn11 : driver installed
        device (1385:5F01) present


charlie@dell:~$ sudo ifup wlan0
wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```

i have changes the "/etc/network/interfaces" to correct and "/etc/modules"



please help as i am new
//charlie//




**i have feisty

---

### Post by charliemcf on 2007-05-28
bump coz i really need this for my work.

i have ndiswrapper installed, and im now using the drivers direct from

"C:\Windows\System32\DriverStore\"

---

### Post by Petergeek on 2007-06-02
Here I the files from the installation disk that I used.

---

### Post by miesnerd on 2007-06-03
ok, so im having some probs here
when running sudo ndiswrapper -l I see:
athwpn: invalid driver
netwpn111: driver installed
device (1385: 5F01) present

and that's all. My WPN has the blue light flashing. What am I missing?
btw-- i have to copy everything from a flash drive, so if you could make it as little "apt-get" as possible, I'd appreciate it.
Miesnerd

---

### Post by miesnerd on 2007-06-03
update: i now have two valid drivers, but the light is still flashing. Any help? Thnx. To be more specific, the athwpn is saying "driver installed" but that's the only change.

---

### Post by mars01 on 2007-06-06
I bet there's some people left out there that has just installed Ubuntu feisty and realized that their Windows-WPN111 doesn't have any linux drivers. If you know why it doesn't have any linux drivers, please reply.
 
Could someone more linux-experienced help me out here, cause I don't know what to do anymore. I'm currently running Ubuntu 7.04 with the  2.6.20-16-generic kernel.
I will consider myself as a newbie as long as I haven't got my WPN111 working.
I've tried to get this usb stick working for too long already. I've got this wlan working buggy on dapper when that release came out, but back then it had some freeze problems when plugging it in so I didn't bother. Now when feisty came out I thought I would give it a try on a clean system.

Now to the problems. First I connected the usb stick to a Windows-computer and that worked without problems and the blue LED was flashy.

I then built ndiswrapper from source with the WIfi docs howto and installed new headers, dependencies etc. 

```

sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install dh-make fakeroot gcc-3.4 build-essential  

```

Then I downloaded the current version of ndiswrapper-1.46 from sourceforge.

```

tar xvfz ndiswrapper-1.46.tar.gz 
cd ndiswrapper-1.46

```  

Then I built the package without errors.

```

sudo make
sudo make install

```

The drivers from this thread I downloaded with firefox to the desktop.
I loaded the two drivers athwpn.inf and netwpn111.inf with their .sys and .bin files respectively in the ~/Desktop/drivername.inf  folder. 

```

sudo ndiswrapper -i ~/Desktop/.inf

```
 

[I]ndiswrapper -l gives me this result....
[/I]
athwpn : driver installed
        device (1385:5F01) present
netwpn111 : driver installed
        device (1385:5F01) present

[I]... and ndiswrapper -v gives me this. 
[/I]

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.46
vermagic:       2.6.20-16-generic SMP mod_unload 586 

utils-version and the one needed are at least the same as they should according to the ndiswrapper site.

I then loaded the driver module with

```

sudo depmod -a
sudo modprobe ndiswrapper

```

--------------------------------------------
When I first loaded the netwpn111.inf driver (but not the athwpn.inf) the usb-stick was flashy.
But after a reboot it haven't flashed blue again on ubuntu. I've tried it again on Windows and that worked so there's nothing wrong with the WPN111.
Is the ar5523.bin file needed and in that case which versions etc are needed to load it.
There seem to be some way "load_fw_something-I-don't-remember" not working with the bash....?
Should I use older versions of the ndiswrapper or is the latest the ones the best?
Could someone please respond to this thread and clear things out cause everyone that has succeded seems to have "fulhaxat" as we say in Sweden which means approximately "messed things up to work". 
I really need this WPN111-LED to flash. 

/Thanks in advance to the ubuntu community :popcorn:

---

### Post by wrtrdood on 2007-06-12
Another possibility in case others have had trouble with this:

I pulled the latest ndiswrapper (1.46) from the sourceforge page:
[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148")

Build requirements have been stated.  The INSTALL file describes the steps but here's the simple process I used:

sudo make uninstall
make
sudo make install
sudo ndiswrapper -i netwpn11.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo gedit /etc/modules (add ndiswrapper)


This version of ndiswrapper will install everything needed if it is all located in the same directory.    Make sure netwpn11.inf, ar5523.bin, and athwpn.sys are in this directory. 

After the **modprobe** command the blue light should start flashing.  Verify the adapter is active with iwconfig and ifconfig should show the wlan device.  

Configure the device using the NetworkManager by selecting the correct wireless network and you should be in business.

---

### Post by midlifecrisis on 2007-07-06
Hi,

I seem to have got the wpn111 working, it's getting an ip address. But, i'm unable to see my network or the internet. 

Does anybody know what I'm missing?

Cheers

david

---

### Post by midlifecrisis on 2007-07-06
I've been digging around a bit and found that i need to disable the wire connection in order for the   wireless card to connect. Can this be changed? if so how would i do it?

---

### Post by tprzepiorka on 2007-07-17
I have been trying to get this working for a while. I get errors when I try to install ndiswrapper 1.6, so the original post is out of the question. Then when i try to load the drivers with 1.47 i get errors at it lists both athwpn and netwpn11 as invalid drivers. I don't know what to do from here. 

Any ideas?

---

### Post by lindau on 2007-07-24
I can get wpn111 to work OK, but as soon as I make the network connection my mouse freezes, any Idea.
:confused:

---

### Post by specialdave on 2007-09-16
Hey everyone.

I am a new linux user and have a couple of problems with the WPN111.

Firstly I installed Ubuntu 7.10 Tribe 5 to see what it was like. Using this guide I was able to get it working, however, the WPN111 stopped working after a reboot.

I then decided to install Ubuntu 7.04. This is the version of Ubuntu i would like to use untill the official release of Gusty, but for some reason my pc freezes after the "sudo modprobe ndiswrapper".

I type it in.... then nothing. cant type cant move my mouse cant do anything. Its strange because when i did the same it gusty i had no problems (barring the stopped working after reset.)

Any help would be useful.

Thanks in advance. :)

---

### Post by pivociak on 2007-09-20
hello, now my turn.

after step 4 i get something like that"

> kamil@ubuntu:~$ sudo ndiswrapper load_fw_ar5523 /etc/ndiswrapper/netwpn111/ar5523.bin
install/manage Windows drivers for ndiswrapper
usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid'
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
kamil@ubuntu:~$ 

and light in my netgear is not flashing. 
but it starts to flash after step 5. i've done rest of the steps but i stil was not having internet connection. so i figured out that i must go to preferences/network ;) i choose wireless connection and there was a scroll list with connections to pick. and there was my wi-fi (with 43% signal) (there was also my neighbours' wi-fi with a little weaker signal ;) ). i wrote my wifi password, pick automatically IP from DHCP and nothing :( i can't open any webpages, and so and so. 

do you think that my wpn111 is working fine as it finds wi-fi networks and only problem is in my network settings? or it may be caused by that 'step 4'?

---

### Post by pivociak on 2007-09-21
anybody? [yeah i'm trying to put this thread up hoping that more ubuntu-experts look on first page of threads ;) ]

---

### Post by googlah on 2007-09-27
Hey,

I've been installing Debian and configuring it almost all day. As Ubuntu is built on Debian, I thought this how-to should also apply for me. I've installed the ndiswrapper and build-essential packages, and then ran the commands.

BUT!!!

```
ndiswrapper load_fw_ar5523 /etc/ndiswrapper/netwpn111/ar5523.bin
```

Does not work at all as others has also stated in this thread. It only gives me the normal ndiswrapper command line. I really need this line to work, in order to continue! Can anyone give me any advice?

I really need this WPN111 to work!
Many thanks,
Fredrik

---

### Post by googlah on 2007-09-28
Any1, please? What version of Ubuntu and Ndiswrapper is needed to get the above code to work?

Currently I'm on Debian Etch 4.0 (2.6.18.5) and Ndiswrapper from "main etch".. thanks in advance,

Fredrik

---

### Post by mandrill on 2007-09-28
I posted same question re: ndiswrapper on feisty w/wpn311 - no takers.....

---

### Post by sorak on 2007-10-05
encountered the same problem you guys did.

ndiswrapper 1.7 removed the load_fw method of atheros firmware support, and now just loads it like any other driver.

download the atheros firmware. i found it here: 
[http://www.airlink101.com/support/index.php?cmd=files&_a=download&id=115&prosupport_client=aeea331ccf404bff933582c007e1380a](http://www.airlink101.com/support/index.php?cmd=files&_a=download&id=115&prosupport_client=aeea331ccf404bff933582c007e1380a)

unzip the package, cd into the directory, and run
sudo ndiswrapper -i athfmwdl.inf

then proceed with the rest of the directions.

have a great day!

---

### Post by googlah on 2007-10-05
Hey sorak,

Thanks for your reply.. I've tried to load the atheros files tonight but with still no sucess. I have no clue to get this working, but one thing is for sure.. I think I will try with another distro. Currently using Debian.. Newest release of Ubuntu and apt-get install ndiswrapper should work, shouldn't it?

I'll try it tomorrow and post some results. You guys who got it working, what Ubuntu-version did you use?

---

### Post by pivociak on 2007-10-18
anything new about wpn111 in 7.10 ?

---

### Post by keeper83 on 2007-10-26
hi there!

Is there anybody who got the wpn111 running under Ubuntu 7.10??
A few days ago I was able to use my wireless network connection.. I've never been so haapy before :-)

But after some reboots the wpn did not work anymore.. so I triedto install it again. Until now it is not working.

What I did so far:

- installed the ndiswrapper
- installed the driver

thats what I got when typing "ndiswrapper -l"

athfmwdl : driver installed
athwpn : driver installed
        device (1385:5F01) present <- what does this mean??
load_fw_ar5523 : invalid driver!
netwpn11 : driver installed

But the blue light is not flashing, So the wpn is not listet when typing "lsusb"

Any ideas/updates concerning the wpn111?

---

### Post by Petergeek on 2007-10-27
I just don't understand why everyone is having such problems and coming up with such complex solutions.  The way I got mine to to work on 7.04 months ago still works happily now I have upgraded to 7.10.  This is what I did:

If you look at the notes against ndiswrapper version 1.7, it explains why you don't need load_fw_ar5523 any more.

All I did was this:

   1. Copy the all the files that are not in any folders from the WPN111 installation disk to the desktop (There are 13 of them and I don't know which ones you need)
   2. Now you install TWO drivers

sudo ndiswrapper -i /home/<username>/Desktop/netwpn111.inf
sudo ndiswrapper -i /home/<username>/Desktop/athwpn.inf

You then re-boot, the blue light comes on and once you have gone through System/Admin/Network to set up your network ESSID & encryption, the job's done.

So why won't this work with everyone else's systems?

---

### Post by W. Irving on 2007-10-28
This worked surprisingly well for me on a fresh install of Ubuntu 7.10. Not having a net connexion, I installed ndiswrapper-common and ndiswrapper-utils-1.9 from the CD. Then downloaded the tar in the first post and installed the driver.
I am by no means an expert on the matter, but perhaps you should make sure to run sudo ndiswrapper -m before modprobing ndiswrapper. After executing those two commands, the interface was created.
After that it was only the matter of choosing ESSID and key in the network settings, and the interface was brought up.

I like the irony of this setup - I am using the Windows drivers, but the installation was far quicker in Ubuntu than in that 'other' OS..
Will post here if I run into problems.

---

### Post by Dateline1945 on 2007-11-17
I'm having problems setting up a WPN-111.  I tried setting up with ndiswrapper and installed the drivers from Petergeek's previous post.  Command *ndiswrapper -l* shows both athwpn and netwpn11 as present and installed.  Immediately after setting up the drivers for the first time, wlan0 appeared in system>admin>network, and I was able to connect to a wireless router.  After rebooting, however, wlan0 disappeared from system>admin>network, but the drivers still come up as installed and present.  The little blue light on the netgear is blinking, but ubuntu won't recognize it.
I loaded ndiswrapper into etc/modules, so I don't think that's it.
I've read other posts where people with different wireless usb cards have had the same thing occur after rebooting the first time after loading drivers with ndiswrapper.  Anyone have any ideas?
Thanks!

---

### Post by artod on 2007-11-22
Hello,
I have troubles installing my Netgear WPN111: I can install the driver and ndiswrapper -l shows the driver as installed and the device as present, but when I try dmesg, I get the following message:
```
ndiswrapper (check_nt_hdr: 153): kernel is 64-bit, but Windows driver is not 64-bit; bad magic: 010B
ndiswrapper (load_sys_files:216): couldn't prepare driver 'netwpn11'
ndiswrapper (load_wrap_driver:118): couldn't load driver netwpn11; check system log for messages from 'loadndisdriver'
```

I have tried the out-of-the-box drivers. I have downloaded the 1.1 Windows driver, but I don't have cabextract, so I can't extract the drivers. But I suppose they won't work anyway, won't they? Should I try the Vista ones?

Thanks in advance for any help.

---

### Post by W. Irving on 2007-12-02
Once connected, I updated the system. Disaster.

```
[ 7545.061399] usb 2-4: new high speed USB device using ehci_hcd and address 6
[ 7545.194681] usb 2-4: configuration #1 chosen from 1 choice
[ 7545.309386] usb 2-4: reset high speed USB device using ehci_hcd and address 6
[ 7545.442070] ndiswrapper (NdisWriteErrorLogEntry:192): log: C0001391, count: 4, return_address: f8e2be8c
[ 7545.442076] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf01d2400
[ 7545.442079] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x1
[ 7545.442082] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x0
[ 7545.442085] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x0
[ 7545.442088] ndiswrapper (mp_init:263): couldn't initialize device: C0000001
[ 7545.442093] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)
[ 7545.442102] ndiswrapper (mp_halt:305): device d8ca3500 is not initialized - not halting
[ 7545.442106] ndiswrapper: device eth%d removed
[ 7545.442121] ndiswrapper: probe of 2-4:1.0 failed with error -22

```

So uninstalled ndiswrapper and ndiswrapper-common (completely) via Synaptic, fetched the latest (1.5) at the ndiswrapper website, installed build-essential (it's on the CD) and compiled according to instructions. Seems to work well. Just a suggestion for those of you who can't get it to work no matter what. Compiling isn't that difficult. :)

---

### Post by itsjareds on 2008-07-08
My internet isnt connecting :(

I have ndiswrapper installed, and my wpn111 usb adapter is plugged in and blinking. It is recognized by the Networking window and I filled in all the information including the WPA2 password. 

My router has the MAC address added for the adapter and everything, but the internet still doesnt work :confused:

---

