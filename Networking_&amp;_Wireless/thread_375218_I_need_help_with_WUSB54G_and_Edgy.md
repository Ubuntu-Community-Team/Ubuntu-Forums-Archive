---
title: "I need help with WUSB54G and Edgy"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by Yellohead on 2007-03-03
I have attempted to connect to the internet using a linksys WUSB54G (no version number) for some time now, with no success.  I have just installed the 32 bit version of Edgy, as the 64 bit version seems to be a lost cause.

I have tried to get things going using the guide in the WUSB54G for Dapper Drake thread, with little success.  When I try to install the driver with the command:

sudo ndiswrapper -i WUSB54Gv2.inf

I get:

couldn't copy wusb54gv2 at /usr/sbin/ndiswrapper-1.8 line 144

What should I try next?

---

### Post by Yellohead on 2007-03-03
Hello?

---

### Post by Yellohead on 2007-03-03
Any advice?

---

### Post by Yellohead on 2007-03-03
Will my usb adapter even work with ubuntu?

---

### Post by watson540 on 2007-03-03
it seems to be a common misconception that you need ndiswrapper for this chipset/stick. This card has a ralink chipset which means you need to be using the rt73 drivers from serialmonkey. Works fine for me. Also great for packet injection (wink,wink)

---

### Post by Yellohead on 2007-03-04
> **watson540 said:**
> it seems to be a common misconception that you need ndiswrapper for this chipset/stick. This card has a ralink chipset which means you need to be using the rt73 drivers from serialmonkey. Works fine for me. Also great for packet injection (wink,wink)

Thank you for responding.

I am still a relative newbie to Linux, so I am not too familiar with how to do a lot of the basics (extracting files to the right place, using the right commands, etc.) can you recommend a good walkthrough to install the rt73 driver (drivers?) properly?

Thanks

---

### Post by watson540 on 2007-03-04
Well lets see here, depending on your distro, you should already have *some* version of the driver. Try going to the console and typing 'sudo modprobe rt73-usb' or 'sudo modprobe rt73' i dunno it might even be named rt3usb. As far as iif you want to know how to build the driver, well.. the forums are you're friend and you have a good start already

---

### Post by Yellohead on 2007-03-04
I am bouncing back and forth between XP, where I have internet access, and Ubuntu, where I don't.  

I have made a FAT32 partition on a second drive so that I can send output from the various ubuntu commands over to windows, so that I can post output on this forum as required.  The problem is, I can't seem to even access this partition (in ubuntu) now.  Sigh.

Anyhow, I will try to use  "sudo modprobe rt73" and report what i find back here.

---

### Post by Yellohead on 2007-03-04
> **Yellohead said:**
> I am bouncing back and forth between XP, where I have internet access, and Ubuntu, where I don't.  

I have made a FAT32 partition on a second drive so that I can send output from the various ubuntu commands over to windows, so that I can post output on this forum as required.  The problem is, I can't seem to even access this partition (in ubuntu) now.  Sigh.

Anyhow, I will try to use  "sudo modprobe rt73" and report what i find back here.

I get the following output with the above command:

FATAL;  Module rt73 not found

for all name variants suggested

---

### Post by watson540 on 2007-03-05
Yeah I messed up in my post. I meant to say rt73usb not rt3usb.

In any case here is the link to the driver since google seems to elude you so well.

[http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)

Not much to do after you download that. Make sure you have all the junk to build it (build-essential, kernel headers maybe). Make and Make install it. Be sure to read the README file inside the archive. Now no more excuses, go read!

---

### Post by odox on 2007-03-05
Hi there,

First post - complete n00b so sorry :P

Having exactly the same issue.

Downloaded rt73-cvs-daily.tar.gz on windoz laptop. Copied across on a mem stick, extracted files to home dir. 

Complied driver source code

installed kernal module

Tried command "modprobe rt73"..

Got back Module rt73 not found.

Any advice for a newbie?

---

### Post by watson540 on 2007-03-05
yes, if it compiled with no errors the module is there. make sure you use sudo

sudo modprobe rt73

sorry i always use root cause im a loser and i forget to tack on the sudo command for people unlike me

try a reboot if all else fails

---

### Post by Yellohead on 2007-03-06
> **watson540 said:**
> Yeah I messed up in my post. I meant to say rt73usb not rt3usb.

In any case here is the link to the driver since google seems to elude you so well.

[http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)

Not much to do after you download that. Make sure you have all the junk to build it (build-essential, kernel headers maybe). Make and Make install it. Be sure to read the README file inside the archive. Now no more excuses, go read!


Thanks for the file.

Ok, let me restate the level of noobyness we are dealing with here.  

I currently have the tar (correct word to use? Tarball?) sitting on my desktop.  I looked at the readme.  I typed the command to extract the files (starts with xvz... or something like that), and I get an error.

Please tell me *exactly* what to type in order to get these files to where they are supposed to go.

I understand that it would be easier for you to help me if I already knew what I was doing in linux, but I don't.  So far, my experience has been to:

1.  log into XP (where I have internet access) and go to this forum

2.  ask for help.

3.  wait

4.  get some advice

5.  Sign out of XP, Sign into ubuntu

6.  Try whatever has been suggested

7.  get some error message

8.  log out of ubuntu

9.  Return to step 1.

over and over again.  This has been rather frustrating.  especially with step 3.  See the sticky for WUSB54G sticky under Networking & Wireless, my last post there, and the length of time without a response.

Thanks in advance for your help

---

### Post by watson540 on 2007-03-06
would be nice to know what the error is.

take the file put it in your home directory. /home/foo for now
ok this might take a little bit of common sense on your part but bear with me here.

we'll call the file rt73.tar.gz
go to the console. alt f2. type in gnome-terminal
(or find it in the menu)
go to the folder where you put the file
cd /home/foo
sudo tar -zxvf rt73.tar.gz
cd (folder it made) .. so type cd rt    --then hit tab to complete it -- make sure you have stuff to build it
sudo apt-get install build-essential
sudo make
sudo make install
sudo modprobe rt73
ok by now your module is inserted and your little light on the card comes on
to get it configged do this. (or set it up in gnome)
sudo iwconfig eth1 essid (your essid) key (your key if you use wep)
dhclient eth1

viola
Edit: if you get an error while doing 'make' then you need your kernel headers. oh crap. you dont have internet heh. you need to get build-essential and put it on your hardrive to transfer over man. go to packages.ubuntu.com get build-essential AND everything it depends on. get all of these files in a folder. then when you boot back into ubuntu go to that golder and type 'sudo dpkg -i *.deb' --good luck man that is a painful way to do things..might i suggest you download either the ubuntu ultimate edition 1.2 or the new gamer iso. it has all the wireless junk you need built in for the most part. that is also the reason you cant build ndiswrapper probably. but you need to download kernel-headers for your kernel (uname -r in ubuntu to find your kernel) and build essential....just got download ultimate 1.2 man that already has the tools you need to build stuff..it would be a lot easier for a noob

---

### Post by Yellohead on 2007-03-07
Thanks for your help.

Still no wireless.

Things are falling apart at the sudo make part of the instructions you posted.

I did end up getting build-essential and everything it depends on, as well as the kernel headers as per your rec, but must have missed something in these bits.

I am contemplating a reinstall, since I have lost track of all the changes I have made, and am probably not much closer to connecting.

I will then start over.

Before I do that though, can you recommend any output that I should record and post here as a good starting point of reference?

---

### Post by watson540 on 2007-03-07
yes please. it sounds like you are getting close..good job so far. paste the output of the error message you recieve when issuing the sudo make command. dont reinstall, it will just be lost time. if nothing else you can use ndiswrapper..i think , i never used it with that card but i use it with my broadcom

if you coulod somehow hook up an ethernet connection to the pc i would suggest that you use automatix or easyubuntu to install ndiswrapper, i know one of those apps does it

---

### Post by Yellohead on 2007-03-07
Ok, I won't reinstall.

just to be clear, when I attempt to do sudo make, 

which folder should I be in?

the folder made after the sudo tar -zxvf.... command, or one of the folders inside?

Also, the LED on my usb device has been on while I am in ubuntu.

Does this matter?

Anyhow, I will try to post the errors when I try sudo make

---

### Post by watson540 on 2007-03-07
yes the led matters. in my case when the led is on it means the driver is loaded and activated. just for kicks do this command and post the output as well

sudo iwconfig

In regards to the folder you should be in. Im glad you asked. you should be inside the folder that was made when you did 'tar -zxvf' ...there is a folder inside of THAT folder called Modules. that is the folder you need to be in ...Modules..dont forget under linux the case matters so make sure when you 'cd Modules' that you use the uppercase M.

also.. inside the folder you created there is a file called README. you need to READ it. it tells you how to install it step by step. if you are in a command line you can type 'more README' otherwise view it under x

---

### Post by Yellohead on 2007-03-07
OK, I entered the sudo make and sudo make install commands in the Modules folder, and everything seemed to go well, with no errors.  I did this on a hunch just before you posted!

I did iwconfig with the following output (transcribed, since I can't get at my fat32 partition, but i digress):

lo  no wireless extensions

eth0 no wireless extensions

eth1 no wireless extensions

eth3 IEEE 802.11b ESSID: MyRouterID
Mode Auto  Channel=14 Access point: Invalid
Sensitivity =0/200  Link Quality: 0 (0 for all other categories)

sit0

no wireless extensions

---

### Post by Yellohead on 2007-03-07
signing off for the night

---

### Post by watson540 on 2007-03-08
awesome man, your card is there..installed. it is eth3.
eth3 IEEE 802.11b ESSID: MyRouterID
Mode Auto Channel=14 Access point: Invalid
Sensitivity =0/200 Link Quality: 0 (0 for all other categories)

see??now set it up under gnome..good luck :)

PS. if your partition is indeed fat32 you can mount it even though it should auto mount under /media...type

mount -t vfat /dev/(fat32 partition, probably hda1 or something like that) /media/(place you want to mount it)

fdisk -l       -- will tell you which partition is fat32

---

### Post by watson540 on 2007-03-08
if you want to set up your card under console you can too, instead of using gnome. you need to know your 'essid' or the name that the router has.
type this:

sudo ifconfig eth3 up
sudo iwconfig eth3 essid (name of essid)
dhclient eth3

thats it! after the last command it should give you an ip. you can type 'ping google.com' to test it.

---

### Post by Yellohead on 2007-03-08
Hmmm...

I'm still not quite there

if I try the commands that you have suggested, I get the following error:

Can't create /var/lib/dhcp3/dhclient.leases:  Permission denied

Can't create /var/run/dhclient.pid:  Permission denied

If I try to enter my relevant info (essid, password, etc.) it accepts the info, but nothing happens

I can't browse with firefox, get nothing when I try to ping google, either in a terminal or with network tools.

when I check iwconfig, I get the same output in my previous post.  It identifies my essid, and 0 for all other categories

I will try to mount that partition for now.

BTW, what do you mean by where I want to mount the partition?  Eventually, I will add another user, and I want them to be able to access this partition without special permission, command lines, etc., but be able to go through gnome without hassles.

---

### Post by watson540 on 2007-03-08
ok you have posted here about 3 seperate times now complaining o errors realiting to permissions. ie. permissions errors, granted, its my ault or not being more thorough, and this is due to me doing things a dierent way than others do ( i use root) but...im not going to tell you again what to do i you get a permission error man. what did i tell you the riggin last time??! use sudo. you have to start piclking up on this **** on your own because we cant always be here to hold your hand :)

just noticed that i have a key not working on my keyboard , heh. thats why my post looks all jacked up. what i meant by where you want to mount it exactly that, you really shoulod google mounting or do a search in the orums. its pointless to try and describe something that someone else has done already :)

---

### Post by Yellohead on 2007-03-09
> **watson540 said:**
> ok you have posted here about 3 seperate times now complaining o errors realiting to permissions. ie. permissions errors, granted, its my ault or not being more thorough, and this is due to me doing things a dierent way than others do ( i use root) but...im not going to tell you again what to do i you get a permission error man. what did i tell you the riggin last time??! use sudo. you have to start piclking up on this **** on your own because we cant always be here to hold your hand :)

just noticed that i have a key not working on my keyboard , heh. thats why my post looks all jacked up. what i meant by where you want to mount it exactly that, you really shoulod google mounting or do a search in the orums. its pointless to try and describe something that someone else has done already :)

Re:  mounting partitions--I will try to slay that dragon later.

Re: sudo---ok, ok, I will develop my sudosenses and try harder.  I did read up on what sudo is all about.  Good idea, tough to make it reflexive if you are a relative noob to using the terminal.

Anyhow, trying that sequence of commands in the terminal (using sudo for all commands of course) led to :

DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 9

DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 16

etc.

No DHCPOFFERS received
No working leases in persistent database-sleeping

on the command "sudo iwconfig eth3 essid (name of essid)", do I tack on my WEP key somehow?

if so, how do I type out the command?

I swear, I am trying

---

### Post by watson540 on 2007-03-10
yes if you have wep enabled then that is why you get that error running dhclient.
do this
sudo iwconfig eth3 essid nameof-router key 123456789
sudo dhclient eth3

---

### Post by Yellohead on 2007-03-10
> **watson540 said:**
> yes if you have wep enabled then that is why you get that error running dhclient.
do this
sudo iwconfig eth3 essid nameof-router key 123456789
sudo dhclient eth3

Getting close, but a few more things to iron out

When I try to endter my key as described, I get the following error:

Error for wireless request "Set Encode" (8B2A);
   SET failed on device eth3; Unknown Error 524

I tried to search this out on google, without getting a clear solution.

Any ideas?

---

### Post by Yellohead on 2007-03-12
Just a quick update.

I just installed ubuntu Ultimate Edition 1.2

No wireless yet.

The upshot is that it set up my fat32 partition such that I can get into it with ease, and save files to it from both ubuntu and XP, so I can now post output here.  My extra ext3 partition on my second hdd is inaccessible for some though.  Weird, but I can deal with that later.

Looks like Ultimate is a bit easier to use for a noob, as you suggested in an earlier post.  

I think I will try to install the rt73 driver, and see if that works.  

Let me know if you have any other suggestions, requests for output, etc.

---

### Post by s9am_me on 2007-03-13
I have the exact same problem as you yellow.  I have the same WUSB54G (no v. number) and have Edgy installed. I  installed ndiswrapper and installed the linksys driver on the website.  It shows up as eth1 with all the settings 0 or invalid.  I've set all the proper info under Admin -> Networking -> Wireless Connection.  Been at this for 2 days now and have not got this wireless to work. Any luck so far?

---

### Post by s9am_me on 2007-03-13
ok i even tried the drivers from the CD and i get the same results

---

### Post by s9am_me on 2007-03-13
I also installed Network Manager via synaptics as someone mentioned before.

---

### Post by cliff01 on 2007-03-13
I may have screwed up during the "Make" portion of your instructions. I did not do a "sudo make". I did do a "sudo make install". There were no errors, but do ya' think it's dorked? And if so, how do I back out of it and do it over? The USB wireless does show up under eth0 but does not function. (No yellow light)  Also, when I check for the chipset I see something that says "islim".. 
I hope you don't mind a lurker.
Thanks!

---

### Post by Yellohead on 2007-03-13
No problems with joining in on the thread.  Its also good to see there is someone else out there with the same WUSB54G (no version).  Maybe we will all get it figured out soon.

Well, I just installed the rt73 driver, but still am running into the same issue, getting:

Error for wireless request "Set Encode" (8B2A);
SET failed on device eth3; Unknown Error 524

when I try to enter my WEP key.

At this point, I am not sure if it is the driver, some WEP issue, or something else.  I am eager to get this sorted out.

---

### Post by watson540 on 2007-03-14
try 'ifconfig eth3 up' first before the rest

---

### Post by Yellohead on 2007-03-14
No luck.

I get the same error when I try to enter the key:

Error for wireless request "Set Encode" (8B2A);
SET failed on device eth3; Unknown Error 524

Any output requests which might help find a solution?

---

### Post by watson540 on 2007-03-15
sounds like eth3 is no lolnger your wireless device, do a iwconfig to see what the wireless device is again also try the command iwconfig in place of ifconfig

---

### Post by Yellohead on 2007-03-16
> **watson540 said:**
> sounds like eth3 is no lolnger your wireless device, do a iwconfig to see what the wireless device is again also try the command iwconfig in place of ifconfig
I ended up reinstalling UE 1.2 again, as something seemed to get screwy with my first install.  Anyhow, with the reinstall, I can now get into all partitions.  Wierd, no?

Anyhow, I reinstalled the rt73 driver, looked up my device with iwconfig, found the new location  (eth2), entered the commands as instructed, and- 

Swing and a miss.  Same error.

In the (probable) event that I am misunderstanding or mistyping the correct commands, could you please type out the exact commands to enter in sequence?

I am also still suspicious that I am missing something obvious and critical to this problem, but don't know how to sniff it out.

I'll be away for about a week, but plan to take another shot at this when I get back.  Let me know if any output would help.

---

### Post by Yellohead on 2007-03-20
Back and ready to problem solve.  Here is some output that may or may not be helpful:

lucas@WFC:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: VT6105 [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 8
       bus info: pci@05:08.0
       logical name: eth1
       version: 86
       serial: 00:0d:88:f4:9a:15
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:d4000000-d40000ff irq:58
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth2
       serial: 00:0c:41:fb:c5:85
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
lucas@WFC:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth2      No scan results
sit0      Interface doesn't support scanning.

lucas@WFC:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:F2:CF:7C:8A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:0D:88:F4:9A:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:58 Base address:0xa000 

eth2      Link encap:Ethernet  HWaddr 00:0C:41:FB:C5:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5132 (5.0 KiB)  TX bytes:5132 (5.0 KiB)

lucas@WFC:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  
          Mode:Auto  Channel=1  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by benutne on 2007-03-20
Sorry to weigh in so late.  I am also having the same issues.  I'm using KUbuntu, but that shouldn't make a difference.  I have completely disabled security on my network and I still cannot get an IP from my router.  I'm really thinking this is some sort of driver issue.  I plugged the stupid thing into a Windows box and connected in seconds.  I am in the process of trying the rt73usb driver and the native drive using ndiswrapper.  I do not have high hopes for either.  I think maybe this particular adapter may be incompatible with Edgy.

---

### Post by benutne on 2007-03-20
Update:  Tried both drivers.  Neither worked.  Some people appear to have luck with the v4 adapter.  It seems the v1 (no version printed on bottom) just plain doesn't work here.  If anyone can get the v1 to work, please let us know how you did it.  Thanks.

---

### Post by Yellohead on 2007-03-21
I am also wondering if rt73 is the correct driver for this particular usb device.  Any suggestions would be appreciated.

I hope that I don't have to replace the device in order to get connected.  That strikes me as a Vista solution.

---

### Post by dmjones500 on 2007-03-22
I'm having similar problems with ndiswrapper.

If you really want to get connected, you could try the Linuxant Driverloader ([http://www.linuxant.com/driverloader/)](http://www.linuxant.com/driverloader/)).  You get a 30 day trial, and then its $20 or something.  I found it worked first time, however I kept getting a dropped connection, so I'm trying ndiswrapper.  No luck so far....

---

### Post by dmjones500 on 2007-03-22
> **Yellohead said:**
> I am also wondering if rt73 is the correct driver for this particular usb device.  Any suggestions would be appreciated.

I hope that I don't have to replace the device in order to get connected.  That strikes me as a Vista solution.


I haven't read very far back, but if you have a WUSB54G that doesn't specify a version number, then you have a version 1 model.  This uses the prism54 chipset, not the ralink chipset.  Only if your usb unit specifies version 4 can you use the rtxxxxx drivers.

prism54.org is apparently working on drivers, but I haven't tried any...

---

### Post by Yellohead on 2007-03-22
Are there any commands I can use to confirm the chipset for my device? so far I am not too sure  of any details on my device:

ucas@WFC:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: VT6105 [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 8
       bus info: pci@05:08.0
       logical name: eth1
       version: 86
       serial: 00:0d:88:f4:9a:15
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:d4000000-d40000ff irq:58
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth2
       serial: 00:0c:41:fb:c5:85
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

If it turns out that i need to use prism54, I am gravely concerned, as I can't make heads or tails of what version I need, or how to set up my system to make the driver work.

---

### Post by dmjones500 on 2007-03-23
> I have attempted to connect to the internet using a linksys WUSB54G (no version number)

^^ from your first post.

As I said, if you have no version number next to the model number on the bottom of your WUSB54G, then you have a version one unit, and it will use the prism54 chipset.

---

### Post by cliff01 on 2007-03-23
My device ID is 1915:2234 on a WUSB54G (No vs number) and I thought I read that the islsm_usb driver is what I'm to use?? And, NO it doesn't work. Where di you get the driver5s for the prism54 chip set? (Sorry for butting in.)

---

### Post by Yellohead on 2007-03-23
I am very much stumped.  I do not know what to do next.

---

### Post by dmjones500 on 2007-03-24
Well sadly my knowledge pretty much covers only which version you have!

I seriously recommend the Linuxant driverloader solution ([http://www.linuxant.com/driverloader/)](http://www.linuxant.com/driverloader/)).  It may not be free, but it's only $20 and it solves the problem instantly.

Alternatively, for similar money, you could just buy a wireless card/usb-thing that works out the box with Linux.  Perhaps something from Belkin or Edimax which uses the Ralink chipset.  Ralink have released their drivers on the GPL, so apparently it all works smoothly...

---

### Post by Yellohead on 2007-03-24
In the event that I give up on this adapter (highly likely), will version 4 (WUSB54Gv4)of the same device give me as much grief?

---

### Post by dmjones500 on 2007-03-24
I'm under the impression that v4 works reasonably well with the ralink drivers from serialmonkey, but I've never tried it.

I gave up on my WUSB54G today and bought an Edimax PCI card ([http://www.edimax.com/en/produce_detail.php?pd_id=1&pl1_id=1&pl2_id=44)](http://www.edimax.com/en/produce_detail.php?pd_id=1&pl1_id=1&pl2_id=44)).  I get a stronger signal that I had with my WUSB54G, even though the aerial is now further away (as I was previously using an USB extension cable).  It worked well with the serialmonkey drivers.

/I bought the card through The Linux Emporium, which sent me the modified ralink drivers plus some scripts to install them.

---

### Post by Yellohead on 2007-03-25
Quick update:

I threw money at the problem and it went away.

Just bought a D-Link WDA-2320.

Connected right away.

Its a shame that I had to scrap the WUSB54G, as it worked fine on the other OS.

---

### Post by cliff01 on 2007-03-25
I am trying the driverloader from Linuxamp.com It installed right away and <<<IT WORKED>> then I did an upgrade to my software and kernel and now the driverloader module and the kernel versions don't match. But at least I'm getting closer. Was that a WDA-2320...?   :)

---

### Post by Sherlock Holmboy on 2007-03-26
linuxamp.com seems to be F'ed. It comes up with something about asterisk management :confused:

---

