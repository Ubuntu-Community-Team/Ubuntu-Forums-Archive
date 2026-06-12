---
title: "Internet &amp; USB drives not running (9.10)"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by kayjix on 2010-03-23
Hi, in last 2 days I realized I am a complete novice & shall not be able to take steps without hand holding. Installed Ubuntu 9.10 with a LOT of enthu 2 days back, only to be felt betrayed over & over again in these 2 days.
 
(1) Network is not working: Poured over several threads / forums / helps but couldnt activate my internet: neither wireless, nor cable is working. Obviously no problem with my house wifi / cable connection, or I would be able to post this using my other (Windows) pc
 
PC: Compaq Presario V6000 32bit intel pentium 2GHz 1GB RAM
Network card: Broadcom bcm4311 802.11 b/g wlan (rev 02)
System > Hardware Drivers simply does _NOT_ show up the network driver, says something like 'no proprietary drivers found'
 
(2) Ubuntu also fails to recognize any USB drive (external hard disk / pen drive) or even DVD / CD !! This is my other problem, it simply fails to mount anything except my the hard disk itself. Is it because my USB drive/disks are NTFS & my ubuntu pc is now ext4 (or whatever)?
 
Conclusion
- I cant run any of your sudo apt-get install suggestions, obviously because internet is not running
- I cant download any of your tars / gzs on this windows pc & unzip + instal them on that ubuntu pc becasue there is no way of transferring data between the two (no usb / cd / dvd working on ubunutu, as already said)
 
Kindly tell me all the commands I need to run & report the output here so sombody could make sense out of them & help me figure out what has gone so horribly wrong?
Catch: no way of transferring data from that ubuntu pc to this windows pc, so I shall have to read the outputs of those commands (e.g. lspci) & manually type them here, so might take some time to respond
 
Sadly, all my enthu of switching out of windows has waned, but I REALLY want to give myself 3-4 more days with Unbuntu, before the novice / loser in me decides to return to windows forever :(

---

### Post by Directive 4 on 2010-03-23
1/ lets try to get online first.

what happens if you click up on the top right of the screen.

wireless network conection.


can you see your home network?



don't worry about 'no proprietary drivers found'
all is as it should be

---

### Post by kayjix on 2010-03-23
Thanks SO much for trying to help !!
 
Some news 1st: When I boot using live CD, then System > Administration > Hardware Drivers popup wizard displays the following in headline "No proprietary drivers are in use on this system" and lists 2 drivers with radio buttons below:
. Broadcom B43 wireless driver
. Broadcom STA wireless driver
both claimed to be "Tested by the Ubuntu devlopers"
 
Though they are "not activated", but I can "Activate" the at least the 2nd driver by clicking on "Activate" button. Upon which, "This driver is not activated" message changes to "You need to restart the computer to activate this driver". Also the Network Manager starts showing all available wireless networks (including my house wireless), and I can successfully hook to it also (without restarting !!)
 
So thats some hope !! At least the live cd can recognize (& probably activate 1 of my drivers) ...
 
 
However when botting from the installed ubuntu, the same wizard does _NOT_ list any drivers with radio buttons, and confirms the header message "No proprietary drivers are in use on this system"
 
Your question: clicking on the top right of the screeen on , it lists the following:
Wired Network <greyed out>
disconnected <greyed out>
_______________________
_V_PN Connections >
 
Thats all.
 
Live cd boot was showing
Wired Network <greyed out>
disconnected <greyed out>
Wireless Network <greyed out>
disconnected <greayed out>
_______________________
<wireless network 1>
<wireless network 2>
<wireless network 3>
etc etc
_______________________
_V_PN Connections >
 
 
Thanks for helping sir !!

---

### Post by kayjix on 2010-03-23
More news: live CD can successfully mount all USB devices (external hard disk / pencil drive) and read / copy / write / delete files / folders  !! Although my installation doesnt seem to ;)

---

### Post by rockinroll on 2010-03-23
im having this same issue i can see my testbox (thats what i named the linux box) on my router it show the ip address and the name of the pc but when i put my mouse over the internet connection icon is greyed out this is very frustrating.  also firefox will freeze if i try and change my home page to goole.com.  idk man

---

### Post by Directive 4 on 2010-03-24
umm, strange.

sometimes ubuntu has problems with the wireless key, doesn't know which one to use.

can you select

create new wireless network

from the same menu.

type in your networks name and it's key,

try this for all the different security keys,

wpa, wep 128bit. wep 40bit128bit etc...


i'll have a think, hopefully this bump will attract someone who knows what to do.



oh and my system says, 'no proprietary drivers found' to, but my wireless works.


maybe this problem would be solved if your system was fully updated. however i can see than thats a problem without internet!

---

### Post by kayjix on 2010-03-24
Unfortunately cant even create a new wireless network. As already mentioned:
 
Your question: clicking on the top right of the screeen on network manager, it lists the following:
Wired Network <greyed out>
disconnected <greyed out>
_______________________
_V_PN Connections >

Thats all.

No entry for Wireless Network at all :(

---

### Post by mullinsn2000 on 2010-03-24
I do believe that the drivers for the wireless card are contained in the LiveCD so someone with more experience here will be able to tell you how to get them onto you install through the Terminal.  Once you get online you should be able to get everything else working fairly easily.  The broadcom wireless are bad.  I just installed 9.04 because the wireless worked immediately, but I would rather have 9.10 so I will just wait for the 10.04.  Good Luck.  Someone will tell you how to do it properly sometime soon.

---

### Post by kayjix on 2010-03-24
Did the windows way: reinstalled :)
 
Now left-clicking network manager shows:
Wired Network
 disconnected <greyed>
Wireless Networks
 disconnected <greyed>
______________________
VPN Connections >
______________________
Connect to Hidden Wireless Network...
Create New Wireless Network...
 
I tried creating New wireless network with all kinds of Wireless security (WEP WPA WPA2 etc), but still shows me:
"Network
disconnected - you are now offline"
 
and System > Hardware Drivers still doesnt show up my driver
 
Thanks "mullinsn2000", I also think it is somewhere in the liveCD but doesnt get into my computer when installing. Only dont know how to extract / run it :(

---

### Post by 3rdalbum on 2010-03-24
It shouldn't be this hard... maybe your computer is REALLY oddball. Ubuntu supports over 50% of wireless cards out there these days and close to 100% of Ethernet cards, so most of the time Ubuntu really is an "out-of-the-box" experience.

I'm thinking you should be able to get a connection through an Ethernet cable. I know you've said you've tried this, but it's very possible that your networking and internet is working on the Ubuntu side, but your domain name resolution isn't.

In short: Ubuntu doesn't know where to find the server that converts "www.google.com" into the actual IP address "252.58.195.10".

Connect your Ethernet cable. Network Manager should say that it's connected. Go to the Network Manager applet and right-click, and go to Edit Connections. With your "Auto eth0" connection, click it and click Edit. Under IPv4 Settings, and the Method, choose "Automatic (Addresses Only)". This frees up the DNS field so you can type in it.

Put in the address for OpenDNS, which is:

```
208.67.220.220,208.67.222.222
```

Click OK and Apply. You may need to unplug the network cable and plug it back in again, but now your DNS resolution will be handled and your internet should work through the cable.

You can now go to System > Administration > Update Manager and hit the Check button. Install the updates if you want. Then go to System > Administration > Hardware Drivers and you should be able to activate the Broadcom driver, the same way as you can do on the live CD.


Now, in the event that this method doesn't work, you can always run the live CD, copy the driver across from /var/cache/apt/archive/ straight onto your Linux partition, and then boot into your installed Ubuntu and install the package.

/var/cache/apt/archive is where you go to Places > Computer and then Filesystem, then var, then cache etc. You should be able to mount the Linux partition by selecting it under Places.

---

### Post by kayjix on 2010-03-24
Thanks 3rdalbum, however ... seems my experience is full of "however"s ;)
 
inserted ethernet cable, a prompt comes up: auto etho0 connection established
open browser, type "252.58.195.10" in addressbar, still "Unable to connect"
so doesnt seem like IP resolution problem
 
anyway
entered "208.67.220.220,208.67.222.222" in "DNS servers"
doesnt help, neither google nor its IP can be connected
 
You can now go to System > Administration > Update Manager and hit the Check button. Install the updates if you want.
Doesnt work. Cant fetch any updates (probably coz network still doesnt work?)
 
Then go to System > Administration > Hardware Drivers and you should be able to activate the Broadcom driver, the same way as you can do on the live CD.
Driver doesnt appear in the list still
 
anyway
manually copying the driver from liveCD into computer & trying to install the package
Places > Computer > Filesystem > then var, then /var/cache/apt/archive/
but which is the driver?
there are 2 "things" in archive:
(name) partial (size) 0 items (type) folder
(name) lock (size) 0 bytes (type) unknown

---

### Post by kayjix on 2010-03-24
More meticulous this time:
 
booted using liveCD

system > Administration > Hardware Drivers
noticed 2 drivers present there:
Broadcom B43 wireless driver
Broadcom STA wireless driver

"Activated" the 2nd one
says: you need to restart the computer to activate this driver
I did _NOT_ restart (I am on liveCD, wont restarting erase everything?)
 
Network Manager now shows several wireless networks. I chose mine.
verified that [www.google.com]("http://www.google.com") is connecting
 
navigated to Places > Computer > Filesystem > then var/cache/apt/archive/
It still shows only 2 "things" there:
(name) partial (size) 0 items (type) folder
(name) lock (size) 0 bytes (type) unknown
 
they have zero size, I dont think they are the requisite package :(
 
 
 
system > Administration > Hardware Drivers
"Removed" Broadcom STA wireless driver
"Activated" Broadcom B43 wireless driver
says: this driver is activated and currently in use

Network Manager > I chose my wireless network
verified that [www.google.com]("http://www.google.com/") is connecting in this driver also ...
 
Places > Computer > Filesystem > then var/cache/apt/archive/
Still shows only 2 "things" there:
(name) partial (size) 0 items (type) folder
(name) lock (size) 0 bytes (type) unknown
 
Seems I cant locate the package that my liveCD is using ...

---

### Post by Directive 4 on 2010-03-24
here's a thread that seems to hold all the answers.

let me know how you get on

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by kayjix on 2010-03-24
Thanks Directive 4, still problems
did everything step by step
 
system > Administration > Hardware Drivers
shows
Broadcom STA wireless driver
active & currently in use
 
wireless:
Network Manager > try to connect to my home network
it asks for wireless network authenticatino required password
keeps asking for it again & again, even though I enter it correctly
the network manager icon keeps going round & round but never really connects to my home wireless
although I can see my home network & lots of neighbouring networks, but can seem to connect
 
wired:
insert ethernet cable
says Auto eth0 connection established
open browser, but still cant connect to
[www.google.com]("http://www.google.com")
or
252.58.195.10
 
I think I am close: driver ready & networks visible, only cant seem to hook on ...

---

### Post by Directive 4 on 2010-03-24
ah. maybe try all the different types of wireless security. i had that problem for days at the start, but wired should work.

umm

---

### Post by kayjix on 2010-03-24
I am using the same wireless security that my windows pc is using, so I dont think I should try with a different security :( But, as said, wired is not working either :((

---

### Post by admiralspark on 2010-03-24
Heh, I hate to say it, but the Broadcomm drivers are a serious pain to work with. I've got a Broadcomm 4318, used to be in the same boat.

Assuming you don't have a corrupted install CD...

Here's the deal. There's two ways to get this process going, and you probably will have an easier time than I did getting it to work.

First:
_**<<[SIZE=3]Linux Drivers[/SIZE]****>>**_
The two drivers that Ubuntu associates with your card are the B43 and the STA. I personally will recommend the B43, it seems to be superior to what I've heard about both the STA and the ndiswrapper, which I'll mention later. To utilize either driver, first go to System -> Administration -> Software Sources. On the screen that pops up, tick the bottom option, "CdRom with Ubuntu 9.10 'Karmic Koala' ". This allows you to download content (including drivers) off of the cd. Then, click "reload" to refresh the content available. It may (probably will) spit back something about 'cannot connect to repositories', just ignore that.

For the [COLOR=Red]**STA DRIVER**[/COLOR]:

Go to System -> Administration -> Synaptic Package Manager. In the search box, type 
```
bcmwl-kernel-source
```And, when you see it, tick it and click apply, to install it. Then, simply go to System -> Administration -> Hardware Drivers, click it, and reboot computer. 

For the [COLOR=Red]**B43 DRIVER**[/COLOR]:

For these, it's all done in a terminal. Please _READ THE STEPS_ before you continue:
```
cd /media/cdrom0/pool/main/b/b43-fwcutter; sudo dpkg -i b43-fwcutter*
```****Note:** Do not select 'fetch and extract firmware'. This extraction will have to be done manually. See also the b43-fwcutter [manual]("http://manpages.ubuntu.com/manpages/karmic/en/man1/b43-fwcutter.1.html") page.**

If that doesn't bring it up in Hardware Drivers, you'll need an internet connection and to follow the directions [here]("http://ubuntuforums.org/showthread.php?t=766560").


Hope this helps,
-Admiralspark

_**EDIT**_: As for your ethernet, please post the output of ```
ifconfig
``` here AFTER YOU'VE 'CONNECTED'. We'll see what that can tell us.

---

### Post by admiralspark on 2010-03-24
As for your current setup:
try running the commands ```
sudo ifconfig wlan0 down; ifconfig wlan0 up
``` and ```
sudo ifconfig eth0 down; ifconfig eth0 up
``` in a terminal.

What kind of encryption does your wireless router use? You possibly could be sending it the wrong kind of password (sending it as WEP if it's a WPA password).

The other possibility is that there is a permissions error. I found this when trying to print, I had the same repetitive asking for my password.
Go to System -> Administration -> Users and Groups. Now, click on the key in the bottom center to unlock, then  highlight your username and click on the Properties button. Click on the User Privileges tab, and make sure EVERYTHING is checked. Sometimes the "Connect to internet with wireless/ethernet is not checked, and that would give you the symptoms you're experiencing. 

If that doesn't solve it, we may have to start checking the system messages.

---

### Post by kayjix on 2010-03-24
thanks admiralspark for trying to help, I shall definitely run all you suggestions tonight when I get back home.
 
Meanwhile, is there a way of copying my ubuntu pc xterm output to my windowsPC (for posting on this thread)? U know, neither internet, nor usb drives are currently working on ubuntu PC right now :(
 
Otherwise, I shall manually 'read-from-there & type-here' but am afraid of typos, though shall pay utmost care ...

---

### Post by egalvan on 2010-03-25
Let's concentrate on the wired LAN first...

Connect your machine with a cable...

boot and open a terminal, and run this code...

```
 sudo ifconfig
```

below is what my machine shows....
the **bold** parts; are what we want to see...
the [COLOR="Blue"]BLUE[/COLOR] values; exact values are needed.
the [COLOR="GREEN"]GREEN[/COLOR] values; only need to see if there are any "errors", exact values not needed.

your machine will (most likely) have different values...


```
~$ [COLOR="red"]sudo ifconfig[/COLOR]
[sudo] password for ernest: 
[B]eth0      Link encap:Ethernet  HWaddr 00:12:3f:a1:f7:c5  
          [COLOR="Blue"]inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0[/COLOR]
          inet6 addr: fe80::212:3fff:fea1:f7c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1480  Metric:1
          [COLOR="green"]RX packets:1088234 errors:0[/COLOR] dropped:0 overruns:0 frame:0
          [COLOR="green"]TX packets:469436 errors:0[/COLOR] dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1027948796 (980.3 MB)  TX bytes:55679902 (53.1 MB)
          Interrupt:16 [/B]

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:678376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:678376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:512110161 (488.3 MB)  TX bytes:512110161 (488.3 MB)
```

Do this with the LiveCD so we can get a feel for the hardware...
should be easy as you have internet connectivity...

Then do it again with the hard drive install...
sorry, you will have to copy to another machine...

---

### Post by kayjix on 2010-03-29
Thanks admiralspark & egalvan for help, I am currently travelling, shall try out these steps & update you here as soon as I return (1 week) !!

---

### Post by egalvan on 2010-03-31
> **kayjix said:**
> PC: Network card: Broadcom bcm4311 802.11 b/g wlan (rev 02)
System > Hardware Drivers simply does _NOT_ show up the network driver, says something like 'no proprietary drivers found'

This does not mean that no drivers are being used...
it just means that no "**proprietary** drivers are loaded...
it could mean that open-source equivalents have been loaded...
and no others are needed...

Or it could mean that no drivers were loaded, due to no internet connection being found...
and you need those proprietary drivers.

There ARE ways to get a list of needed packages that need to be installed, but you need a way of getting that list onto a net-connected machine...
 which is problematic in your case...

And a final question.....
does your laptop have a hardware switch for the wireless LAN?
Don't laugh, this was the problem with a laptop a co-worker had just bought... no wireless... it seemed the switch was OFF...
and *don't* assume that because it *works in Windows* that it should work the same in Linux...
check for that switch... please...


> (2) Ubuntu also fails to recognize any USB drive (external hard disk / pen drive) or even DVD / CD

This has me even more stumped....

It's leading me to suspect a bad install...

Since you say you can run a LiveCD, then the hardware is running well.

Have you checked the LiveCD to make sure  it is a good burn?

When you boot the LiveCD, there is an option on the Ubuntu Boot Menu
it should be called something such as...

"check media for errors"

run it, it will run a check-sum on all the files...
hopefully it will report a bad burn, because this is the easiest to fix :D

---

### Post by kayjix on 2010-04-07
You guys are AMAZING !! Its your constant help & support that makes things work for us beginners !! Thanks admiralspark for the hint:

"The other possibility is that there is a permissions error. I found this when trying to print, I had the same repetitive asking for my password.
Go to System -> Administration -> Users and Groups. Now, click on the key in the bottom center to unlock, then highlight your username and click on the Properties button. Click on the User Privileges tab, and make sure EVERYTHING is checked. Sometimes the "Connect to internet with wireless/ethernet is not checked, and that would give you the symptoms you're experiencing."

I did this & rebooted, _CAN_ connect to wireless now !!

---

### Post by kayjix on 2010-04-07
Then when I restarted, it automatically prompted me for ~100 updates available, I installed all, restarted, now USB hard disk & pen drive  also started working. I guess it could be because of some correct patch / driver / something got downloaded & installed in that bunch of updates ...

---

### Post by kayjix on 2010-04-07
But wired lan (using the cable) still doesnt work. When I try to connect using Network Manager, it shows successful:
Auto etho0
Connection established


So let me show the output messages you have requested:


ifconfig (with wireless connected & working)
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:44:9c:4c  
          inet6 addr: fe80::21b:24ff:fe44:9c4c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8444 (8.4 KB)  TX bytes:23199 (23.1 KB)

eth1      Link encap:Ethernet  HWaddr 00:1a:73:5d:70:9a  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe5d:709a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:37005 errors:0 dropped:0 overruns:0 frame:358373
          TX packets:34107 errors:11 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51944006 (51.9 MB)  TX bytes:3568185 (3.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


ifconfig (with wired lan connected but not working):
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:44:9c:4c  
          inet addr:192.168.8.3  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe44:9c4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20092 (20.0 KB)  TX bytes:43837 (43.8 KB)

eth1      Link encap:Ethernet  HWaddr 00:1a:73:5d:70:9a  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe5d:709a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:37309 errors:0 dropped:0 overruns:0 frame:380111
          TX packets:34434 errors:11 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52277601 (52.2 MB)  TX bytes:3608175 (3.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

---

### Post by kayjix on 2010-04-07
@egalvan: thanks  for your valuable time & suggestions,

> **egalvan said:**
> This does not mean that no drivers are being used...

And a final question.....
does your laptop have a hardware switch for the wireless LAN?

This has me even more stumped....
It's leading me to suspect a bad install...

- I can see 1 proprietary driver now: Broadcom STA wireless driver (this driver is activated and currently in user"
- You are right, there IS a wireless switch, I have made sure that it is ON
- The installation seems fine (at least till now :() and I have check-sum'ed ...

But my wired lan is still not working. Your suggestions / comments are welcome since I can easily paste any command outputs here with  wireless working at the least :P !!

---

