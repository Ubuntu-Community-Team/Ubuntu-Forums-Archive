---
title: "&quot;It Just Works&quot;...Huh?"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by plinydogg on 2007-06-08
Hi everyone,

I was really excited about learning Ubuntu and from the first moment I booted up the LiveCD I was very impressed. I had envisioned a steep learning curve initially but was anxious to learn as much as I could and eventually make Ubuntu my main OS. The community here was VERY supportive and I couldn't have gotten my dual-boot (with Vista) working without them (thank you again!). 

But the Internet (especially wireless) problems are just too much to bear. My fiance asked me the other day what I was working at so intently and I told her that apparently I had the most incompatible type of wifi card for Ubuntu (Broadcom bcm4318). After days and days of trying to get it work I just can't. I've tried every tutorial out there and tried to follow all sorts of tips that you people generously took the time to provide me with. And while I'm a linux newbie, I'm not stupid. I've used a command line before and even written some computer programs before. And I'm not one of those people who is looking for a different version of Windows. I want to use the command line to do stuff!

The fact that one type of wireless card doesn't work isn't that big of a deal. The thing that really got me down was that when I decided that I was willing to buy a new wireless card and went to look up which cards work the best in Feisty, I found absolutely no consensus! There is not a single wireless card that reliably works in Ubuntu 7.04! For each card and chipset, there are dozens of disagreements, tutorials, tips, problems, purported solutions, and the like. 

I'm not trying to be overly harsh, but how in all honesty can Ubuntu really be considered a viable alternative to the other OSes out there when there's not a single reliable way to get wireless working? That's just mind boggling to me. 

Add to that the fact that my Ethernet won't work in Feisty either! I don't know what the problem there is because (as is also the case with my wireless) it works fine in Vista. Having said that, I haven't really looked into the Ethernet issue as much and so maybe it's easily fixable (but that would surprise me). 

The final component of my gripe is that from what rudimentary tinkering I've done so far it seems like this OS isn't something that you can really explore without an Internet connection. There may be plenty of neat programs out there to do X or Y but in order to get them, you usually have to use apt-get or some other Internet-based solution. Thus, the sorry state of the wireless support (and ethernet support?) is just jaw dropping in its proportions. 

And aside from this excellent forum, there is no where else to turn for help (unless you want to shell out $250). The books out there on Ubuntu don't have the solution, nor does anyone at any retail outlet have a clue of what Ubuntu is, nor are there any Ubuntu user groups in my geographical area. I could probably put a classified ad in my paper saying "Get my wireless working in Ubuntu and I'll give you $10,000" and no one would respond. 

Like I said above, I really, really want to learn to use and love Ubuntu. That's why this is so disappointing. Perhaps even more sad is the fact that Ubuntu is "the" distribution out there right now, which is to say that there are a lot of people who have heard about it and are going to be trying it. And of those that do so, how many are going to be unable to get their wireless working and walk away from Ubuntu and put it out of their mind forever? That seems like a huge waste of potential lifelong supporters and contributors to this project.

Against this backdrop, the "it just works" slogan is just laughable. I know that part of the Ubuntu philosophy requires that proprietary drivers, etc. not be included in distributions but I mean, seriously, does anyone have a realistic idea when things are going to get better?

---

### Post by ryanVickers on 2007-06-08
Wireless internet huh, yeah, they made it worse in some cases I think :p

but after some looking around, there's lots of help because it is the most common problem!

---

### Post by floke on 2007-06-08
I've used intel pro 3945 flawlessly with ubuntu since edgy (though gnome-network-nonsense is a load of crap - install wifi-radar the second your wireless works in case it breaks) - as for your wireless have you tried this:

[http://ubuntuforums.org/showthread.php?t=405990&highlight=easy+way](http://ubuntuforums.org/showthread.php?t=405990&highlight=easy+way)

---

### Post by plinydogg on 2007-06-08
That's the thing: I don't mind looking around but I've tried EVERYTHING I've found out there. 

And if you trust this poll ([http://ubuntuforums.org/poll.php?do=showresults&pollid=1806](http://ubuntuforums.org/poll.php?do=showresults&pollid=1806)) then fully 57.94% of Ubuntu users can't get their wireless working. That's unbelievable! If the promotional materials for Ubuntu said:

"42.06% that your wireless will work with our OS"

No one in their right mind would even think about ditching another OS for it!

I'm not trying to mean, I'm just saying...

---

### Post by plinydogg on 2007-06-08
Steve.K: You're lucky that you have an Intel card, while there was by no means perfect consistentcy, a lot of the posts I read led me to believe that people have more success with Intel cards than others. 

And, yes, I have tried the method in that link but I'm going to try it again (I've been trying one method, having it fail, doing a fresh install of Ubuntu to get rid of any changes, and then moving on to the next method. The next, and last, thing I'm going to do is repeat the process with each method). Thanks for posting it though!

---

### Post by luisromangz on 2007-06-08
Umm well, the Broadcom Wireless model 4318 works flawlessly with Ubuntu in my Compaq Presarion M2000. Both using te bcm43xx and ndiswrapper drivers. But of course I agree with you in which wireless support is far from perfect. But the ones to blame aren't ubuntu nor linux, but those crappy chipset manufacturers.

The issue with the ethernet card is more disturbing to me.

I hope you get your problems solved!

---

### Post by floke on 2007-06-08
Maybe you could post the output of 'iwconfig' from a terminal so that others more knowledgable than ourselves might be able to assist?

---

### Post by mtn on 2007-06-08
I not sure if this will help, but...if you are after a new Linux compatible wireless card the Linux Emporium sell them [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

A good bet I reckon (if you are in the UK that is!). If you need more info I have found them very helpful when calling. Could also try [http://efficientpc.co.uk/index.php?cPath=24](http://efficientpc.co.uk/index.php?cPath=24) I reckon they would have a good idea!

---

### Post by plinydogg on 2007-06-08
luisromangz: I know that the broadcom 4318 works fine for some people, but not for others (just like every card it seems)

Steve.K.: I've done the iwconfig thing before. I can tell you what it says from memory because I've messed with it so many times. After a fresh install, it lists (under the alias eth1) that I have a broadcom 4318 and have the broadcom43xx driver installed. After I attempt (unsuccessfully) to use ndiswrapper, there is nothing there and eth1 doesn't exist (i.e., my card isn't even detected anymore)...and this despite the fact that when I type in "ndiswrapper -l" it tells me that both the hardware and drivers are installed! Thanks for the suggestion though!

mtn: Thanks for the suggestion but I imagine having them shipped to the US would be rather expensive...perhaps I'll have to look into this. Thanks.

---

### Post by Henry Rayker on 2007-06-08
Ubuntu's wireless has been getting worse and worse since Dapper. That's why I left. I have found Fedora's releases to break less and fix more.

---

### Post by plinydogg on 2007-06-08
Henry Rayker: Thanks for the tip. How is Fedora as far as newbie's go? I'm not a computer newbie, just a Linux newbie. Thanks!

---

### Post by Gary.M on 2007-06-08
Linux newbie here, 3 machines, wireless network... wireless works on every machine. 1 Orinoco PCMCIA card, 1 D-Link PCI adapter, 1 IBM Thinkpad R40.

It was the first thing I checked with the live CD on each machine. Each worked out of the box.

I'd bet you pick something from the compatibility list and you'll be OK.

---

### Post by lawr_rawr on 2007-06-08
Wireless working fine for me (no GUI manager, though) with Ralink RT73. Seems like the Intel cards are the best -- my boyfriend's laptop worked straight away. He has a Netgear WG311T PCI card (Atheros guts) in his desktop, and that, too, was detected. Between Fedora and Ubuntu on 2 laptops and a desktop, only Ubuntu automatically detected both the Intel and Atheros wifi. Configuring the Atheros card under Fedora took a couple hours...

---

### Post by plinydogg on 2007-06-08
Thanks for tips Gary.M. and lawr_rawr. I'm not asking for out of the box functionality. I don't mind running ndiswrapper (or whatever) to get it running. I'm just wary of any of the other cards that say they work with ndiswrapper because that's what people say about mine but it hasn't been true for me. And while buying a new wireless card isn't an enormous investment, I don't want to just guess....

---

### Post by floke on 2007-06-08
Best for wifi IMO is PCLinuxOS - burn a copy and try it - simply amazing - you could also try Linux Mint (based on ubuntu). PCLOS is very easy to set up.  I have a partition for it myself :D

---

### Post by plinydogg on 2007-06-08
Thanks for the tip Steve.K. I'll definitely look into them. Perhaps I'll give one more wireless card a try in ubuntu (but which one?) before actively looking for a linux alternative....

---

### Post by plinydogg on 2007-06-08
One more thing Gary.M: the problem with the compatiblity list, as I see it, is that most of the data is from the pre-fiesty days. And if there's one constant drumbeat throughout most of the posts on these forums its that "X card worked perfectly in 6.06 but doesn't work in Feisty." In other words, if it says works great for a given card, looking over to the date of that data usually reveals that it was working great in 6.06 but there's no reason to think that it will work well in 7.04.

---

### Post by plinydogg on 2007-06-08
Does anyone know if there are any plans to improve things in the next edition of Ubuntu?

---

### Post by jglen490 on 2007-06-08
plinydogg --

There are a lot of variables when you move from one distro to another and even in an upgrade within the same distro.  Right now, I run Kubuntu 6.06 LTS -- O.K. I'm a KDE freak.   I moved from Mandriva to Kubuntu (after a brief flirtation with PC-BSD), because I heard so much that was good about Dapper.   Also, I was getting desparate because my Broadcom 4318-based cardbus wifi card wasn't doing anything.  Finally, while browsing through this forum one day, it all came together, and it's worked ever since.  "It" is a combination of blacklisting the the bcm43xx module loaded by the kernel, using the ndiswrapper and utils found on my install CD, and the Win2K .inf and .sys files from the driver disk that came with the wifi card.  That and a little help from kwlan to configure the wifi to router connection with WPA.

I still run Dapper, the "Long Term Support" version of Kubuntu, and I have no intention of changing, until the next LTS version.  Some folks have upgraded to Feisty with problems, others without.  There seems to be little consistency.  It may be that for some, configurations get clobbered in the upgrade - for whatever reason - and for others their configurations don't.  I use adept, sometimes apt-get, (same underlying process) to keep my system up to speed and to install new apps.  But I think, the simple fact that I keep with the same version of Kubuntu has about eliminated any difficulties.

Obviously, that won't work for everyone.  I can't explain, either, why some version upgrades work, while others don't.  For me it's all about staying with something that is stable and allows me to do what I want to do with my computer.

---

### Post by NotReallyIntoPokemon on 2007-06-08
Allow me to commiserate with you, plinydogg.  I was lured in to this by tales of how easy everything was.  "A Linux Even Your Mom Could Use."  And, after I got past the installer freezing when trying to partition some swap space and had it finally installed, I immediately was presented with another hurdle - no wifi.  For me, this basically equates to no internet, which honestly makes the entire thing useless to me.  A trip here reveals that not only are these problems widespread, but that mine in particular is a known and unresolved one.  At least Windows "Just Works" when you just install it over 50% of the time.  If Ubuntu is exhibiting this kind of dramatic problem straight from install, I shudder when I consider how bad it could be when I do something to screw it up.

---

### Post by oxalá on 2007-06-09
> **NotReallyIntoPokemon said:**
> Allow me to commiserate with you, plinydogg.  I was lured in to this by tales of how easy everything was.  "A Linux Even Your Mom Could Use."  And, after I got past the installer freezing when trying to partition some swap space and had it finally installed, I immediately was presented with another hurdle - no wifi.  For me, this basically equates to no internet, which honestly makes the entire thing useless to me.  A trip here reveals that not only are these problems widespread, but that mine in particular is a known and unresolved one.  At least Windows "Just Works" when you just install it over 50% of the time.  If Ubuntu is exhibiting this kind of dramatic problem straight from install, I shudder when I consider how bad it could be when I do something to screw it up.

first -- I love [xkcd]("http://xkcd.com/c178.html"), too.

second:  I just installed Ubuntu Studio (Feisty), which recognized my D-Link [WDA-1320]("http://www.dlink.com/products/?sec=0&pid=475") almost as soon as i got to the desktop.  It Just Worked.  That said, I had a horrible time with wireless cards in previous releases.  I have always gone back to Windows because I needed wireless access -- not because I needed a particular program (though I think I&#314;l miss iTunes).  This time it worked though -- from XP to Ubuntu Studio with 0 hangups.  True story.

---

### Post by tgalati4 on 2007-06-09
Try the Dapper live CD and see if wifi works.  If not try ndiswrapper under Dapper.  Dapper is a decent distribution.  I've been running it for the past year on several machines.  165 days of uptime on one of my machines.  After you have applied the updates,  you will still be running the near-latest kernel, and 99% of the 18,000 packages will install and run in Dapper.  You want to explore the applications, the OS is only needed to access all of your hardware, so find a distro that works with your hardware.  When you find that distro, then you will understand--"It Just Works".

Right now:  "It Just Works, just not for you."

---

### Post by NotReallyIntoPokemon on 2007-06-09
[QUOTE=Ubuntu's new motto]It Just Works, Just Not For You.[/QUOTE]
I'm not sure it's quite so catchy.

Far from being just not for me, however, it appears to just not work for quite a few!

I may give Dapper a shot, however.  I didn't realize I was using something that was released less than a month ago, something I'd be extremely hesitant to do do, normally.

---

### Post by tgalati4 on 2007-06-09
The normal foray into Linux is a Windows user whose system has borked.  Someone helpful comes along and pops in a Dapper Live CD and boots their system.  It looks like an operating system from another planet.  Except you can now see your stranded data--your pictures, your music, your email.  After fixing a few things, your system boots normally into Windows and you are happy.  Until your system gets borked again.  Then you ask, what was that alien thing that was used to repair my system?

Trying to install Feisty without running Dapper Live for a few weeks to ensure hardware compatibilitiy can cause problems because Feisty is a moving target.  Dapper is in maintenance mode, so minor tweaking is taking place, but overall its pretty stable.

The bottom line, it's your computer, do what you want.  If you break it, you get to keep both pieces.

---

### Post by kevdog on 2007-06-09
I didnt know this particular post was a rant forum.  If the guy that started this post would actually post some information for us to help him with his wireless problem, other than complaining that he cant get his wireless working, I think we would all be better off.  Does wireless support stink in Feisty out of the box -- YES!!! -- now get it over it and on to fixing it.  There are plenty of posts that address installation of the installation of bcm43xx drivers for cards with the broadcom chipset, and many addressing the installation of ndiswrapper.  Perhaps you should just go to the ndiswrapper website at sourceforge.  The documentation of how to install drivers for your card are very complete.

I get angry when I see posts like this!

---

### Post by idx on 2007-06-09
Pls see the following post:

[http://ubuntuforums.org/showthread.php?p=2771887](http://ubuntuforums.org/showthread.php?p=2771887)

hope it helps.

---

### Post by Mets on 2007-06-09
Ubuntu is a lot friendlier with configuring things than most of the other Linux distros, but it's still Linux and therefore inherently complicated.  There's a lot that could be done to make networking easier.  Personally, I think it's embarrassing when there are basic things that Windows does better than Ubuntu or Linux in general but I don't decide how the OS gets developed.  I don't think I've ever heard or experienced a case where wifi didn't work on Windows with minimal effort at most.  You just plug in your card, maybe install some drivers, and connect.  In Ubuntu, literally half of the Networking forum is people struggling to get theres to work.

---

### Post by jincongz on 2007-06-09
Funny of all of you saying about Dapper, i used to have dapper on my lil' sister's computer, but wifi wouldn't work. Upgrading to Feisty acually fixed the problem, not adding to.

---

### Post by plinydogg on 2007-06-09
kevdog: I *have* posted information about the problems I'm having on other threads. In fact, you even gave me some tips on one of them (thank you for that). I have attempted to do what those threads tell me to do. Here's a summary, either:

(1) Install bcm43xx-fwcutter, reboot, and everything should just work, albeit somewhat intermittently; or
(2) Blacklist bcm43xx, install ndiswrapper, install drivers, reboot, and it should work. 

There are variations on each of these methods, but these are basically it. I've tried them all and it just doesn't work. I didn't post this thread until after literally days of searching these forums and receiving tips from you guys (thanks again to all who tried).

NotReallyIntoPokemon and Mets: thanks for understanding!

idx: thanks for the tip, but I've more or less already tried that. It's another variation of the ndiswrapper installed method. 

oxala: thanks for the tip on the WDA-1320. Regrettably, a PCI solution won't work for me since I'm on a laptop, but I have heard good things about the WNA-1330 (I think that's what it's called) from D-Link. Perhaps I'll give it a try. 

tgalati4: Thanks for the tip. I thought about switching down to a previous release but my understanding is that before 7.04 there was no option during the install process to specify where GRUB is installed, which means that I would be required to install it into the MBR and I really want to avoid messing with Windows if at all possible. 

jglen490: I'm glad you find a way to make your wireless work and I agree with what you said about the inconsistency of experiences out there. 

Thanks everyone for posting!

---

### Post by kevdog on 2007-06-09
Please tell me what type of hardware or wireless card you have.  This can be found by typing (assuming you have a wireless PCI card):

lspci

If you have already done this, my apologies, but there are a lot of wireless cards thrown around in this post, and a lot of people making recommendations that do not address your problems.  If you want to switch to another distro -- Great -- If you want to stick with Ubuntu and get things working, then I will help you.  This is a Ubuntu help forum, not a "hey guess what distro is better than Ubuntu" forum.

If you could also post (or cut and paste), your /etc/iftab file it would be great.
Also the results of: uname -r


A couple of other questions.  Do you have a working internet connection somewhere??  I assume the computer you are installing Ubuntu on can not connect.  In this case you will need a computer with internet connection and a USB stick for file transfer.

If you have the ndiswrapper package installed -- I think you do -- what is the output of:
ndiswrapper -v

---

### Post by plinydogg on 2007-06-09
kevdog: regardless of whether or not I get this working in the end, I really appreciate you (and others who have tried) attempting to help. I DO want to stay with Ubuntu...I really do!

By asking for me to paste my lspci results, I think you're trying to find out is this: 14e4:4318

If I'm wrong, here's my lspci results:

[HTML]00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)[/HTML]

Here is the contents of my /etc/iftab file:

[HTML]# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:d4:09:f2:23 arp 1
eth1 mac 00:14:a5:a8:f7:35 arp 1[/HTML]

Here is the result of uname -r:

[HTML]2.6.20-15-generic[/HTML]

ndiswrapper -v says that ndiswrapper is not installed, which is correct because I did a clean install yesterday and attempted the bcm43xx-fwcutter method one more time. 

As far as Internet goes, I have access to it via Vista (I dual boot with Ubuntu) and I have a USB key. I have no Internet connection in Ubuntu because wireless obviously doesn't work and for some other strange reason Ethernet doesn't work either (both work in Vista). 

Thanks!

---

### Post by kevdog on 2007-06-09
Before you tell me, Im guessing you have a linksys card -- WPC54G???

Anyway the chipset in your card is:
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Basically a broadcom rev02 chipset

Do you have a wired ethernet port on your computer??? Your /etc/iftab lists eth0 and eth1.  If you flip over your wireless card, you should probably see the MAC address on the back.  Match this up to either eth0 or eth1 in /etc/iftab and tell me the results.

To the best of my knowledge broadcom rev 02 chipset only will install with ndiswrapper (someone correct me if this is wrong).

Your kernel is  2.6.20-15-generic, or Im going to refer to it as the version 15 (v15) kernel.

Ok, sorry this post isnt really going to help you (this one Im writing), I just need a bit more info.  
Please post the results of:
lspci -n

Also did you install from Ubuntu Live CD or alternate CD??
Are you running Edgy or Feisty??

Hope you have your install CD available, because we are just about ready to get things going.

---

### Post by plinydogg on 2007-06-09
Thanks kevdog. Here's the results of lspci -n:

[HTML]00:00.0 0600: 1002:5950 (rev 01)
00:01.0 0604: 1002:5a3f
00:05.0 0604: 1002:5a37
00:13.0 0c03: 1002:4374
00:13.1 0c03: 1002:4375
00:13.2 0c03: 1002:4373
00:14.0 0c05: 1002:4372 (rev 11)
00:14.1 0101: 1002:4376
00:14.3 0601: 1002:4377
00:14.4 0604: 1002:4371
00:14.5 0401: 1002:4370 (rev 02)
00:14.6 0703: 1002:4378 (rev 02)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:05.0 0300: 1002:5955
06:02.0 0280: 14e4:4318 (rev 02)
06:04.0 0607: 104c:8031
06:04.2 0c00: 104c:8032
06:04.3 0180: 104c:8033
06:04.4 0805: 104c:8034
06:06.0 0200: 10ec:8139 (rev 10)[/HTML]

To answer your other questions, my card is listed as simply a broadcom card (there is no other brand name associated with it). It is actually an internal card. 

Yes, I have Ethernet connection but it doesn't work in Ubuntu. The alias for the wireless card is eth1. I was able to figure this out by using sudo lshw. 

I am running Feisty and I installed it using the LiveCD, which I have handy. 

Thanks!

---

### Post by kevdog on 2007-06-09
Ok, first thing, lets get ndiswrapper installed, not just downloaded.  Im going to use the ndiswrapper package that I believe comes on the installation cd.  Pop in the installation CD and let everything settle down. Then

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper

After doing all of this check if it was installed:

ndiswrapper -v

Hopefully you dont get any error messages.

Hopefully everthing is good up to this point -- I dont see why it shouldnt be.  Next lets download the driver.  I didnt know you were working with internal card -- it seems almost like my linksys card.

Ok here is the download link for your driver for your card -- its an .exe file  
[ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
Just for clarity place this file in ~/broadcom folder


Ok the .exe file is for windows.  In order to extract the driver you need the cab extract utility.

sudo aptitude install cabextract

I hope the above command works, if not let me know! (I hope cabextract is located on the cd!)

Then extract wireless driver:

cd ~/broadcom
cabextract xxxx.exe 

Substitute name of exe file above.  

Once files are extracted please refer to my previous post on how to install.  I think it was pretty thorough.

---

### Post by louistan3 on 2007-06-09
i remember installing ubuntu on my sisters hp tablet hybrid a few months back.. 

she also has a broadcom wireless.. not sure which one.. but im sure its new...

anyway.. i used the fwcutter method to install it and it works perfect... aside from

it not auto connecting on bootup.. 

i hope you get yours to work.. cause i only got hers working after a few tries.. 

goodluck! :)

---

### Post by plinydogg on 2007-06-09
kevdog: I did as you suggested but when I ran

sudo aptitude update 

I got a bunch of errors relating to the fact that I couldn't connect to the Internet. And afterwards, when I tried to install ndiswrapper (with sudo aptitutde install ndiswrapper) it couldn't find any ndiswrapper to install. 

Is there a way to get around this problem? 

Thanks!

louistan3: thanks for the well wishes! I wish bcm43xx-fwcutter worked for me too :(

---

### Post by kevdog on 2007-06-09
Did you add the cd to the repository??

I know that you dont have an internet connection,  but I think it should give you an error for every repository or site listed in the /etc/network/sources.list until it reaches the line with the cd.  It should then look for the repository from there.

Is the ubuntu cd in the drive??

What does your sources.list say???

---

### Post by plinydogg on 2007-06-09
The Ubuntu cd is in the drive. The cd was added to the repository (with sudo apt-cdrom add). I got an error for each website it tried to access with the sudo aptitude update command. Every error thing began with [http://.](http://.) I'll check what my sources.list says in a few minutes and post it back here. Thanks!

---

### Post by kevdog on 2007-06-09
Ok -- Ive never done this first part before so just hang with me, everything else however I can confirm.

One post I read said the ndiswrapper package is not on the cd, but build essential package is.  This will allow us to compile the sources.  I think you have the ndiswrapper sources

So lets do this:

sudo aptitude install build-essential

Then go into the directory where you unzipped the ndiswrapper package. Then do this:
sudo make uninstall
sudo make (this may take a minute or so)
sudo make install

Cross your fingers. Type
ndiswrapper -v

If youve gotten this far, smile :)

---

### Post by plinydogg on 2007-06-09
Thanks kevdog. One question, when you say go to the directory where you put ndiswrapper, I'm a little confused because I don't have ndiswrapper yet (we were hoping it was on the install cd but it wasn't). Am I missing something? 

THANKS!

---

### Post by kevdog on 2007-06-09
Damn, your right.  Im getting my different posts mixed up.  Ok here is the tarball for the ndiswrapper.
[http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.46.tar.gz?modtime=1180919462&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.46.tar.gz?modtime=1180919462&big_mirror=0)

Unzip with:
tar -zxvf ndiswrapper-version.tar.gz

This will create the ndiswrapper-version directory. Change to that directory with
cd ndiswrapper-version

Good luck

---

### Post by plinydogg on 2007-06-09
No prob. Thanks kevdog. I'll try that and get back to you. THANKS!

---

### Post by plinydogg on 2007-06-09
Alright kevdog...I think everything went fine. Here is what ndiswrapper -v returns:

[HTML]module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.46
vermagic:       2.6.20-15-generic SMP mod_unload 586 
ben@ben-ubuntu:~/Desktop/ndiswrapper-1.46$ 
[/HTML]

---

### Post by kevdog on 2007-06-10
Success, alright one major hurdle cleared.

Ok next step for you (please refer to previous posts) -- 
1. Untar the driver
2. Use the cabextract utility to pull the files out of the exe file 
3. Wrap the ndiswrapper around the windows driver (a few posts ago)
In the directory where the driver is unzipped and cab extracted, issue command similar to following:
ndiswrapper -i *****.inf

To see if command was successful:
ndiswrapper -l


The only potential problem from here on in is if the cabextract utility isnt on the LiveCD.  Im not sure if it is or not.  Try:
sudo aptitude install cabextract

If you get a bunch of errors: get the package here:
(This is assuming you are not installing with a 64 bit processor -- sorry if I took the liberty of assuming):
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fc%2Fcabextract%2Fcabextract_1.2-2_i386.deb&md5sum=b9f48e133c4d2a522178c03590b8ad29&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fc%2Fcabextract%2Fcabextract_1.2-2_i386.deb&md5sum=b9f48e133c4d2a522178c03590b8ad29&arch=i386&type=main)

You can install the package with following command:
sudo dpkg -i cabextract.deb
(Again substitute cabextract.deb for the real name of the package).

Proceed as instructed above!

If we get past this step it should be downhill from here!

---

### Post by plinydogg on 2007-06-10
kevdog: I think everything went right. Here's my ndiswrapper -l:

[HTML]bcmwl5 : driver installed
 device (14E4:4318) present (alternate driver: bcm43xx)[/HTML]

---

### Post by dmizer on 2007-06-10
think i might be able to finish things off for ya.

remove the non-working native driver module:
```
sudo modprobe -r bcm43xx
```
make it permanent by adding the following line to /etc/modprobe.d/blacklist (sudo gedit):
```
blacklist bcm43xx
```
add the ndiswrapper to the module list:
```
sudo modprobe ndiswrapper
```
and finally make ndiswapper add to the modules list on reboot by adding the following line to /etc/modules (sudo gedit):
```
ndiswrapper
```

see if that allows you to see your wireless card in network manager, or in system > adminstration > networking

edit:
please note, that the above changes can easily be undone by removing the edited lines from the two files, so if it does not work you shouldn't find yourself needing to reinstall from scratch just to undo the changes.

---

### Post by plinydogg on 2007-06-10
Thanks for the help dmizer but I'm afraid it didn't work. I did everything you suggested and then rebooted but the card is not listed in system->administration->networking. To confirm this I typed iwconfig in the terminal and my wireless card's alias (eth1) wasn't listed. 

This is similar to the experience I had before kevdog and you started to help me. That is, I could install ndiswrapper and get a driver wrapped but wireless still wouldn't work and my wireless card was no longer recognized once I blacklisted bcm43xx.

---

### Post by plinydogg on 2007-06-10
kevdog: is there a chance that we're trying to use the wrong driver? That's the only thing I can think of...

---

### Post by lsutiger on 2007-06-10
[Try this.]("http://ubuntu1501.blogspot.com/2007/05/another-way-to-get-wi-fi-on-dell-1501.html")..took me all of 3-4 minutes and worked for me. I had similar problems with the same exact card, but got it working.
 You WILL need an internet connection to get this working, so go grab your ethernet cable! Good Luck!

---

### Post by plinydogg on 2007-06-10
lsutiger: thanks for the tip. That looks like a handy guide. I think I'm going to wait to see if kevdog and/or dmizer  have any more thoughts about getting it to work with ndiswrapper before I try to follow your bcm43xx-based method because I've already come so far with ndiswrapper. If in the end I can't get the ndiswrapper way to work, then I will try the link you suggested. THANKS for posting it!

---

### Post by kevdog on 2007-06-10
Ok it seems you've made some progress.

ndiswrapper by default installs the interface as wlan0 and not eth1.  That means you have to change everything from eth1 to wlan0.

Here is how to do that

1. Modify /etc/iftab -- If there is an eth1 line in the file, change eth1 to wlan0
2. Modify /etc/network/interfaces - If there is any reference to eth1, change to wlan0
3. Did you up the ndiswrapper script to start when wlan0 is started??
sudo ndiswrapper -m
The command will make a /etc/modprobe.d/ndiswrapper file.  Take a look at it if you want.

Reboot -- I think you are really close!

---

### Post by plinydogg on 2007-06-10
kevdog: what do you mean when you ask:

"Did you up the ndiswrapper script to start when wlan0 is started?"

Thanks!

---

### Post by kevdog on 2007-06-10
Sorry, I guess that makes no sense.  Basically did you ever issue command
sudo ndiswrapper -m

Reboot computer, then
sudo /etc/init.d/networking restart

Then give me output of ifconfig.

Please ensure that you are using no encryption on your router or MAC filtering.  We can deal with this later.

If you have problems, please post following:
ifconfig
/etc/network/interfaces
/etc/iftab
/etc/modprobe.d/ndiswrapper

---

### Post by ind on 2007-06-10
I agree with the original post 100%.

I was excited to try Ubuntu. Initial install went excellent, and the OS detected all the hardware and assigned drivers as necessary. Once I was up and running however, I found myself disappointed that the wireless was not working. 

I spent a couple days trying various tips/tricks found online... and nothing works.

FYI - I'm using a Dell Inspiron 1100 with a Linksys WPC54G wireless PCI card.


I really want this to "Just Work" for me... cmon team

---

### Post by ind on 2007-06-10
Quick note:
I discovered that the card is not supported 'out of the box' as per the following list of supported wireless cards:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)
My card: WPC54G (ver 1.2)

There is a fix mentioned on the right side of the page, and it asks to update some firmware. It points to this URL which is currently down:
[http://bcm43xx.spugna.org/index.php?topic=29.0](http://bcm43xx.spugna.org/index.php?topic=29.0)


Does anyone know what firmware they are talking about, and how can I update it?

---

### Post by plinydogg on 2007-06-10
kevdog: I did as you said. Specifically, I went into /etc/iftab and changed the reference to eth1 to wlan0. I went to do the same in /etc/network/interfaces but there was no mention of eth1 in it so I didn't have to do anything. Then, I typed in sudo ndiswrapper -m and rebooted. 

After rebooting, I typed sudo /etc/init.d/networking restart but got some errors. Here's what it said:

[HTML] Reconfiguring network interfaces...                                          eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
[/HTML]

Here is the contents of ifconfig and iwconfig:

[HTML]ben@ben-ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

ben@ben-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.[/HTML]

Here's the contents of /etc/network/interfaces:

[HTML]auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp[/HTML]

Here's /etc/iftab:

[HTML]# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:d4:09:f2:23 arp 1
wlan0 mac 00:14:a5:a8:f7:35 arp 1[/HTML]

Here's /etc/modprobe.d/ndiswrapper:

[HTML]alias wlan0 ndiswrapper[/HTML]

THANK YOU!

---

### Post by plinydogg on 2007-06-10
Oh, I forgot to mention. I have WPA security on the router. I know that there are other issues with WPA (and that I'll probably need wpasupplicant or something like that) but it's not my router and I can't mess with it. I should still be able to tell if wireless is working though, right?, because I should be able to see the network just not log onto it......and don't worry.....I'll try to figure out the WPA thing on my own :)

---

### Post by kevdog on 2007-06-10
Please edit /etc/network/interfaces file, and put a # sign in front of any line (except blank lines) that do not contain either lo, eth0, or wlan0.

---

### Post by plinydogg on 2007-06-10
ind: I wish I could help you getting your wireless working but, as you can see, my advice wouldn't be very helpful to you at this point I'm afraid. I can promise you this, though. If I get mine finely working I'll do my best to give back to the community by helping others getting there's working (assuming that I have at least a vague idea of what I'm talking about by then). 

What I can tell you for certain is that as far as Ubuntu is concerned, the brand of a particular wireless card isn't what is crucial. What really matters is what chipset your wireless adapter uses. Do you know what chipset your card has?

---

### Post by plinydogg on 2007-06-10
kevdog: will do. Should I then reboot? or try to restart the networking again?

THANKS!

---

### Post by kevdog on 2007-06-10
Hmmm, as far as the WPA thing, we will get that working.  Are you sure you cant turn off WPA on the router for now.  Its going to make it difficult to troubleshoot if you dont, possibly we can get by with it.

What happens when you make your interfaces file look like the following:

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet dhcp

---

### Post by kevdog on 2007-06-10
Reboot!!!

---

### Post by darth_indy on 2007-06-10
To ind - I've got the WPC54G card, and I was confused at first in the supported wifi cards section, because it lists a few different versions of the card. I have ver. 3, but it lists five different versions of the WPC54G card. Make sure you're following the directions for the right card - I almost screwed up my computer big time!

---

### Post by plinydogg on 2007-06-10
kevdog: I made /etc/network/interfaces look almost like you suggested. Here's what it looked like:

[HTML]auto lo
iface lo inet loopback


#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp[/HTML]

I rebooted and then ran /etc/init.d/networking/restart and got this:

[HTML] * Reconfiguring network interfaces...                                          wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.[/HTML]

I will make the /etc/network/interfaces identical to what you said and then repeat the process and see if that helps. 

As far as the WPA goes, I would make the others that use this router pretty P.O.ed if I made ANY changes to it, but like I said, I won't take up your time trying to work around the WPA....hope that's not too much of a problem :(

---

### Post by dmizer on 2007-06-10
also post the contents of dmesg and the contents of lsmod please.

---

### Post by plinydogg on 2007-06-10
Alright, I changed the /etc/network/interfaces to what you suggested (all I had to do was add one line) and then ran sudo /etc/init.d/networking restart and got the following:

[HTML]ben@ben-ubuntu:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5109
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:d4:09:f2:23
Sending on   LPF/eth0/00:16:d4:09:f2:23
Sending on   Socket/fallback
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
SIOCSIFFLAGS: Function not implemented
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: Function not implemented
SIOCSIFFLAGS: Function not implemented
Listening on LPF/eth0/00:16:d4:09:f2:23
Sending on   LPF/eth0/00:16:d4:09:f2:23
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: Network is down
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
[/HTML]

---

### Post by plinydogg on 2007-06-10
dmizer: here is my lsmod:

[HTML]Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
af_packet              23816  0 
nls_utf8                3072  1 
ntfs                  107764  1 
ndiswrapper           185820  0 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
sg                     36252  0 
joydev                 10816  0 
snd_atiixp             20620  1 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
sd_mod                 23428  2 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
pcmcia                 39212  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ipaq                   34456  0 
snd_atiixp_modem       17160  0 
snd_ac97_codec         98336  2 snd_atiixp,snd_atiixp_modem
sdhci                  18700  0 
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usbserial              32488  1 ipaq
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              23684  2 snd_seq,snd_pcm
lmpcm_usb               7040  0 
pcspkr                  4224  0 
mmc_core               26756  1 sdhci
serio_raw               7940  0 
snd                    54020  13 snd_atiixp,snd_seq_oss,snd_rawmidi,snd_seq,snd_atiixp_modem,snd_ac97_codec,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               8672  1 snd
i2c_piix4               9740  0 
tifm_7xx1              10240  0 
tifm_core               9856  1 tifm_7xx1
psmouse                38920  0 
k8temp                  6656  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
ati_agp                10124  0 
agpgart                35400  1 ati_agp
snd_page_alloc         10888  3 snd_atiixp,snd_atiixp_modem,snd_pcm
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
i2c_core               22784  1 i2c_piix4
evdev                  11008  2 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_disk               17024  4 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ata_generic             9092  0 
libata                125720  1 ata_generic
generic                 5124  0 [permanent]
usbhid                 26592  0 
hid                    27392  1 usbhid
usb_storage            72256  1 
scsi_mod              142348  5 sbp2,sg,sd_mod,libata,usb_storage
libusual               17936  1 usb_storage
8139too                27648  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
atiixp                  7440  0 [permanent]
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  10 ndiswrapper,ipaq,usbserial,lmpcm_usb,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
[/HTML]

Here is dmesg:

[HTML]ben@ben-ubuntu:~$ sudo dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d0000 size: 0000000000030000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fda0000 end: 000000003fea0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fea0000 size: 000000000000c000 end: 000000003feac000 type: 3
[    0.000000] copy_e820_map() start: 000000003feac000 size: 0000000000054000 end: 000000003ff00000 type: 4
[    0.000000] copy_e820_map() start: 000000003ff00000 size: 0000000000100000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fea0000 (usable)
[    0.000000]  BIOS-e820: 000000003fea0000 - 000000003feac000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003feac000 - 000000003ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7c50
[    0.000000] Entering add_active_range(0, 0, 261792) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261792
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261792
[    0.000000] On node 0 totalpages: 261792
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32163 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID:          Product ID:              APIC at: 0xFEE00000
[    0.000000] Processor #0 15:4 APIC version 16
[    0.000000] I/O APIC #1 Version 33 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1791.038 MHz processor.
[    8.057841] Built 1 zonelists.  Total pages: 259747
[    8.057845] Kernel command line: root=UUID=f15e423b-4900-4897-8e67-a94c9593a5ac ro quiet splash linux acpi=off
[    8.057998] mapped APIC to ffffd000 (fee00000)
[    8.058001] mapped IOAPIC to ffffc000 (fec00000)
[    8.058004] Enabling fast FPU save and restore... done.
[    8.058007] Enabling unmasked SIMD FPU exception support... done.
[    8.058017] Initializing CPU#0
[    8.058086] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    8.059024] Console: colour VGA+ 80x25
[    8.059633] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.060141] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.081930] Memory: 1026716k/1047168k available (1992k kernel code, 19684k reserved, 893k data, 328k init, 129664k highmem)
[    8.081940] virtual kernel memory layout:
[    8.081941]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    8.081943]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.081944]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.081945]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.081947]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[    8.081948]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[    8.081949]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[    8.081952] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.157960] Calibrating delay using timer specific routine.. 3585.53 BogoMIPS (lpj=7171063)
[    8.158000] Security Framework v1.0.0 initialized
[    8.158007] SELinux:  Disabled at boot.
[    8.158022] Mount-cache hash table entries: 512
[    8.158163] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[    8.158171] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    8.158174] CPU: L2 Cache: 1024K (64 bytes/line)
[    8.158177] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[    8.158189] Compat vDSO mapped to ffffe000.
[    8.158194] Remapping vsyscall page to ffffe000
[    8.158204] Checking 'hlt' instruction... OK.
[    8.174095] SMP alternatives: switching to UP code
[    8.174376] Freeing SMP alternatives: 11k freed
[    8.174593] Early unpacking initramfs... done
[    8.497246] CPU0: AMD Turion(tm) 64 Mobile Technology ML-34 stepping 02
[    8.497266] Total of 1 processors activated (3585.53 BogoMIPS).
[    8.497348] ExtINT not setup in hardware but reported by MP table
[    8.497436] ENABLING IO-APIC IRQs
[    8.497630] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=0 pin2=2
[    8.641342] Brought up 1 CPUs
[    8.641536] Booting paravirtualized kernel on bare hardware
[    8.641618] Time: 18:26:21  Date: 05/10/107
[    8.641641] NET: Registered protocol family 16
[    8.641712] EISA bus registered
[    8.641829] PCI: PCI BIOS revision 2.10 entry at 0xfd86c, last bus=8
[    8.641831] PCI: Using configuration type 1
[    8.641833] Setting up standard PCI resources
[    8.642446] ACPI: Interpreter disabled.
[    8.642450] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.642456] pnp: PnP ACPI: disabled
[    8.642459] PnPBIOS: Scanning system for PnP BIOS support...
[    8.642465] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7c60
[    8.642468] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbc01, dseg 0x400
[    8.642909] PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
[    8.642943] PCI: Probing PCI hardware
[    8.642948] PCI: Probing PCI hardware (bus 00)
[    8.643744] Boot video device is 0000:01:05.0
[    8.644387] PCI: Transparent bridge - 0000:00:14.4
[    8.645336] PCI->APIC IRQ transform: 0000:00:13.0[A] -> IRQ 19
[    8.645341] PCI->APIC IRQ transform: 0000:00:13.1[A] -> IRQ 19
[    8.645345] PCI->APIC IRQ transform: 0000:00:13.2[A] -> IRQ 19
[    8.645350] PCI->APIC IRQ transform: 0000:00:14.1[A] -> IRQ 16
[    8.645357] PCI->APIC IRQ transform: 0000:00:14.5[B] -> IRQ 17
[    8.645361] PCI->APIC IRQ transform: 0000:00:14.6[B] -> IRQ 17
[    8.645365] PCI->APIC IRQ transform: 0000:01:05.0[A] -> IRQ 17
[    8.645370] PCI->APIC IRQ transform: 0000:06:02.0[A] -> IRQ 0
[    8.645375] PCI->APIC IRQ transform: 0000:06:04.0[A] -> IRQ 154
[    8.645379] PCI->APIC IRQ transform: 0000:06:04.2[C] -> IRQ 5
[    8.645384] PCI->APIC IRQ transform: 0000:06:04.3[B] -> IRQ 154
[    8.645389] PCI->APIC IRQ transform: 0000:06:04.4[A] -> IRQ 154
[    8.645393] PCI->APIC IRQ transform: 0000:06:06.0[A] -> IRQ 124
[    8.645397] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[    8.645399] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[    8.669746] NET: Registered protocol family 8
[    8.669748] NET: Registered protocol family 20
[    8.669785] pnp: 00:00: ioport range 0x1080-0x1080 has been reserved
[    8.669794] pnp: 00:0a: ioport range 0xf40-0xf41 has been reserved
[    8.669801] pnp: 00:0e: ioport range 0x40b-0x40b has been reserved
[    8.669804] pnp: 00:0e: ioport range 0x4d6-0x4d6 has been reserved
[    8.669807] pnp: 00:0e: ioport range 0x4d0-0x4d1 has been reserved
[    8.669810] pnp: 00:0e: ioport range 0xc00-0xc01 has been reserved
[    8.669813] pnp: 00:0e: ioport range 0xc14-0xc14 has been reserved
[    8.669815] pnp: 00:0e: ioport range 0xc50-0xc51 has been reserved
[    8.669818] pnp: 00:0e: ioport range 0xc52-0xc52 has been reserved
[    8.670042] PCI: Bridge: 0000:00:01.0
[    8.670045]   IO window: 9000-9fff
[    8.670048]   MEM window: c0100000-c01fffff
[    8.670051]   PREFETCH window: c8000000-cfffffff
[    8.670054] PCI: Bridge: 0000:00:05.0
[    8.670055]   IO window: disabled.
[    8.670057]   MEM window: disabled.
[    8.670060]   PREFETCH window: disabled.
[    8.670065] PCI: Bus 7, cardbus bridge: 0000:06:04.0
[    8.670067]   IO window: 0000a400-0000a4ff
[    8.670073]   IO window: 0000a800-0000a8ff
[    8.670078]   PREFETCH window: 50000000-53ffffff
[    8.670084]   MEM window: 54000000-57ffffff
[    8.670090] PCI: Bridge: 0000:00:14.4
[    8.670093]   IO window: a000-afff
[    8.670100]   MEM window: c0200000-c02fffff
[    8.670105]   PREFETCH window: 50000000-53ffffff
[    8.670122] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    8.670169] NET: Registered protocol family 2
[    8.701289] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.701443] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    8.702547] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    8.703097] TCP: Hash tables configured (established 131072 bind 65536)
[    8.703100] TCP reno registered
[    8.713343] checking if image is initramfs... it is
[    9.347879] Freeing initrd memory: 7003k freed
[    9.348285] audit: initializing netlink socket (disabled)
[    9.348297] audit(1181499981.372:1): initialized
[    9.348366] highmem bounce pool size: 64 pages
[    9.348427] VFS: Disk quotas dquot_6.5.1
[    9.348444] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.348495] io scheduler noop registered
[    9.348498] io scheduler anticipatory registered
[    9.348500] io scheduler deadline registered
[    9.348512] io scheduler cfq registered (default)
[   10.003638] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   10.003659] assign_interrupt_mode Found MSI capability
[   10.003662] Allocate Port Service[0000:00:05.0:pcie00]
[   10.003757] isapnp: Scanning for PnP cards...
[   10.357859] isapnp: No Plug & Play device found
[   10.378480] Real Time Clock Driver v1.12ac
[   10.378536] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.379174] mice: PS/2 mouse device common for all mice
[   10.379601] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.379800] input: Macintosh mouse button emulation as /class/input/input0
[   10.379827] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   10.379830] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   10.380083] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[   10.380086] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   10.401392] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.401396] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.402681] EISA: Probing bus 0 at eisa.0
[   10.402689] Cannot allocate resource for EISA slot 1
[   10.402718] Cannot allocate resource for EISA slot 8
[   10.402720] EISA: Detected 0 cards.
[   10.402788] TCP cubic registered
[   10.402797] NET: Registered protocol family 1
[   10.402816] Using IPI No-Shortcut mode
[   10.402836]   Magic number: 11:35:443
[   10.402926] Time: tsc clocksource has been installed.
[   10.403323] Freeing unused kernel memory: 328k freed
[   10.416247] input: AT Translated Set 2 keyboard as /class/input/input1
[   11.636787] Capability LSM initialized
[   11.689614] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   12.149633] usbcore: registered new interface driver usbfs
[   12.149654] usbcore: registered new interface driver hub
[   12.149674] usbcore: registered new device driver usb
[   12.177425] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   12.177492] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   12.177677] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   12.177699] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[   12.252484] ieee1394: Initialized config rom entry `ip1394'
[   12.276934] usb usb1: configuration #1 chosen from 1 choice
[   12.276958] hub 1-0:1.0: USB hub found
[   12.276972] hub 1-0:1.0: 4 ports detected
[   12.293647] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   12.380442] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   12.380466] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[   12.380525] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[   12.380538] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.380617] usb usb2: configuration #1 chosen from 1 choice
[   12.380642] hub 2-0:1.0: USB hub found
[   12.380651] hub 2-0:1.0: 8 ports detected
[   12.534269] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   12.534292] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[   12.534309] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[   12.537479] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[c0209000-c02097ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   12.592088] usb usb3: configuration #1 chosen from 1 choice
[   12.592111] hub 3-0:1.0: USB hub found
[   12.592124] hub 3-0:1.0: 4 ports detected
[   12.697550] 8139cp 0000:06:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   12.697554] 8139cp 0000:06:06.0: Try the "8139too" driver instead.
[   12.699543] 8139too Fast Ethernet driver 0.9.28
[   12.700267] eth0: RealTek RTL8139 at 0xf8828400, 00:16:d4:09:f2:23, IRQ 124
[   12.700269] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   12.700487] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   12.700507] ATIIXP: chipset revision 0
[   12.700510] ATIIXP: not 100% native mode: will probe irqs later
[   12.700519]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   12.700535]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   12.700547] Probing IDE interface ide0...
[   12.803708] usb 2-1: new high speed USB device using ehci_hcd and address 2
[   12.948115] usb 2-1: configuration #1 chosen from 1 choice
[   12.987906] hda: ST98823A, ATA DISK drive
[   13.618604] usb 3-2: new full speed USB device using ohci_hcd and address 2
[   13.659268] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   13.659399] Probing IDE interface ide1...
[   13.825536] usb 3-2: configuration #1 chosen from 1 choice
[   14.129916] usb 3-3: new low speed USB device using ohci_hcd and address 3
[   14.342907] usb 3-3: configuration #1 chosen from 1 choice
[   14.345588] usbcore: registered new interface driver libusual
[   14.352858] SCSI subsystem initialized
[   14.353937] Initializing USB Mass Storage driver...
[   14.354002] scsi0 : SCSI emulation for USB Mass Storage devices
[   14.354056] usbcore: registered new interface driver usb-storage
[   14.354059] USB Mass Storage support registered.
[   14.354132] usb-storage: device found at 2
[   14.354134] usb-storage: waiting for device to settle before scanning
[   14.365274] usbcore: registered new interface driver hiddev
[   14.377899] input: Logitech USB RECEIVER as /class/input/input2
[   14.377918] input: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:13.1-3
[   14.377931] usbcore: registered new interface driver usbhid
[   14.377935] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   14.394007] hdc: PIONEER DVDRW DVR-K16, ATAPI CD/DVD-ROM drive
[   15.065084] ide1 at 0x170-0x177,0x376 on irq 15
[   15.072128] libata version 2.20 loaded.
[   15.088980] hda: max request size: 128KiB
[   15.088986] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[   15.091050] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache, DMA
[   15.091057] Uniform CD-ROM driver Revision: 3.20
[   15.164413] hda: cache flushes supported
[   15.164445]  hda: hda1 hda2 hda3
[   15.525088] Attempting manual resume
[   15.525092] swsusp: Resume From Partition 3:3
[   15.525094] PM: Checking swsusp image.
[   15.525304] PM: Resume from disk failed.
[   15.559314] kjournald starting.  Commit interval 5 seconds
[   15.559324] EXT3-fs: mounted filesystem with ordered data mode.
[   19.347201] usb-storage: device scan complete
[   19.348193] scsi 0:0:0:0: Direct-Access     Crucial  Gizmo            1.13 PQ: 0 ANSI: 0 CCS
[   28.229865] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.234542] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.595481] Linux agpgart interface v0.102 (c) Dave Jones
[   28.630891] Yenta: CardBus bridge found at 0000:06:04.0 [103c:30a4]
[   28.630917] Yenta: Enabling burst memory read transactions
[   28.630924] Yenta: Using INTVAL to route CSC interrupts to PCI
[   28.630926] Yenta: Routing CardBus interrupts to ISA
[   28.630933] Yenta TI: socket 0000:06:04.0, mfunc 0x00a61b22, devctl 0x64
[   28.630940] Yenta: request_irq() in yenta_probe_cb_irq() failed!
[   28.630942] Yenta TI: socket 0000:06:04.0 no PCI interrupts. Fish. Please report.
[   28.630949] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[   28.630951] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[   28.759002] Yenta: ISA IRQ mask 0x0058, PCI irq 0
[   28.759008] Socket status: 30000006
[   28.759694] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   28.759698] cs: IO port probe 0xa000-0xafff: clean.
[   28.759963] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   28.759966] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   28.760273] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   28.760424] tifm_7xx1: probe of 0000:06:04.3 failed with error -38
[   29.170189] input: PC Speaker as /class/input/input3
[   29.237848] usbcore: registered new interface driver lmpcm_usb
[   29.237852] ubuntu/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   29.360892] usbcore: registered new interface driver usbserial
[   29.360915] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   29.374975] sdhci: Secure Digital Host Controller Interface driver
[   29.374978] sdhci: Copyright(c) Pierre Ossman
[   29.375023] sdhci: SDHCI controller found at 0000:06:04.4 [104c:8034] (rev 0)
[   29.375083] sdhci: probe of 0000:06:04.4 failed with error -38
[   29.406118] usbcore: registered new interface driver usbserial_generic
[   29.406123] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   29.417972] drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PDA
[   29.417975] drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
[   29.418009] ipaq 3-2:1.0: PocketPC PDA converter detected
[   29.419453] usb 3-2: PocketPC PDA converter now attached to ttyUSB0
[   29.419460] usbcore: registered new interface driver ipaq
[   29.434482] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   29.502294] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   29.517258] MC'97 0 converters and GPIO not ready (0x1)
[   29.720200] SCSI device sda: 252928 512-byte hdwr sectors (129 MB)
[   29.735053] sda: Write Protect is off
[   29.735058] sda: Mode Sense: 03 00 00 00
[   29.735060] sda: assuming drive cache: write through
[   29.764365] SCSI device sda: 252928 512-byte hdwr sectors (129 MB)
[   29.774009] sda: Write Protect is off
[   29.774013] sda: Mode Sense: 03 00 00 00
[   29.774016] sda: assuming drive cache: write through
[   29.774020]  sda: sda1
[   29.781126] sd 0:0:0:0: Attached scsi removable disk sda
[   29.799189] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.864202] cs: IO port probe 0x100-0x3af: clean.
[   29.866681] cs: IO port probe 0x3e0-0x4ff: clean.
[   29.867656] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   29.868482] cs: IO port probe 0xc00-0xcf7: excluding 0xc68-0xc6f 0xcd0-0xcdf
[   29.869329] cs: IO port probe 0xa00-0xaff: clean.
[   29.977191] fuse init (API version 7.8)
[   30.038039] lp: driver loaded but no devices found
[   30.208734] ndiswrapper version 1.46 loaded (smp=yes)
[   30.282634] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   30.282840] PCI->APIC IRQ transform: 0000:06:02.0[A] -> IRQ 0
[   30.291314] IRQ handler type mismatch for IRQ 0
[   30.291320] current handler: timer
[   30.291340]  [<c01540fe>] setup_irq+0x12e/0x1e0
[   30.291368]  [<f8dfaa00>] io_irq_isr+0x0/0x50 [ndiswrapper]
[   30.291406]  [<c0154253>] request_irq+0xa3/0xc0
[   30.291421]  [<f8dfb63f>] IoConnectInterrupt+0xcf/0x130 [ndiswrapper]
[   30.291448]  [<c016aeac>] map_vm_area+0xdc/0x160
[   30.291462]  [<f8df50f0>] NdisMRegisterInterrupt+0x100/0x1c0 [ndiswrapper]
[   30.291484]  [<f8df3780>] ndis_isr+0x0/0x90 [ndiswrapper]
[   30.291590]  [<f8e01114>] mp_init+0xa4/0x180 [ndiswrapper]
[   30.291628]  [<f8e01869>] NdisDispatchPnp+0xd9/0xda0 [ndiswrapper]
[   30.291674]  [<c0102236>] __switch_to+0xc6/0x1f0
[   30.291686]  [<c02f1334>] kprobe_flush_task+0x44/0x90
[   30.291700]  [<c02ecc15>] __sched_text_start+0x8d5/0xa90
[   30.291740]  [<f8dfb07b>] IoAllocateIrp+0x5b/0x80 [ndiswrapper]
[   30.291771]  [<f8dfb8f5>] IoBuildAsynchronousFsdRequest+0x35/0x170 [ndiswrapper]
[   30.291807]  [<f8dfacc5>] IofCallDriver+0x55/0xc0 [ndiswrapper]
[   30.291842]  [<f8dfd16b>] IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
[   30.291890]  [<f8dfd4c0>] pnp_start_device+0x50/0xb0 [ndiswrapper]
[   30.291942]  [<f8dfd703>] wrap_pnp_start_device+0x1e3/0x290 [ndiswrapper]
[   30.291992]  [<f8dfd7f5>] wrap_pnp_start_pci_device+0x45/0x50 [ndiswrapper]
[   30.292021]  [<c01b8005>] sysfs_dirent_exist+0x45/0x70
[   30.292037]  [<c01b8ede>] sysfs_create_link+0x6e/0x160
[   30.292050]  [<c01fb953>] pci_match_device+0x13/0xc0
[   30.292056]  [<f8dfd7b0>] wrap_pnp_start_pci_device+0x0/0x50 [ndiswrapper]
[   30.292080]  [<f8dfd7b0>] wrap_pnp_start_pci_device+0x0/0x50 [ndiswrapper]
[   30.292099]  [<c01fba76>] pci_device_probe+0x56/0x80
[   30.292109]  [<c0257a66>] really_probe+0x66/0x190
[   30.292117]  [<c0257bd9>] driver_probe_device+0x49/0xc0
[   30.292134]  [<c0257dae>] __driver_attach+0x9e/0xa0
[   30.292144]  [<c0256f3b>] bus_for_each_dev+0x3b/0x60
[   30.292161]  [<c0257904>] driver_attach+0x24/0x30
[   30.292165]  [<c0257d10>] __driver_attach+0x0/0xa0
[   30.292168]  [<c02572cb>] bus_add_driver+0x7b/0x1a0
[   30.292188]  [<c01fbc44>] __pci_register_driver+0x74/0xc0
[   30.292197]  [<f8df16b2>] loader_init+0x102/0x220 [ndiswrapper]
[   30.292219]  [<f8dfdb4f>] wrap_procfs_init+0x3f/0xb0 [ndiswrapper]
[   30.292244]  [<f881b0b5>] wrapper_init+0xb5/0xc2 [ndiswrapper]
[   30.292267]  [<c014421d>] sys_init_module+0x15d/0x1ba0
[   30.292359]  [<c0107a5d>] sys_mmap2+0xcd/0xd0
[   30.292378]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[   30.292415]  =======================
[   30.292432] ndiswrapper (IoConnectInterrupt:566): request for irq 0 failed
[   30.292435] ndiswrapper: request for IRQ 0 failed
[   30.295625] ndiswrapper (mp_init:261): couldn't initialize device: C000009A
[   30.295632] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   30.295647] ndiswrapper (mp_halt:303): device f7f63400 is not initialized - not halting
[   30.295659] ndiswrapper: device eth%d removed
[   30.295678] ndiswrapper: probe of 0000:06:02.0 failed with error -22
[   30.298847] usbcore: registered new interface driver ndiswrapper
[   30.328587] Adding 1951888k swap on /dev/disk/by-uuid/b5d290af-0cbe-402a-8e4b-3cb1b693a6c8.  Priority:-1 extents:1 across:1951888k
[   30.466108] EXT3 FS on hda2, internal journal
[   30.694085] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   30.739743] NTFS volume version 3.1.
[   32.049866] NET: Registered protocol family 17
[   32.690977] powernow_k8: Unknown symbol acpi_processor_notify_smm
[   32.691017] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[   32.691094] powernow_k8: Unknown symbol acpi_processor_register_performance
[   32.715819] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   32.715859] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   32.715949] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   32.715995] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   37.919826] ppdev: user-space parallel port driver
[   38.656069] apm: BIOS not found.
[   38.839969] Bluetooth: Core ver 2.11
[   38.840022] NET: Registered protocol family 31
[   38.840024] Bluetooth: HCI device and connection manager initialized
[   38.840028] Bluetooth: HCI socket layer initialized
[   38.873299] Bluetooth: L2CAP ver 2.8
[   38.873303] Bluetooth: L2CAP socket layer initialized
[   38.916642] Bluetooth: RFCOMM socket layer initialized
[   38.916656] Bluetooth: RFCOMM TTY layer initialized
[   38.916658] Bluetooth: RFCOMM ver 1.8
[   69.639449] NET: Registered protocol family 10
[   69.639541] lo: Disabled Privacy Extensions
[/HTML]

---

### Post by kevdog on 2007-06-10
Can you repost the following:  (All of this is troubling to me):

ndiswrapper -v
dmesg | grep ndiswrapper

---

### Post by dmizer on 2007-06-10
looks like you have an irq conflict.

try adding one more line to the /etc/modprobe.d/blacklist file as follows:
```
blacklist ochi_hcd
```

reboot, and retry.

---

### Post by plinydogg on 2007-06-10
kevdog: here is ndiswrapper -v:

[HTML]utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.46
vermagic:       2.6.20-15-generic SMP mod_unload 586 [/HTML]

Here is dmesg | grep ndiswrapper:

[HTML]ben@ben-ubuntu:~$ dmesg | grep ndiswrapper
[   30.666480] ndiswrapper version 1.46 loaded (smp=yes)
[   30.740384] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   30.749116]  [<f8e00a00>] io_irq_isr+0x0/0x50 [ndiswrapper]
[   30.749170]  [<f8e0163f>] IoConnectInterrupt+0xcf/0x130 [ndiswrapper]
[   30.749219]  [<f8dfb0f0>] NdisMRegisterInterrupt+0x100/0x1c0 [ndiswrapper]
[   30.749243]  [<f8df9780>] ndis_isr+0x0/0x90 [ndiswrapper]
[   30.749389]  [<f8e07114>] mp_init+0xa4/0x180 [ndiswrapper]
[   30.749437]  [<f8e07869>] NdisDispatchPnp+0xd9/0xda0 [ndiswrapper]
[   30.749589]  [<f8e0107b>] IoAllocateIrp+0x5b/0x80 [ndiswrapper]
[   30.749626]  [<f8e018f5>] IoBuildAsynchronousFsdRequest+0x35/0x170 [ndiswrapper]
[   30.749669]  [<f8e00cc5>] IofCallDriver+0x55/0xc0 [ndiswrapper]
[   30.749712]  [<f8e0316b>] IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
[   30.749773]  [<f8e034c0>] pnp_start_device+0x50/0xb0 [ndiswrapper]
[   30.749840]  [<f8e03703>] wrap_pnp_start_device+0x1e3/0x290 [ndiswrapper]
[   30.749905]  [<f8e037f5>] wrap_pnp_start_pci_device+0x45/0x50 [ndiswrapper]
[   30.749983]  [<f8e037b0>] wrap_pnp_start_pci_device+0x0/0x50 [ndiswrapper]
[   30.750009]  [<f8e037b0>] wrap_pnp_start_pci_device+0x0/0x50 [ndiswrapper]
[   30.750154]  [<f8df76b2>] loader_init+0x102/0x220 [ndiswrapper]
[   30.750178]  [<f8e03b4f>] wrap_procfs_init+0x3f/0xb0 [ndiswrapper]
[   30.750206]  [<f888e0b5>] wrapper_init+0xb5/0xc2 [ndiswrapper]
[   30.750454] ndiswrapper (IoConnectInterrupt:566): request for irq 0 failed
[   30.750457] ndiswrapper: request for IRQ 0 failed
[   30.753642] ndiswrapper (mp_init:261): couldn't initialize device: C000009A
[   30.753648] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   30.753663] ndiswrapper (mp_halt:303): device f7f5a400 is not initialized - not halting
[   30.753673] ndiswrapper: device eth%d removed
[   30.753693] ndiswrapper: probe of 0000:06:02.0 failed with error -22
[   30.756830] usbcore: registered new interface driver ndiswrapper
[/HTML]

---

### Post by plinydogg on 2007-06-10
dmizer: I'll do as you suggest and report back here.

dmizer and kevdog: I really can't thank you enough for all your help. Please don't feel obligated to keep helping me as you've already been more than generous with you time.

---

### Post by plinydogg on 2007-06-10
dmizer: I did as you suggested but nothing changed. The card is still not showing up in the network manager. 

Thanks though:)

---

### Post by dmizer on 2007-06-10
okay ... let's add a couple of kernel options to try to avoid that irq conflict.

first backup your grub like so:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```
now, if your computer won't boot after the changes, just use the live cd and move the menu.list-backup to menu.lst

find your most recent kernel line.  it should look something like this:
```
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
```
add "irqpoll" and "noapic" options to your kernel like so it looks something like this:
```
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash [COLOR="Red"]irqpoll noapic[/COLOR]
```

make sure that the kernel line doesn't wrap to a second line.  this will prevent your machine from booting.  everything should appear on the same line.

save ... reboot.  if you still have problems, please post the output of dmesg again.

---

### Post by plinydogg on 2007-06-10
I've gotta run right now. I'll try this first thing in the morning. THANKS to both of you for your ongoing help!

---

### Post by plinydogg on 2007-06-10
By the way, something just occurred to me: when you say "find your most recent kernel line" what do you mean? 

I've never messed with the kernel before.

---

### Post by plinydogg on 2007-06-10
I really am leaving (as soon as my fiance gets ready) but one more question. Everyone complains about how wireless doesn't work well in Ubuntu (me included, obviously!). Yet at the same time, we all know that a certain number of cards do work once the proper groundwork has been laid (e.g., ndiswrapper installed, etc.). 

My question is: while there's seemingly no magical out-of-the-box wireless card for feisty, is there a particular card that almost always works once ndiswrapper is set up and configured? I'm okay with the idea of purchasing a new card and by now I feel like installing and configuring ndiswrapper would be a piece of cake. In other words, would the problems I'm having prevent another card from working well with ndiswrapper? 

I'm not giving up with this broadcom4318 or anything...just want to know my options :)

---

### Post by dmizer on 2007-06-10
> **plinydogg said:**
> By the way, something just occurred to me: when you say "find your most recent kernel line" what do you mean? 

I've never messed with the kernel before.

well, in my grub there are several ... but you won't have that because you haven't upgraded yet.

when you look toward the bottom of menu.lst, you'll see a number of lines that will look *similar* to this:
```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-28-686
root            (hd0,0)
[COLOR="Red"]kernel          /boot/vmlinuz-2.6.15-28-686 root=/dev/hda1 ro quiet splash[/COLOR]
initrd          /boot/initrd.img-2.6.15-28-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-686 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-686 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-28-686
boot
```

the above is from dapper because it was handy, but the only difference you will see is in the kernel version number and maybe where your root partition is.  you should edit the line beginning with "kernel".  ignore the section below the title "(recovery mode)"

you're not really editing the "kernel" here, you're merely passing options to the kernel as it boots so that it knows how to handle your hardware.

enjoy your evening!

edit:
i've managed to get my linksys pcmcia wpc54g v.2 (acx111 chipset) card to work in every release since hoary.

---

### Post by kevdog on 2007-06-10
Sorry wasted post

---

### Post by plinydogg on 2007-06-11
Guess what?.....I'm posting this from within Ubuntu!!!!!!!! kevdog and dmizer: THANK YOU!!!!!!! and also......THANK YOU!!!!!!!! I guess after future fresh installs I need to just install ndiswrapper and drivers (the packages from kevdog) and then edit menu.lst as dmizer suggested. This sounds crazy but I may do a fresh install just to verify that I can repeat this process. 

This may be beyond the scope of this thread but how can I tell if someone has an IRQ conflict? The reason I ask is because others might be suffering from the same problem, and I wonder why it doesn't come up in Windows(?). 

Now that my wireless works I guess I need to revisit my original post. As the number of posts in this thread makes clear, wireless can be too difficult to get working in Ubuntu. But, to be fair, an IRQ conflict isn't a wireless problem per se (at least I don't think it is). And requiring a basic installation of ndiswrapper and drivers isn't all that cumberesome...once you know what you're doing. In other words, now that kevdog has walked me through the process of installing and configuring ndiswrapper (and pointed me towards the proper packages, drivers, etc.) I could repeat the process in a matter of mintues. But without that help, it can take literally days or even weeks for a newbie to figure ndiswrapper out and to track down the proper drivers. I guess what I'm saying is that something needs to be done to make wireless easier for newbies. 

I can't thank kevin and dmizer enough for their patience and perserverence. Thanks also to everyone who posted other tips and suggestions about how to get my card working.

---

### Post by dmizer on 2007-06-11
congrats!  glad we got you online.

as for the irq conflict, if you look carefully through your previously posted dmesg, you'll find it ... it happens toward the end of all the ndiswrapper junk like so:
```
[   30.292432] ndiswrapper (IoConnectInterrupt:566): request for irq 0 failed
[   30.292435] ndiswrapper: request for IRQ 0 failed
```
and yes, this is a kernel issue, not a hardware or driver issue.  in reality ... a bug should be filed against it.

you may ALSO find that after upgrading to the current kernel, that this problem goes away.

---

### Post by srilyk on 2007-06-11
Congrats about getting your card working! I also have a Broadcom chip in my laptop...

When I originally tried to get it working, I had installed Ubuntu 5 or 6ish, and tried getting it to work just d/ling some stuff using the Synaptic pkg manager... No dice...

well, then I upgraded my kernel... and VOILA! it worked!

Well, I screwed something up (I can't remember what) and had to reinstall... so I did that and upgraded, but it didn't work, so I went the ndiswrapper route, and that got it to work pretty quickly.

My only issue that I have is sometimes it won't connect just regularly to a WAP, usually when there's no webkey, I find what I have to do is run kwifimanger, search for networks, select the one I want (you have to click the WEP box part) and then click switch to network, and it will connect just fine that way... I'm not sure exactly why it does, but it works and that's good for me.

---

### Post by plinydogg on 2007-06-11
dmizer: thanks for the tip about where to look for IRQ conflicts. By the way, what exactly do "irqpoll" and "noapic" do? THANKS again!

---

### Post by plinydogg on 2007-06-11
srilyk: so you use Feisty now?

---

### Post by ts51 on 2007-06-11
> **plinydogg said:**
> Hi everyone,

I was really excited about learning Ubuntu and from the first moment I booted up the LiveCD I was very impressed. I had envisioned a steep learning curve initially but was anxious to learn as much as I could and eventually make Ubuntu my main OS. The community here was VERY supportive and I couldn't have gotten my dual-boot (with Vista) working without them (thank you again!). 

But the Internet (especially wireless) problems are just too much to bear. My fiance asked me the other day what I was working at so intently and I told her that apparently I had the most incompatible type of wifi card for Ubuntu (Broadcom bcm4318). After days and days of trying to get it work I just can't. I've tried every tutorial out there and tried to follow all sorts of tips that you people generously took the time to provide me with. And while I'm a linux newbie, I'm not stupid. I've used a command line before and even written some computer programs before. And I'm not one of those people who is looking for a different version of Windows. I want to use the command line to do stuff!

The fact that one type of wireless card doesn't work isn't that big of a deal. The thing that really got me down was that when I decided that I was willing to buy a new wireless card and went to look up which cards work the best in Feisty, I found absolutely no consensus! There is not a single wireless card that reliably works in Ubuntu 7.04! For each card and chipset, there are dozens of disagreements, tutorials, tips, problems, purported solutions, and the like. 

I'm not trying to be overly harsh, but how in all honesty can Ubuntu really be considered a viable alternative to the other OSes out there when there's not a single reliable way to get wireless working? That's just mind boggling to me. 

Add to that the fact that my Ethernet won't work in Feisty either! I don't know what the problem there is because (as is also the case with my wireless) it works fine in Vista. Having said that, I haven't really looked into the Ethernet issue as much and so maybe it's easily fixable (but that would surprise me). 

The final component of my gripe is that from what rudimentary tinkering I've done so far it seems like this OS isn't something that you can really explore without an Internet connection. There may be plenty of neat programs out there to do X or Y but in order to get them, you usually have to use apt-get or some other Internet-based solution. Thus, the sorry state of the wireless support (and ethernet support?) is just jaw dropping in its proportions. 

And aside from this excellent forum, there is no where else to turn for help (unless you want to shell out $250). The books out there on Ubuntu don't have the solution, nor does anyone at any retail outlet have a clue of what Ubuntu is, nor are there any Ubuntu user groups in my geographical area. I could probably put a classified ad in my paper saying "Get my wireless working in Ubuntu and I'll give you $10,000" and no one would respond. 

Like I said above, I really, really want to learn to use and love Ubuntu. That's why this is so disappointing. Perhaps even more sad is the fact that Ubuntu is "the" distribution out there right now, which is to say that there are a lot of people who have heard about it and are going to be trying it. And of those that do so, how many are going to be unable to get their wireless working and walk away from Ubuntu and put it out of their mind forever? That seems like a huge waste of potential lifelong supporters and contributors to this project.

Against this backdrop, the "it just works" slogan is just laughable. I know that part of the Ubuntu philosophy requires that proprietary drivers, etc. not be included in distributions but I mean, seriously, does anyone have a realistic idea when things are going to get better?

I feel the exact same way. Last year, I spent an unbelievable amount of time trying to get Ubuntu to work with my wireless card. If I could have gotten that to work, I would probably only be booting into windows to play games, and, maybe to use MS Office. 



-TS51

---

### Post by plinydogg on 2007-06-11
So, do you not use Ubuntu now?

---

### Post by plinydogg on 2007-06-11
Now that I've updated my kernel it would seem that I have run into the WPA issue.....here's to another journey :)

[Edit: after looking at some other threads, it looks like I'll be trying wicd...I'll report back here with my success or failure]

---

### Post by plinydogg on 2007-06-11
Wow! Ten minutes and I'm in business! Here's what I did if anyone has the same problem:

(1) Downloaded Wicd from here: [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)
(2) Uninstalled Network Manager in using Synaptic Package Manager
(3) Installed Wicd (by double clicking on it)
(4) Rebooted
(5) Started Wicd, entered my network's information and bam, I'm in business!

Actually, the first time I tried to connect using Wicd it didn't work. But I tried again a minute later and it worked. Fantastic!

---

### Post by lsutiger on 2007-06-11
Glad to hear you are up and running. As far as WPA is concerned, Network manager actually does a good job in Feisty. I would like to take a screen shot of it in use ( it has a dropdown menu with all of the wireless networks available), but I can't get a screenshot with the menu pulled down...Is there a keyboard shortcut for that???

And WELCOME TO THE WORLD OF UBUNTU! FREEDOM IS OUR COMMON CALL!

BTW - this post should be stikied somewhere. It shows how the community helped someone fix a genuine problem with Ubuntu and got in solved in what? 3 days? Most forums, in my experience, you don't get this much help. Mostly speculation and misinformation.

---

### Post by plinydogg on 2007-06-11
Thanks for the welcome lsutiger! I'm looking forward to exploring EVERYTHING in Ubuntu!!!!

I agree that this is a shining example of the help that people are willing to give. I hope I can help someone someday like all of you helped me. I think it's also a good example because I had a problem (IRQ conflict) that wasn't addressed in other threads, and if everyone would have just told me to shut up and looka t other threads then the problem never would have been solved. I'm really thankful for everyone's patience.

---

### Post by lsutiger on 2007-06-12
You are very welcome! I am a noob here myself, but have learned volumes within 5 months, I still have questions and they are usually answered here. The worst thing about  the forum is that there are so many questions getting posted by 'absolute beginners' in all of the rooms that a lot of posts get buried. But all in all, it is a community, and help is out there. I find myself, even being a noob, being able to help out a person here and there. There is some satisfaction that comes with that. 

You know, once you are part of this family, there's no getting out - Tony Soprano

hehe....fill in the blank for linux! :p

PS - do you gtalk? judelandry2002

---

### Post by wulfhound on 2007-06-12
Oh come on.

You would have the same problems with any OS. Just look at VISTA!

Just likes VISTA, Feisty is new. If you want stable, use XP or use Edgy Eft, with PLENTY of people's "concensus" on what works and what doesn't.

Stop whining about how much things don't work and use some common sense. It just recently came out, you have to give it time (just like VISTA, which by the way, makes boatloads of money).

When I go to the store I have to figure out what I want just like the next guy, and what will work. I'm just a little more than tired of people who can't do any research. I know you tried to find something that worked, but maybe you should have stayed with Edgy Eft then (or started out with it, as it were). Then you would have had the support you needed.

Having the latest greatest thing - isn't exactly the greatest, for newbies.

Eft is well supported and works with many peripherals and cards right out of the box.

Sandaili:(

---

### Post by wulfhound on 2007-06-12
> **plinydogg said:**
> Hi everyone,

I was really excited about learning Ubuntu and from the first moment I booted up the LiveCD I was very impressed. I had envisioned a steep learning curve initially but was anxious to learn as much as I could and eventually make Ubuntu my main OS. The community here was VERY supportive and I couldn't have gotten my dual-boot (with Vista) working without them (thank you again!). 

But the Internet (especially wireless) problems are just too much to bear. My fiance asked me the other day what I was working at so intently and I told her that apparently I had the most incompatible type of wifi card for Ubuntu (Broadcom bcm4318). After days and days of trying to get it work I just can't. I've tried every tutorial out there and tried to follow all sorts of tips that you people generously took the time to provide me with. And while I'm a linux newbie, I'm not stupid. I've used a command line before and even written some computer programs before. And I'm not one of those people who is looking for a different version of Windows. I want to use the command line to do stuff!

The fact that one type of wireless card doesn't work isn't that big of a deal. The thing that really got me down was that when I decided that I was willing to buy a new wireless card and went to look up which cards work the best in Feisty, I found absolutely no consensus! There is not a single wireless card that reliably works in Ubuntu 7.04! For each card and chipset, there are dozens of disagreements, tutorials, tips, problems, purported solutions, and the like. 

I'm not trying to be overly harsh, but how in all honesty can Ubuntu really be considered a viable alternative to the other OSes out there when there's not a single reliable way to get wireless working? That's just mind boggling to me. 

Add to that the fact that my Ethernet won't work in Feisty either! I don't know what the problem there is because (as is also the case with my wireless) it works fine in Vista. Having said that, I haven't really looked into the Ethernet issue as much and so maybe it's easily fixable (but that would surprise me). 

The final component of my gripe is that from what rudimentary tinkering I've done so far it seems like this OS isn't something that you can really explore without an Internet connection. There may be plenty of neat programs out there to do X or Y but in order to get them, you usually have to use apt-get or some other Internet-based solution. Thus, the sorry state of the wireless support (and ethernet support?) is just jaw dropping in its proportions. 

And aside from this excellent forum, there is no where else to turn for help (unless you want to shell out $250). The books out there on Ubuntu don't have the solution, nor does anyone at any retail outlet have a clue of what Ubuntu is, nor are there any Ubuntu user groups in my geographical area. I could probably put a classified ad in my paper saying "Get my wireless working in Ubuntu and I'll give you $10,000" and no one would respond. 

Like I said above, I really, really want to learn to use and love Ubuntu. That's why this is so disappointing. Perhaps even more sad is the fact that Ubuntu is "the" distribution out there right now, which is to say that there are a lot of people who have heard about it and are going to be trying it. And of those that do so, how many are going to be unable to get their wireless working and walk away from Ubuntu and put it out of their mind forever? That seems like a huge waste of potential lifelong supporters and contributors to this project.

Against this backdrop, the "it just works" slogan is just laughable. I know that part of the Ubuntu philosophy requires that proprietary drivers, etc. not be included in distributions but I mean, seriously, does anyone have a realistic idea when things are going to get better?


I forgot to add, apparently you have never had a problem with a driver not being found or not working suddenly in XP? That, my friend, IS laughable.

PS. I have had no problems with getting anything to work with Ubuntu "out of the box". You just expect perfection in a world where there is none when it comes to computers. If you want it "out of the box" I suggest buying a Dell that has Ubuntu on it. There ya go.

L=;

---

### Post by plinydogg on 2007-06-12
Sandaili:

Let me answer each of your charges in turn.

First, you say that a person would have the same problems with any OS and then point to Vista as an example. I'm not really sure what you're referring to here because I have never had any problems with Vista except for software compatibility issues. I'm no Microsoft lover or anything but your argument about stability doesn't really hold up: Vista is stable, despite any other inadequacies it may have. 

Secondly, you tell me to "stop whining about how much things don't work and use some common sense." Well I admit that I was doing a little whining in my original post, but this wasn't occurring in a vacuum. As the title of my post indicates, my whining was the result of the disparity between the way Ubuntu is presented (i.e., "it just works") and the experience I was having, and countless others have had. And I'm not sure how using "common sense" would change anything. The fact that something is new doesn't automatically require the conclusion that it is unstable, one need only look to Vista to prove that. 

Thirdly, as far as I your "when I go to the store I have to figure out what I want....I'm just a little tired of people who can't do any research" goes, I really resent it. Had you clearly read this thread, you would know that one of my first posts set forth the methods I had attempted to employ to get my wireless card working and a in my original post I lamented the fact that there was absolutely no consensus about which wireless cards worked in Feisty. Thus, I had not only done my research regarding getting my current card working I had also done my research regarding other cards that might work better. What omission in my research made you blurt out your exasperation with people "who can't do any research?"

Fourth, I'm not sure if I've had driver problems in XP before. I'm pretty sure I have. What of it?

Finally, your charge that I just "expect perfection in a world where there is none when it comes to computers" betrays the fact that you probably didn't do too well on reading comprehension exams. In the very first post I say that "I am not one of those people who is looking for a different version of Windows. I want to use the command line to do stuff!" Does that sound like the words of someone who is expecting perfection? With that one sentence alone I've acknowledged and embraced the fact that the Ubuntu experience will be different from the Windows experience and have also said that I am looking forward to diving in as far as the command line goes. Furthermore, the ten pages of this thread reveal that I am willing to do whatever it takes to get my wireless working. Suggestion after suggestion is offered to me and I try them all thankfully. Not once do I complain that what someone is suggesting to me is too hard or is not "perfect" enough for me. 

It's obvious to me that you didn't even read my original post carefully. It's also obvious to me that you didn't read the rest of this thread. I think I know why. Everytime you see someone complaining about something you probably just assume that whatever the person is complaining about has not merit whatsoever, that they didn't do their research, that they have no idea what they're talking about. You're probably right sometimes. 

I'm just glad that there's a number of people on this forum who don't think like you do, people who don't assume the poster is an idiot; who don't assume that the poster hasn't done his or her research; and  who are willing to actually help a newbie work through a problem. I might be a newbie but I can already tell that this is an amazingly supportive community. It's just a shame that the community also includes people like you.

---

### Post by ts51 on 2007-06-12
> **plinydogg said:**
> So, do you not use Ubuntu now?


Nope. I might try to dual boot Ubuntu with XP soon, though. I just need some exact instructions on dual booting, installing, and setting up wireless (one giant Ubuntu tutorial :D) 



-TS51

---

### Post by jglen490 on 2007-06-12
Congratulations plinydogg!!  You hung in there and got something going.  You also did one more thing, you provided a good stream of lessons that someone else might be able to at least relate to, and learn from.  Sorry 'bout using a preposition to end a sentence with; sometimes it's just easier :D !!

---

### Post by plinydogg on 2007-06-12
I dual boot with Vista and don't know how to dual boot with XP but I'm sure there are good tutorials around. Have you looked?

---

### Post by plinydogg on 2007-06-12
lsutiger: I don't know what gtalk is but I don't think I do it. It sounds like a chat application. If so, I haven't used a chat application since AIM drove me out of my mind :)

---

### Post by JerseyDevil1111 on 2007-06-12
I got the LAN wired connection working, so that's better than nothing.

---

### Post by plinydogg on 2007-06-12
JerseyDevil1111: I guess I'm in the opposite boat. My wireless works but my wired connection doesn't...come to think of it, I haven't checked my wired connection since I got my wireless working...

jglen490: Thanks...and ending your sentence with a preposition is something I can forgive you for . :) Ha! I ended with a preposition too.

---

### Post by lsutiger on 2007-06-12
JerseyDevil1111: List your hardware and let us help you get your wireless fixed!
plinydogg: Yes it is a chat thing. I really like it because you can only be invited by other members, who were invited before you. I never get spammed with gtalk. You should check out Google's gmail. Free, huge space, you can send HUGE attachments (up to 10 MB...but most ISP's will reject something that big) and well organized.
Anyhoo I am rattling....

---

### Post by JerseyDevil1111 on 2007-06-12
Problem with Intel card, too:[http://fedoraforum.org/forum/showthread.php?p=807431#post807431](http://fedoraforum.org/forum/showthread.php?p=807431#post807431)

Oh well, I'm outta here.

---

### Post by wsx123 on 2007-06-12
i'm only using linux for 3 days and 
i got my broadcom 4306 card working fine on an old IBM Thinkpad

all 
i did was search in these forums and do a little reading, trial and error. I f I plug in my wired ethernet cable my internet connection comes on right away. I had to work a little on wireless.

---

### Post by raul_ on 2007-06-12
Complain to the card manufacturers :)

---

### Post by NfF on 2007-06-14
yep. should be renamed "wireless never works in ubuntu."

im terribly dissappointed.ive posted 10 threads and no replies.
looks like ubuntu could stay at my failed software for now.

---

### Post by plinydogg on 2007-06-14
Well, what kind of card do you have?

---

### Post by Damanther on 2007-06-14
I wouldn't come down too hard on Ubuntu here.

I am willing to bet that if you looked into the various Microsoft and Windows PC dealer's help sites out there you would find an equal amount of people with issues about their wireless cards , printers, usb drives, etc. Especially in the Vista world.

But it sucks when its you with the problem no matter what the OS is. Believe me, I know.  I just got finished fighting a problem with my DVD drive in Kubuntu and I thought I was gonna loose it for a while there.

There are lots of helpful and smart folks out there to help though. (Wish I was one of them).

Good luck.

---

### Post by tiger's on 2007-06-20
What do you thing, when WiFi and WPA problems would be solved and work out-of-box in linux? Next Ubuntu release?

Why can't I use both wired and wireless interfaces? I'm a network engineer and it's my work :-)

---

### Post by tact on 2007-06-20
Is your computer a laptop?   Take it to the shop and tell them you want to plug the wifi card in to test it works.  Plug it in.  If network manager doesn;t see it then try another!

I have built-in intel wifi on my company laptop and no issue at all.  Even Networkmanager is stable and just works (damn well).

I travel a lot in my job and some hotels have weird proprietary wifi networks and you must use their wifi card.  Never had a problem.  Plug it in and it works. 

In another situation recently a hotel without staff competent to diagnose a problem asked me to use their wifi card to be sure there is nothing wrong with my setup.  (I could connect but signal was low and connection kept dropping).   Sure enough their card worked the moment it was plugged in, got good signal (like my internal setup did) in the lobby-  but would lose signal and drop out in my room...   again another wifi card "just worked".

Sorry I didnt note the card brands or models.

My wife's cheapy laptop (it was a gift from her previous boyfriend before I met her...  maybe thats why he is an ex- now....  hehehe)...  back to the point - she was using a D-Link AirPlus DWL-650+ wifi adapter that just refused to play well with Fiesty when I installed on her laptop.

The DWL-650+ would see the available wifi networks, report signal strength and even pretent to try and connect.  It would never connect tho.  I replaced it with an old (7yrs old!) Lucent Technologies Orinoco (Silver) 11Mbit/s card I had laying around and it worked first time.   

(yer yer I will get her something better and faster before i become an ex- too....  hehehe)

Moral of the story - some hardware (lots) Just works.   Some doesnt.

---

### Post by tiger's on 2007-06-20
> **tact said:**
> Is your computer a laptop?   Take it to the shop and tell them you want to plug the wifi card in to test it works.  Plug it in.  If network manager doesn;t see it then try another!

Moral of the story - some hardware (lots) Just works.   Some doesnt.

I'm sorry, but I've another opinion. Some operating systems provide handy support for drivers. Just works. Some doesnt :-)

I agree, that some vendors does not provide drivers for linux. But that hardware is mostly standard-based. And there is tools like ndiswrappers for other hardware. So, where is official HOW-TO's? Not just user-published guides. 

Just for example - I don't have to install 915resolution fix in Fedora 7 - it has already embedded in distr. It's useful because anyway EVERY USER with i915 WOULD/SHOULD install it. So, what's the point to make it as external update?

Anyway, thanks to all this guys, who spent their time to make free and useful OS and software for us! :-)

---

### Post by tact on 2007-06-21
> **tiger's said:**
> I'm sorry, but I've another opinion. Some operating systems provide handy support for drivers. Just works. Some doesnt :-)

*chuckling here*   Hmmmm when was the last time you installed Windows from scratch?   "Handy support for drivers" - just does not fit into that situation at all.  


(real life blood and gore follows)

Installing XP from scratch on a machine with SUPPORTED hardware:
insert WinXP CD...  answer questions, reboot after a coffee, and you end up with:
- a desktop in 640x480x16 colours(?)  (no proper video support)
- no network card support
- weird limited bluetooth support if at all
- likely only PC speaker sound support (no drivers for your sound card)
- (am sure there is more...add to the list pls...)

Now you have to go online (how?  No network card support!) and search and search through vendor sites for the drivers for your hardware.  Search Dell official site for a D610 network card driver and even if you search on the machines unique service tag you still have to "KNOW" which of 3 possible network cards may be actually inside your machine....   thats the trouble for just ONE driver for ONE piece of hardware.  Repeat as needed for all other hardware vendors of the bits in your box.

Once your sort out all the "handy hardware drivers" and get your machine handy again (days)...  then think about the software side - installing the productivity needs like Office suite, AV, antispyware, etc(another few days work)
--------------------

Install ubuntu from scratch on machine with SUPPORTED hardware:
Insert liveCD, answer questions, reboot after a (very rushed) coffee, and you end up with:
- desktop in 1024x768x24bit colour and choices to change resolution as you please
- network (wired and wifi) all working, auto change over, 
- bluetooth happy and working
- full stereo soundcard working
- no need to source driver to get 19" external monitor working
- drop my laptop into its docking station and ALL features work

Nothing to do!  *sigh*  What about the software then?  Oops - thats all there too, Office suite, no need for AV or anti spyware...   

Guess I will just go mow the lawn or surf the net.    THATS what i call handy driver support.  :)

---

### Post by jeffstack on 2007-06-22
im brand new to ubuntu and linux, early may 2007 of all the distros i've tried ubuntu is the only one that my wireless worked and made me chose to keep and learn. i used to be a heavy gamer (oblivion and morrowind) now i have a new game ubuntu and kubuntu.
i have a strait e-machines t5048 nothing special box and two belkin wireless g usb adapters
i do not have a hardwire internet. Im hooked and loving it

---

### Post by tact on 2007-06-22
...and since the mood just struck.   As a balance to the quickie comparo of winXP and ubuntu regarding supported hardware. :

- WinXP with some piece of unsupported hardware...  good luck.

- ubuntu with some piece of unsupported hardware....  start a thread here and see if some work around cannot be found.  :)

:)

---

### Post by Felix-the-Cat on 2007-06-24
(I'm sure you have already tried this, but nevertheless...) I got my broadcom 4318 working (although at only 11mb/s) with bcm43xx-fwcutter. I just installed it from synaptic package manager and when it asked if i wanted to extract the firmware i said yes. I have tried ndiswapper and others but bcm43xx-fwcutter is the only thing that has consistently worked for me.

---

### Post by NotTheMessiah on 2007-06-24
Hello

My post isn't going to help anyone but i just wanted to say that my experience with Ubuntu has been an extremely positive one. I'm(was) a hardcore longtime windows user which means i am(was:) a linux idiot :) ). My first install was suse 10.1 and i really liked it even though it was buggy and a pain in the bum to troubleshoot. And then i installed Ubuntu feisty on my desktop PC(dual boot XP) and it just worked. Updating is a bliss,stability rock solid, even troubleshooting is fun. Then it was time to do it on my laptop and again very straight forward and easy. From my previous experience with Suse 10.1 i didn't even touch my laptop's internal(unrecognized) winmodem and did what every person with an external dial-up modem would do: buy a cheap crossover cable and share the internet connection. It was easy.. just a little configuration of static IP addresses in network manager and playing with firestarter for a while and that was it. I did all of this without any research(typical newbie :) and it just worked for me. Obviously you have to have the time and the desire(like the initiator of the thread) but it is more then worth it. And guess what? I was not able to use the crossover internet sharing when my host was XP(i was just curious to see how it will be compared to Ubuntu network setup). Also my wireless card(laptop) is fully recognized and i'll try to use it in the near future. I have a couple of minor problems(that's why i'm here) which i'm sure i'll solve but either way i am completely willing to live with them:).

On my desktop i have to modprobe my digitalTV card every time i restart the PC in order for kaffein to recognize the SAA7134.

And of course the only persistent problem is the hibernate/suspend thing. It is problematic--it seemed to work for a while but not anymore. And the vertical scroll on my lap doesn't work. I'm not asking for help(for now:)) i just wanted to illustrate my almost flawless transition to linux on two different machines. My desktop is an Athlon64 3700+ clawhammer(skt754) and my lap is NEC versa P8100(centrino 1.73).

So i want to thank everyone that is responsible for Ubuntu or associated with it in any shape or form. Thank you

---

### Post by Josey on 2007-06-25
For broadcom 43xx
First remove ndiswrapper
```
sudo apt-get remove ndiswrapper
```
then install this driver... just double click it after you download it.
[http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133)
reboot
enjoy wireless

---

