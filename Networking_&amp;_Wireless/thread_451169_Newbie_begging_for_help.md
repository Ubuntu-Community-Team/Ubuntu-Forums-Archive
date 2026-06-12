---
title: "Newbie begging for help"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by ocdlampwork on 2007-05-22
Hi all. My first post and I'm groveling for any support I can find.;)
My old/kids computer went down with a nasty virus and crashed a horrible death. I installed a new hard drive and decided to ditch windows and try the Linux I have heard so much about. After many frustrating hours and lots and lots of online reading I finally got Feisty Fawn live loaded and installed. But that's it. I burned the CD so what is on it is installed.  I am by no means computer savvy in case you haven't noticed yet.:D. I can usually muddle through without too many diasters I can't fix. According to my husband I know enough to be dangerous but I'm all we've got and I want to get online to get the rest of my drivers and such loaded so I can learn my new software. (That's the message I received when I attempted to download)
Here's what I've got~
Dell Dimension 4100
Intel Pentium 111 processor
My new HD is a Seagate Barracuda 7200.9 if it matters.
Too much for the current set-up but it appears to play nice after I got past the glitch of it wanting to formatt to windows.
I've got a Linksys WRT54G router and a Linksys wireless PCI adapter model #WMP54G installed in the Dimension.
I've read lots that say the Linksys router is fine with Linux but I have yet to find anything about the wireless adapter and Linux compatability. I have read so much I'm starting to confuse myself because this is my first dip into the wireless networking. My husband set it up but isn't much help because he thinks we should just load Windows and be done with it. I'm holding out from sheer stubbornness and the desire to use something other than windows to see what other parts of the OS world is like. 
I am frustrated because I didn't realize how difficult and time consuming installation it would be when I made the Linux choice.I thought the hard part was supposed to be learning the OS. Heck, I'm learning it simply by trying to get everything installed and functioning. The rest will be easy smeezy.;) It does explain why so many folks like me, without a lot of heavy duty computer knowledge, just pop the Windows CD back in and let it rip though.
 I've tried automatic network configurations and manual settings using the info. from our main computer with no success. I'm not sure if I'm even headed in the right direction. When I run the mouse over the network icon at the top it tells me the networking is disabled. I have added the settings and gotten the "setting new configuration" message but I have yet to find somewhere I can apply or put into action these settings. The installation CD doesn't load and says "there is no application suitable for automatic installation is avaliable for handling this kind of file". 
 Is there anyone who could point me in the right direction please? Website links, previous threads or direct instruction would be greatly appreciated. If my wireless adapter isn't compatible then is there one that can be recommended? Should I install a previous version of Ubuntu since it appears the Feisty version has some wireless problems without my aid. Am I in way over my head?:)
Thanks for any support!

Tracey

---

### Post by DarkN00b on 2007-05-22
The good news is I think you'll like Ubuntu if you give it a chance. Its not really any harder than Windows, just different.

The bad news (for now) is that you're going to have to familiarize yourself with the terminal (kinda like Windows' command prompt).

The first thing you want to do is click Applications > Accessories > Terminal. When the Terminal comes up, type ```
lspci
``` into it and hit enter. Look for anything that has to do with networking. For example, here's the output from lspci on my machine:

```
darkn00b@laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
**03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**
```

Notice the last line (the bold one)? That's the wireless pcmcia card in my laptop. Just post the output here and I'll bet we can help you. Please enclose any output in Code tags though -- it makes it easier to read. I'm goin' to bed now... 2:22 AM... [img]http://www.comicguide.net/images/smilies/gaehn5.gif[/img]

---

### Post by MeeMaw on 2007-05-22
Welcome to a better way!!!!!
I, too, am the computer person in the house...(my husband doesn't want to come near ours after using one all day at work!!!) and I, too, have been described as only "knowing enough to be dangerous"!!!!  We're going to help you all we can.
As a matter of fact, I have the WMP54g wireless card you have, but since Linksys put about 5 different chipsets in their cards, your posting of  "lspci"   is important in that it will tell us which one we are dealing with and how to get it working in your box.
As DarkN00b said, it's not harder, just different.....  and there are many people in this forum who are happy to help you learn all you need to know. 

Don't give up!  If you have it installed and everything works so far (other than the wireless card), you are doing really well.
:D

---

### Post by mips on 2007-05-22
You might want to consider using the wired connection (some, not all, of those pc models came with built in ethernet adapters) to get onto the net. This will make it easier for you copying & pasting stuff to the web and installing the required modules for your wireless and other stuff you need.

This will probably require you to physically move the pc to where the router is.

---

### Post by thunderkyss on 2007-05-22
> **mips said:**
> You might want to consider using the wired connection (some, not all, of those pc models came with built in ethernet adapters) to get onto the net. This will make it easier for you copying & pasting stuff to the web and installing the required modules for your wireless and other stuff you need.

This will probably require you to physically move the pc to where the router is.

really good point.

and though it  might be easier for some folks to use the CLI of the terminal, it is not absolutely necessary. Click on the network Icon in the "system tray" there should be an option there for manual configuration. You should have three options, Wireless something or other, Wired connection, and I forgot what the third is. click on Wireless, then properties. Make sure the little box for roaming is checked, then click okay.

now click on the network icon in the "system tray" again, and it should have a list of all the access points available to you. Click on the one you normally use, and that should be it.

---

### Post by DarkN00b on 2007-05-22
> **thunderkyss said:**
> really good point.

and though it  might be easier for some folks to use the CLI of the terminal, it is not absolutely necessary. Click on the network Icon in the "system tray" there should be an option there for manual configuration. You should have three options, Wireless something or other, Wired connection, and I forgot what the third is. click on Wireless, then properties. Make sure the little box for roaming is checked, then click okay.

now click on the network icon in the "system tray" again, and it should have a list of all the access points available to you. Click on the one you normally use, and that should be it.

Which will work fine if her wireless card already has drivers installed and working properly. This is probably not the case, but I should have asked up front instead of throwing CLI jargon her way. [img]http://www.diegotorres.com.ar/mensajeitor/foro/caritas/110103_sorry_prv1.gif[/img]

---

### Post by thunderkyss on 2007-05-22
> **DarkN00b said:**
> Which will work fine if her wireless card already has drivers installed and working properly. This is probably not the case, but I should have asked up front instead of throwing CLI jargon her way. [img]http://www.diegotorres.com.ar/mensajeitor/foro/caritas/110103_sorry_prv1.gif[/img]

No need to be sorry.  Your reply would have gotten us information that would have helped to solve her problem. Mine would have got an "I can't select the wireless option"

we really need more info.

But seeing how she hasn't been around in 10 hours, I'm guessing she solved her issues, and is enjoying Ubuntu as we speak.

Either that, or she's still moving her computer to a locale where she can use a wired connection.


Or taking care of the kiddos, but who does that anymore??

---

### Post by DarkN00b on 2007-05-22
> **thunderkyss said:**
> Or taking care of the kiddos, but who does that anymore??

My wife -- homeschooler of three. 
[img]http://img189.exs.cx/img189/206/confused2hw.gif[/img]

She works hard here at home. Guys -- always try to make your Wife/GF/SO as happy as possible.

Anyway maybe ocdlampwork will let us know how things are going.

---

### Post by MeeMaw on 2007-05-22
Or she's at work, then going home to care for the kids and _then_ get on the computer......
She'll be back guys..... and we'll be able to help.    ;)

---

### Post by ocdlampwork on 2007-05-23
You guys are so funny! Actually, I have my own business and it's through home, which is nice.:D We are in the process of remodeling our house so I have spent the day trying to get a broken toilet flang up (that the builder so nicely GLUED in place because it was broken:-x) so we can get the floor put down in the bathroom so our kids will no longer have to use ours. Uugghh. The kiddos computer picked a really rotten time to require CPR. Remodeling so our house is upsidedown, end of school year for three kids in three different schools will all sorts of activities, basic day to day tasks that can run a Mom ragged if we let it and installing a new OS that is totally Greek to me kinda keeps me a little busy.:D I wore myself out just thinking about it. LOL! So, please bear with me, I really appreciate all the help! It is usually late into the night or early morning before I get online. I need concentration to figure out what I'm doing and that doesn't happen when everyone is awake.:tongue::lol:
I am off to "hopefully" locate the info you guys require to help me. If I'm not back in a short time it's because I've given in to frustrated rage and shut the computer down. I tend to do that when I can't figure out what I'm doing. Plus calling it a lot of really bad names.:D

Tracey

---

### Post by ocdlampwork on 2007-05-23
O.K. here's what I've got. (Hubby and I are the trees and the kids are Twigs.:D) I hope there are no typos because I had to copy this the old fashioned way.

trees@kitchen:~$spci
00:00:0 Host Bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory controller Hub (rev 02)
00:01:0 PCI Bridge: Intel Corporation 82815 815 chipset AGP Bridge (rev 02)
00:01e.0 PCI Bridge :Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA Bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.2 USB controller: Intel Corporation 82801BA/BAM USB (HUB#1) (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
01:00.0 VGA compatible controller: nVida Corporation NV5M64 [RIVA TNT 2 model 64/model 64 Pro] (rev 15)
02:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139c+ (rev 10)
02:0c.0 multimedia audio controller: Creative Labs SB Live! EMU10K1 (rev 07)
02:0c.1 Input Device controller:Creative Labs SB Live! Game Port (rev 07)
02:0d.0 serial controller: 3Com.Corp.Modem Division 56K Faxmodem Model 5610 (rev 01)
trees@kitchen:~$


I'm going to guess that it is communicating with my main computer since it has the modem info. because the modem is not connected to this computer but the main base computer. That would explain why I noticed my main computer communicating with another in our network yesterday. It stumped me because our laptop is DOA and I didn't believe my Linux computer had made it that far. This is good right? Then again, shouldn't it have somethng about Linksys if it's communicating via wireless with the main computer? (I really do enjoy learning all this even though I get very frustrated because I want it to be easier. ;)) I'm going to stop now and wait for help because I'm tangling my brain up again.:lol:

Tracey

---

### Post by mips on 2007-05-23
> **ocdlampwork said:**
> 
02:0a.0 Network controller: [COLOR=Red]**Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)**[/COLOR]
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139c+ 


I doubt the modem thing.

Anyway you are using the Broadcom Wireless chipset which requires ndiswrapper if I'm not mistaken. I don't know much about wireless so I will let the rest of the people help you with that.

You also have wired ethernet which you can plug into your router to get everything going easily.

---

### Post by thunderkyss on 2007-05-23
> **ocdlampwork said:**
> 
I'm going to guess that it is communicating with my main computer since it has the modem info. because the modem is not connected to this computer but the main base computer. That would explain why I noticed my main computer communicating with another in our network yesterday. It stumped me because our laptop is DOA and I didn't believe my Linux computer had made it that far. This is good right? Then again, shouldn't it have somethng about Linksys if it's communicating via wireless with the main computer? (I really do enjoy learning all this even though I get very frustrated because I want it to be easier. ;)) I'm going to stop now and wait for help because I'm tangling my brain up again.:lol:

Tracey

I don't know how it's getting the modem info, if it isn't connected to your network.

> 02:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

This tells me that Ubuntu at least recognizes the wireless adapter in your computer. whatever you may call it, Ubuntu sees this info through the chipset, and this is what it really is. It may have linksys branding on it, but this is your wireless network card.

Now, if you're using the standard gnome desktop(the one loaded with Ubuntu by default), you should see an icon in the top right corner, that looks like two computers. If the drivers are installed for it, you should be able to click on it, and see all the wireless networks available to you. 

If you don't see any wireless networks(you should see the ESSID:(whatever you named your network)) then click on manual installation. 

In manual installation, you should see "Wireless Connection" (or something to that affect), "Wired Connection"(or something to that affect), and something else.

I believe there is a tab that you can click on, that will show you your Network adapters. If the drivers are installed, you'll see the card here.

Select "Wired Connection", then Click on Properties. You should see a page with "Activate Roaming"(or something to that affect) at the top, make sure there is a check mark next to it. Then close everything.

Click on the network Icon in the top right corner again, and see if you can select your network now.

I'm not at my Ubuntu machine right now, so I may be off on a few details.... but this should get you close enough to where it starts to make sense. It's very similar(I want to say exactly like OSX, but it's been so long since I messed with OSX) to OSX's network set-up, and close enough to the way you'd do it in Windows. 

By the way, what's the old fashioned way?? Pencil & Paper??

Wow.

When I was setting up mine, I copied everything to a basic text file, and stuck it on a USB thumbdrive, and shuttled it back & forth between my Ubuntu computer, and my XP machine. If you don't have one, I highly recommend you get one. You have no idea how handy they are until you start using them.

---

### Post by MeeMaw on 2007-05-23
> **thunderkyss said:**
> 
When I was setting up mine, I copied everything to a basic text file, and stuck it on a USB thumbdrive, and shuttled it back & forth between my Ubuntu computer, and my XP machine. If you don't have one, I highly recommend you get one. You have no idea how handy they are until you start using them.

So true!!! I use my thumb drive all the time! 
I think thunderkyss has you on your way, but this forum is filled with helpful people if you get stuck.
You can also try this post..... [http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom)

Let us know how it goes (hopefully from your Ubuntu machine using your wireless card!!!)
:D

---

### Post by chili555 on 2007-05-23
Before I tried ndiswrapper, I would try this: [http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom) To download the firmware package mentioned, your thumb drive will work nicely.

Oops, MeeMaw (my sister!) beat me to it! Good work, Sis!

---

### Post by MeeMaw on 2007-05-23
> **chili555 said:**
> Before I tried ndiswrapper, I would try this: [http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=Broadcom) To download the firmware package mentioned, your thumb drive will work nicely.

Oops, MeeMaw (my sister!) beat me to it! Good work, Sis!

Thanks, chili555!!! Nice to get compliments!
_I will have to say_, however, if you need help with your Linux box...... my brother chili555 is one of the most knowledgeable guys around (and I don't say this just because he's my brother - if you browse the forums a bit, you will see him helping LOADS of people get going, including me!)

As I said before, ocdlampwork, don't give up...... we're all here for you.    ;)

---

### Post by ocdlampwork on 2007-05-23
Thank you! I will see what I can do when I get the kids to bed.  I'll get back with details soon hopefully. 

Tracey

---

### Post by ocdlampwork on 2007-05-24
Back again. No luck with the firmware download. I get it to my USB buddy and open and extract (where on earth is the save option on this OS?) but after that it's downhill. Command prompt (sheesh, I think that's what it's called but it's what I'm calling it;)) says there is no such directory and I have no clue how to find the correct directory. My first experience with command prompt was during this thread. I told you guys I was a newbie. In more ways than one. I can wipe out a drive and diddle around for days creating havoc and exploring but I've never had to do anything more strenuous than load Windows until I tackled the Ubuntu OS. Windows pretty much takes care of itself except to tell when to hit which button so this is really straining my brain. I was tickled pink to actually get it loaded because even my "computer brained" neighbor couldn't get it.:D Don't ask me to do it again though.;)
I know the Linksys drivers aren't loaded because it only sees the CD as text. The only thing I have loaded on this computer is Feisty Fawn and the new HD info. I've been to the Linksys site but can't locate anything compatible with my hardware and Linux. Their forums appear pretty inactive so I didn't bother. I have also read quite a few posts where folks loaded Ubuntu, restarted their computers and were ready to go. I could not have been so lucky (insert dripping sarcasm icon here).:D
I had to use paper and pen because our extra USB ports were keyboard style and the keyboard was a casualty of soda pop and milk. The economy version doesn't offer USB ports and at the time it didn't matter. Heck, all the kids want to do is chat with each other anyway. LOL! I will now invest in a new keyboard because this post is going to kill me.
I have the two computers at the top and have the option of enabling networking or manual configuration. I've done both. The networking changes itself at it's personal whim. Sometime enabled sometimes not. Either way the network is disabled. Definitely confusing. I've done what thunderkyss recommended but still have no network options when I'm done. It all goes back to the same choices of enable networking or manual configuration even though I've done this. I would dearly love for a save settings button:D. I've done the manual configurations with the info. on my main computer.I've been diddling again and here's my results. Lets see if they shed some light on anything.
In the Host section of the manual configuration slection there are quite a few listings.
local host, kitchen (this is the troubled Linux system) and Linksys all with addys and
::1  ip6-localhost ip6-loopback
fe00:: ip6-localnet
ff00::0 ip6-mcast prefix
ff02::1 ip6-all nodes
ff02::2 ip6-all routers
ff02::3 ip6-all hosts
DNS section has nothing listed.
I've enabled roaming under wired network but it tends to uncheck itself and opt for another connection type at it's whim.:confused:

Under network tools I find some info.
Using the loopback interface device there is IP information.
interfact information~
hardware address: loopback
multicast- disabled
MTU: 16436
link speed:
state: active (this has also been disabled randomly for some reason)

interface statistics~
transmitter bytes: 1.1 KiB
transmitted packets: 16
transmission errors:0
received bytes: 1.1 KiB
received packets: 16
reception errors: 0
collisions: 0

Ping~ (ping results are good right?)
round trip statistics
minimum:0.05 ms
average: 0.06 ms
maxium:0.07 ms
packets transmitted: 5
packets received: 5
successful packets: 100%

Netstat~
routing table info~ nothing
active network services:
tcp """""" 2208 (port) listen (state)
tcp """""" 631 (port) listen (state)
tcp """""" 2207 (port) listen (state)

multicast info:
lo (interface) 1 (member) 224.0.0.1 (group)
lo (interface) 1 (member) ip6-allnodes (group)

traceroute~
3 network addys to choose from . 2 fail but the Linksys has 2 entries with 0.280 ms & 0.169 ms

Then I trolled on over to command prompt (or whatever it's called:tongue:)
typed  iwconfig (which I found in another thread)
here's what I get~
lo no wireless extensions.
eth0 no wireless extensions.
eth1 IEE 802.11 b/g ESSID:"h"
Nickname: "Broadcom 4306"
mode: managed
access point: invalid
RTS thr: off
Fragment thr: off
Link Quality= 0/100
Signal level= -256 dBm
Noise level= -256 dBm
Rx invalid nwd:0
Rx invalid crypt: 0
Rx invalid frag: 0
Tx excessive retries: 0
Invalid misc: 0
Missed beacon: 0


I then type iwlist scan and get~
lo Interface doesn't support scanning
eth0 Interfact doesn't support scanning
eth1 No scan results

Does this help any? (I sure am finding out a lot diddling. Too bad I don't understand half of it:D)(please excuse typos. I'm typing in the dark because hubby is in bed.)

School is over for the kids tomorrow morning so maybe I can get back here before the wee hours of the morning.
Thanks to all of you for the help!

Tracey

---

### Post by thunderkyss on 2007-05-24
Things are a little different here, than in the windows world. So far, I've found that you don't just go buy a CD, and install a program... I haven't figured it all out yet, but it doesn't work that way. Besides, there is so much free stuff out there, of good quality, you'll never want to buy anything again.

So Hang in there.

you're obviously on the other side of the world from me, (two hours ago, I was experiencing REM),  I'm in Texas. Name's Carlos, nice to meet you.

Anyway, I'm not the network guru that I sound like, but I do know a little. I'm also not a linux guru, I've only been at it since Friday.

the command line thing is over my head, but I'm coming to understand, that it is easier to walk a person through a CLI than it is a GUI, mainly because there are so many different ways a GUI can look, all running on Ubuntu.

But it's good that you found Network tools. looks like that is set up right. Good thing that you went through Manual config, sounds like that is right as well. I'm really surprised that you don't see your home network ESSID, when you click on the two computers in the top right corner.

Have you tried right clicking, to see if wireless networking is enabled??

> 
cj@thunderkyss-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Bullpen"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:88:BF:87:01   
          Bit Rate:2 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/94  Signal level=-46 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


That's what mine says. See where it says ath0   IEEE 802.11g ESSID:"Bullpen" Nickname:""

looks similar to eth1 on yours. I could be wrong, but to me, that says that Ubuntu knows that you have a wireless card in your machine. It knows how to talk to it, and it knows that it is working..... sort of. So my best guess, is that you can stop worrying about drivers.

Your ESSID is "H" ?? is that right?? is that for home?? If that is right, then your network interface(eth1, your wireless card) is working like it's supposed to. Check your linksys setup, and find out what rules it is using to allow a connection. Mine was set up on mac filtering to only allow specific computers, so my situation was similar to yours, in that the card was working, but I couldn't connect.

---

### Post by DarkN00b on 2007-05-24
The card will be detected by Ubuntu without loading the firmware, but will not be able to connect. It needs the firmware to be able to talk to the card - right now it can only listen.

So here's what you need to do. 

1. Copy the folder containing the firmware files to your home folder.
2. Open a terminal window (that's the command prompt).
3. Type "cd ~/bcm4" (without quotes) into the terminal and hit the tab key, that should complete the line for you.
4. Type ```
./installbcm43xx
``` into the terminal window and hit enter. Type in your password (you won't be able to see it - just type it anyway) and hit enter..

The drivers should now be installed. Restart your computer and you should be good to go.

---

### Post by ocdlampwork on 2007-05-26
Thank you both so much! I'm going to give it a go right now and see what I get to happen and I'll let you know my results.
Carlos, I'm actually only about 10 hours away from you in Tennessee.;) When I started my home business it was a late night commitment. I couldn't get much accomplished with the kids underfoot so I work after they go to bed. My husband is a firefighter so I have two out of every three days to sleep in while he's with the kids. Works pretty well for us. Especially since I am a true blue night owl. I hit the hay about 4:00 a.m.:D

Tracey

---

### Post by ocdlampwork on 2007-05-26
Arrrgh. Well, apparently I'm really dumb and don't know how to save a file. I typed the commands and received file (or folder I don't remember) or directory not found. (When I hit tab after the first command it didn't go to the next line but remained after the command no matter how many times I hit the tab key. You did mean the keyboard right? I did also try next tab in the menu but no better luck.)  I popped my memory stick into the USB and did a drag and drop into my home folder. I even did a copy and paste again to make sure it made it. I thought that would do the trick since that's what I read in the help section on saving files. What did I do wrong? I definitely don't have any network capabilities even after a restart. I also opened the folder and found the install file and clicked install that way. I thought it would work but apparently not. Why oh why can there not be a simple save button?:(
I believe I've hit desperate mode because I'm doing everything I've been told to do to the letter and nothing is working as it should.. Could my software be bad? I put the computer in hibernate mode after my post two days ago and when I went back today to check things out I had a message that hibernate mode did not enable due to some sort of problem. Should I have loaded the 6.06 version instead because I've read it's much more stable? :confused:
Is there a Ubuntu for dummies publication I can get?:tongue:
I'm going to try copying the file to my USB again and see if anything changes. Crossing my fingers!

Tracey

---

### Post by DarkN00b on 2007-05-26
Copy/paste the .tar.gz file to your home folder and extract it (right click > extract here). Then follow my directions above. This should install the firmware for you.

---

### Post by ocdlampwork on 2007-05-26
> **DarkN00b said:**
> Copy/paste the .tar.gz file to your home folder and extract it (right click > extract here). Then follow my directions above. This should install the firmware for you.

 I'm going to give you every step in what I did and maybe you can see what I did wrong. I tried again a minute ago with the same results. I downloaded the firmware again to my USB just in case the first was corrupted somehow.
Insert USB memory stick. When window for USB memory opens I right click on the firmware and cut (I copied the first time) then opened my home folder and pasted. 
I opened terminal by applications- accessories- terminal. Is this correct?
I enter cd ~/bcm4 and hit tab but nothing happens except a beep inside my computer.:confused: (The same beep I would hear when trying to access the boot menu in Windows and successfullly opened it if this helps.)
I then type in ./installbcm43xx  then enter then my password. BTW~ my password showed on the terminal screen.:( Something has gone horrible wrong hasn't it?

Here's what the terminal results were
trees@kitchen:~/cd~/bcm4./installbcm43xx
bash:cd~/bcm4./installbcm43xx: No such file or directory

I don't know where to go from here because I'm now in no mans land.;):)
Thanks in advance for any help offered.

Tracey

---

### Post by DarkN00b on 2007-05-26
You're OK - nothing has gone wrong. :)

You need to extract the files from the archive first. .bz is like a zip file - compressed. OK you have the file in your home folder. Here's what you do next:

1. Right-click on the file and choose Extract Here. That will create a folder called bcm43xxfirmware.

2. Open a terminal. Applications>Accessories>Terminal

3. Type ```
cd ~/bcm4
``` into the terminal and then hit the tab key on your keyboard. The line should autocomplete. When/if it does then just hit enter and you'll be in the correct folder. Your prompt should look like this now: ```
trees@kitchen:~bcm43xxfirmware$
```

4. Once you are in the /bcm43xxfirmware folder type ```
./installbcm43xx.sh
```

You will be prompted to enter your password. Go ahead and enter your password (you won't be able to see it being typed in) and hit the enter key. The script should tell you when it is done. All you need to do then is reboot and your card should be working. If not post here and I'll help as best I can.

---

### Post by ocdlampwork on 2007-05-26
O.K. So what do I do if the tab doesn't auto complete the line? I'm back at square one.
 I see something that may be the cause of my problem but I have no idea how to correct it. (Yes, I tried again.:)) You mentioned .bz is like a zip file but when I look at my download it is listed as .gz not .bz. 
I'm downloading from my main computer which has Windows XP on it. Does this make a difference? Otherwize I don't understand why it's not working. I've done exactly as you instructed and all I get is no such file or directory.:(
Thank you for your patience.:D I know this has to be trying when you can't get a visual and the people you're trying to help have no clue what they're doing.:tongue:

Tracey

---

### Post by mips on 2007-05-26
The file you downloaded to /home is called [B]bcm43xxfirmware.tar.gz
[/B]
From your /home forder do```
gunzip bcm43xxfirmware.tar.gz
```which leaves you with a file called **bcm43xxfirmware.tar**
```
tar -xvf bcm43xxfirmware.tar
```which leaves you with a folder called [B]bcm43xxfirmware

[/B]You could also achieve the above two steps by right-clicking on **bcm43xxfirmware.tar.gz** and selecting "Extract Here"

Now lets go to the actual folder from within /home:
```
cd bcm43xxfirmware
```Next lets install it:
```
./installbcm43xx.sh
```
To recap, once you are in your /home directory the cli output looks like this:
```
mips@obelix ~ $ gunzip bcm43xxfirmware.tar.gz
mips@obelix ~ $
mips@obelix ~ $ tar -xvf bcm43xxfirmware.tar
bcm43xxfirmware/bcm43xx_initval09.fw
bcm43xxfirmware/bcm43xx_microcode2.fw
bcm43xxfirmware/bcm43xx_initval04.fw
bcm43xxfirmware/bcm43xx_microcode4.fw
bcm43xxfirmware/bcm43xx_microcode11.fw
bcm43xxfirmware/bcm43xx_initval02.fw
bcm43xxfirmware/installbcm43xx.sh~
bcm43xxfirmware/bcm43xx_microcode5.fw
bcm43xxfirmware/installbcm43xx.sh
bcm43xxfirmware/bcm43xx_initval10.fw
bcm43xxfirmware/bcm43xx_initval01.fw
bcm43xxfirmware/bcm43xx_initval05.fw
bcm43xxfirmware/bcm43xx_pcm4.fw
bcm43xxfirmware/bcm43xx_pcm5.fw
bcm43xxfirmware/bcm43xx_initval08.fw
bcm43xxfirmware/bcm43xx_initval03.fw
bcm43xxfirmware/README
bcm43xxfirmware/bcm43xx_initval06.fw
bcm43xxfirmware/bcm43xx_initval07.fw
mips@obelix ~ $
mips@obelix ~ $ cd bcm43xxfirmware
mips@obelix ~/bcm43xxfirmware $ ./installbcm43xx.sh
Removing ndiswrapper...

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

Password:
```

---

### Post by amok69 on 2007-05-26
hi,

new here myself and just finished with a kind of similar problem.

i only skimmed this post so i might be repeating something.

as it would be a LOT easier to connect with a cable to the router i'll describe that first. once we get over that hurdle i imagine that you'll know enough to connect wirelessly alone... 

if you can't connect to the router with a cable still read the following steps, reply here and we'll continue with the wireless connection configuration.

the most obvious step is to enable the network - right click on the network icon (same icon that shows the "networking disabled" when you hover over it) and select "enable networking".

left click on network icon (same one as before) and select "manual configuration". enter your password and click ok.

in the network settings window, make sure you're on the connections tab and double click the  wired connection icon to open it's properties. for configuration select "automatic configuration (DHCP)" and hit accept.

wait till the applet finishes updating, open your internet browser and try going to any site. if you get there that means you're done with this part (unless you want to connect to your windows machine and so on).

if it doesn't work, we'll go to plan B:

to gather some info re your router's setup we'll go to your windows pc, which i assume is connected to the router somehow. on the windows pc go to start and select run. in the text line enter "cmd" and hit enter. when the command prompt opens type "ipconfig /all" and hit enter. btw, if your windows system is corrupted and you can't get this to work there are other ways of getting this info, just say so.

in the command prompt you might get a lot of information, of which we'll be interested in the   following lines:

        IP Address   . . . . . . . . . . . . . . : 192.168.0.2  
        Subnet Mask  .  . . . . . . . . . . . : 255.255.255.0
        Default Gateway  . . . . . . . . . : 192.168.0.1
        DNS Servers  . . . . . . . . . . . . . : 80.58.61.250
                              	                             80.58.61.254

some of your setting will be different. copy down that and now we'll go back to the linux pc.

left click on network icon (same one as before) and select "manual configuration". enter your password if asked to and click ok.

in the network settings window, make sure you're on the connections tab and double click the  wired connection icon to open it's properties. for configuration select "Static IP addres" and insert the following values after reading explanation below:
 
IP address . . . . . . . . . . : 192.168.0.x           (different than the windows machine)
Subnet mask  . . . . . . . : 255.255.255.0      (or same as in the windows machine)
Default gateway  . . . . : 192.168.0.1           (or same as in the windows machine)

explanation:

for a static ip configuration to work, your ip address should be in the same range as the rest of your LAN but unique. both the ip address and the default gateway are on the same range which is almost always either 192.168.0.xxx or 10.0.0.xxx. if you only have the router and windows machine on your network then for your ip pick a number which is not the ip of one of those. if you have more windows machines then get all their ip's and select a different one.

click ok and try to get on the net. if it still won't work then in the network settings go to the DNS tab. add the DNS numbers you got from the window machine if they are not LAN (remember the 192.168.xxx.xxx or 10.0.xxx.xxx?) or try using my DNS ip addresses.

if you still can't get on the net i don't think i can help you any more. but you should be good to go and i hope that your next post will come from your ubunutu machine!

---

### Post by DarkN00b on 2007-05-26
> **ocdlampwork said:**
> O.K. So what do I do if the tab doesn't auto complete the line? I'm back at square one.
 I see something that may be the cause of my problem but I have no idea how to correct it. (Yes, I tried again.:)) You mentioned .bz is like a zip file but when I look at my download it is listed as .gz not .bz. 
I'm downloading from my main computer which has Windows XP on it. Does this make a difference? Otherwize I don't understand why it's not working. I've done exactly as you instructed and all I get is no such file or directory.:(
Thank you for your patience.:D I know this has to be trying when you can't get a visual and the people you're trying to help have no clue what they're doing.:tongue:

Tracey

No, sorry. I should have written .gz not .bz. I was tired.

---

### Post by ocdlampwork on 2007-05-27
> **DarkN00b said:**
> No, sorry. I should have written .gz not .bz. I was tired.

Well shoot, I thought I found the reason it wasn't working. ;)  Oh well, I'll give it another shot with the recent instructions and let you guys know.
Thank you!

Tracey

---

### Post by ocdlampwork on 2007-05-27
O.K. got the firmware installed but nothing else has changed. Upon closer inspection it appears that there are two different wireless connections listed in different areas. In reference to post #18 the eth1 connection has a name and is recognized by Linux  but the only connection that gets scan and ping results appears to be the lo interface. This doesn't appear to be right to me since I don't believe you can run from two different connection types. Am I wrong? The manual config is what created the eth1 connection and it is the one that should be operating according to my main computer info. What I don't understand is when I change my lo interface to eth1 everything else shuts down and I can no longer ping or get any other results. Is this the place where I give my Linux system a new name like eth2 instead of using eth1?

Thanks all!

Tracey

---

### Post by mips on 2007-05-27
Ignore the loopback(lo) interface as it is a phantom/virtual interface used by the system.

---

### Post by DarkN00b on 2007-05-27
According to the post above, your ESSID is "h" correct?

Open Up Network Settings and put that into the ESSID field as in the attached picture below (where I've got "yourESSIDhere). Change the other settings to match the ones I have and your card should connect. Also, when you try this - unplug the LAN cable so your computer doesn't use the wired connection. You can always plug it back in later.

Here's what my Network Settings applet looks like:

---

### Post by ocdlampwork on 2007-05-28
My ESSID is actually "homenet1" I really don't know why it was listed as "H" but it is now corrected. I've done everything as instructed and still nothing.  When I used the static IP settings I could ping and actually show some activity. I just used the IP addy in my main computer network settings. Did that mess anything up? It seems to be the only way to get any action out of my Linux computer. My main computer uses DCHP but that addy and the IP addy are the same with the exception of a 0 at the end of the IP addy. 
I still cannot locate a driver when I pull up my network info. so apparently I need to find something that will work. I'm still at listen state and none of that has changed. I was under the impression that meant the driver was not installed. Then again, what about the firmware that is definitely installed? 
To top it all off, whenever the computer restarts I have to do everything all over again. Manually configuring network settings because it has all jumped back to where it was before I did anything. Aargh. After I installed the firmware the whole system has slowed down to a crawl. It takes quite a while to just open a terminal and half the time when I manually configure the network settings I no longer get the "changing interface settings" window so I'm not sure it's even happening.
On a positive note~ I thought I needed to get online to get the rest of my downloads so everything was fully functional before I could really start to learn about Linux. I believe I'm learning quite a bit as I go and becoming familiar with how everything operates.
I can honestly say that all this wireless info. will be permanently embedded in my brain.;):D

Tracey

---

### Post by mattva01 on 2007-05-28
One thing to try is  System > Administration > Restricted Driver Manager.
Sometimes you can install the correct driver from their.
I'm sorry if this info has already been posted.

---

### Post by benmoreassynt on 2007-05-28
This is the card I am running. It works perfectly, but you have to alter the default setup on Ubuntu. Wireless is the 'baptism of fire' than many new Linux users have to go through, esp if they use Linksys.
 
Have you sorted the problem yet? If not, get back here and I will help you out. There are quite a lot of posts in the Wiki on the linksys WRT54G issue, however my first advice is DON'T use the default bcm43xx program. Use ndiswrapper - it is far more reliable.

---

### Post by ocdlampwork on 2007-05-28
Yes, I have found a ton of different methods for getting the Linksys working but most don't come with step by step instructions and have a lot of steps that are way over my head. That and I'm not too comfortable diving into the sudo area because I'm afraid I'll damage something if I make a wrong step. 
How do I alter the default set-up and how do I add a driver through the restricted driver manager when I thought I had to download the driver. I'm sorry if I have it completely backwards because I'm learning as I go. If I already had the driver wouldn't it have prevented some of these problems? I know when I finally got the bcm43xx firmware loaded from my usb memory stick I had a message in the installation process that ndiswrapper could not be found. Do I have to "blacklist" (I'm assuming this means disable) the bcm43xx and load the ndiswrapper? 
When I first started this wireless adventure I thought I was going to be downloading something that would read the Linksys installation CD.:) Too bad it wasn't that easy.;)
Thanks you guys!

Tracey

---

### Post by benmoreassynt on 2007-05-30
Sorry for delay in reply. How are you doing?

I am trying to remember the exact process I used to get my card working, but my advice would be to maybe try to start from scratch again and take a different approach. There is so much advice here that you may get confused.

First. Have you been here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?) Do you see information that looks like it MIGHT be appropriate? As I say, I prefer ndiswrapper - I have found it far preferable in terms of speed and reliability (and simplicity getting it working), so I dont recommend the bcm43xx approach.

Can you tell me what you see when you type the following at the shell prompt (open a terminal window).

```
lspci | grep Network\ controller
```

```
lspci -n
```

---

