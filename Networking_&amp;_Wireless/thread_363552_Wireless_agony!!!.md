---
title: "Wireless agony!!!"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by gwowders on 2007-02-17
Ok, maybe an exaggeration, but I've tried posting in the main Beginners section without reply so far... perhaps the wireless experts are in here!!!

Ok... first time installing Eubuntu after threatening to for quite some time, and it appears to be a little more painfull than I would have imagined!

I tried 6.06 at first, but it crashed on install (something about X Server not starting... blah blah), a quick hunt of these forums suggested a million and one solutions, none of which seemed entirely clear, so I downloaded 6.10, which seemed to install with no problems.

If it makes any difference at this point I'd like to point out that I have installed Ubuntu on a partition of my existing XP box.

Next problem soon crops up, my wireless card isn't supported out of the box (its not like its a strange make or anything, one of those BT packages using the Voyager2100 and 1040 pci cards, which are based on the Broadcom BCM4306KFB chipset according to the Ndiswrapper list). So I have to install something called Ndiswrapper, which will allow me to run the driver under some kind of emulation or whatever. To be honest, I'm sure it is interesting but at this point I'd just like my shiny Ubuntu installation to be able to talk to the outside world, something which Windows makes rather easy (maybe too easy, different discussion for a different time).

Anyway, I follow the (many) instructions dotted about the place, install Ndiswrapper eventually, locate my bcmwl5a.inf file and then Install New Driver... and this tells me hardware is present, so all good. I then select Configure Network (also System -> Administration -> Networking I believe?). I add my Essid and (assume in the correct place) my wep key. Select Ok. Tick the box next to Wireless connection (a message tells me Activating network interface). Then nothing, when according to the instructions I should now be rocking and rolling. I think I have tried as many different combinations as I possibly can, but still no joy!!!! I have heard that the /etc/network/interfaces file can be important, I tried a few changes but again nothing so rolled back to the original - this looks like:

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid BTVOYAGER2100-23
wireless-key s:XXXXXX

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1
```

From the instructions I was under the impression that this driver would be associated with wlan0 as opposed to eth1 but some of the more recent posts suggest that it doesn't matter... again I have no clue!

So.... as with so many on here, all help appreciated. I have used *nix systems once or twice before but its probably best if any and all instructions were as simple as possible!!! I'll try to help as much as possible by printing output etc. but please bear in mind that any additional files that are needed will have to be downloaded from the xp partition and then copied across (ubuntu nicely seems to mount my ntfs partition which makes this part a little easier, at least in one direction), so again, the simpler the better!!!!

If its of any use, the output from an ifconfig and iwconfig are:

```
ben@Ben-ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 

Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX 

packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7188 (7.0 KiB)  TX bytes:7188 (7.0 

KiB)

ben@Ben-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  

Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  

Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid 

misc:0   Missed beacon:0
```

Thanks in advance!!!!  Looking forward to getting this bad boy up and running!

Ben

---

### Post by Metaljaz on 2007-02-17
If you haven't read through this thread yet give it a try. If no luck post back.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

---

### Post by gwowders on 2007-02-18
I've heard some bad reports about this fwcutter method, all along the lines of the performance being pretty bad.  What would your views be on this?

---

### Post by Metaljaz on 2007-02-18
No personal experience for me but i have read both good and bad. I guess it depends on
your system. Here is another link that did not use fwcutter, you can try using it as a guide to make
sure you did everything:

[http://www.linuxquestions.org/questions/showthread.php?t=462995](http://www.linuxquestions.org/questions/showthread.php?t=462995)

---

### Post by gwowders on 2007-02-19
Hey Mataljaz, cheers for the links!

I eventually found [ this]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-f81347abfd1a9542276e210460e6ecd5fb49fd1a") which proved invaluable!

Ultimately, I had to carry out a fresh install anyway (I think because I had ballsed up the previous installation by trying too many different things), then do everything exactly as described in the HowTo above.  The only point I would make to any other complete beginners like myself is that **it is very important to make sure that there is a corresponding entry in /etc/iftab and /etc/networking/interfaces for (in my case) wlan0.**  Because I don't have any other network devices attached to my PC I was able to edit everything else out with a '#'.  I also needed to pay extra attention to the Ndiswrapper list which mentions that for my pci card (supplied with the BT Voyager wireless pack and labelled as a 1040) I need to use the bcmwl5**a**.inf driver, as opposed to most of the other examples which don't.

So, there we have it, last night at 00:15 I managed to get Ubuntu talking to the outside world.  if I have to make one comment about this (and I really feel I do), it wasn't easy in the slightes, and I'll bet that for every one person like me that perseveres and eventually gets this working, there are hundreds that don't.  If it is the ultimate goal of the Ubuntu crowd to truly push their distro to the masses then this ndiswrapper process needs to be dramatically improved and simplified.  I appreciate that there are lots of other driver issues (and that this isn't always the fault of the OS, rather the vendors that just don't create driver software for *nix) but network connectivity is key, because the CD can't contain everything!  Once a user has access to the 'net (and the great resource that is these forums) then thats half the battle.  IMHO (as far as any opinions are Humble) this needs to be addressed as a matter of priority.

</rant> ;-)

Many thanks again Metaljaz, much appreciated buddy!

---

### Post by chili555 on 2007-02-19
<rant>

This is hardly the fault of Ubuntu. Wireless card manufacturers seem to come out with a new whiz-bang go-fast chipset a week! None provide Linux drivers.

Linus and the kernel developers include kernel modules for many more wireless cards with every release. Of necessity, they are always behind, because what they wrote into the kernel last month doesn't include the whiz-bang go-fast chipset that came out today.

Well, what about picking out a wireless card that is compatible from the git-go? HA! Nobody, including me, ever does that. They install Linux on a partition on whatever computer they own today. You know, the one with the shiny new whiz-bang go-fast wireless chipset.

BTW, I have a whole pile of hardware I guarantee works great in Win 98SE and I guarantee cannot *ever* be coaxed to life in Linux. Watch Ebay!

So we have kernel modules for wireless cards that work out of the box. OK, so walk into Best Buy and try to buy a Prism 2 card. You can't. They haven't been sold retail for years.

Well, I read that Linksys XYZ uses the xyz987.ko module. I'll get that one. Well, which version? Version 2.7? Well, they sell version...hmmm...the box doesn't say which version this is! 

So we get Ndiswrapper. Fwcutter. Which .inf file works? The one from the 98SE driver? XP? The US version of the card? Or...?

Now we have to set up our card to work with WEP or WPA. Looks easy. HA!

All of this is in the hands of the noobs to figure out. The group we want to succeed the most, but with the least knowledge and, in a few cases, perseverance.

I am not sure there is an easy solution. Keep chugging, noobs. We will help you all we can.

</rant>

PS-This post proudly posted with wireless/ndiswrapper/WEP.

---

### Post by gwowders on 2007-02-19
Nice rant Chili555, I like your style!

I agree totally, and appreciate 100% that the majority of the blame does tend to lie with the hardware vendors themselves.  I suspect it will take a while to get everyone educated that they need to write drivers for an OS other than MS, but fingers crossed they'll get there eventually.

What Ubuntu need to make easier is supporting the whole ndiswrapper / <some other generic emulation> process for users that have never picked up a Linux distro before.  We all laugh at the MS 'wizard' approach of Click Next -> Click Next -> Click Next -> Click Finish, but in some instances that is exactly what people need.  

The version of ubuntu that I installed (6.10) needed me to install some other application (the name escapes me) from the CD before I could run the ```
make distclean, make and make install
``` commands (again, double clicking an .exe file, while maybe not as safe, suddenly seems perfect for the vast majority of users that just want to run software and don't really care about compiling it).  That just seemed crazy!  Why **wouldn't** the default install have this included as standard????

I'm going to keep going with Ubuntu, I feel it has alot to offer and is a real alternative to other desktop solutions, but if they're serious about offering to end user 'noobs' then I suspect there might be a little bit more work left to do.

As always, any and all thoughts appreciated!

Ben

---

### Post by gwowders on 2007-02-19
Grumble... 

So, I connect to the internet, first thing that happens is I download a bunch of updates that kill off my network connection again.

I'm getting a little tired of this...

Yes, I know, re-install ndiswrapper etc. etc.
](*,)

---

