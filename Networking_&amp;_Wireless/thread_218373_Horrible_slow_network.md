---
title: "Horrible slow network"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by GlurG on 2006-07-18
Hi

I have a network consisting of 3 computers (2 WinXp and 1 Linux Ubuntu). Transferring files between my 2 WinXP comps works fine. But if I transfer a couple of files between my Ubuntu comp and one of the WinXP comps, it slows to a crawl. Uploading a ~300mb files to my Ubuntu box (through Samba) takes around 3 minutes. Downloading a ~300mb file to the same box takes ~260 minutes. Now , obviously something is wrong, it should NOT take that long.
In order to test the HTTP transfer rate, I installed Apache2 and tried to download a ~300mb file to one of my Win boxes. Well, the avarage speed was around 50kb/s for 5 sec, then the transfer died.
I ran "mii-tool" to check if my network card is running on full duplex. The result:
```

eth0: negotiated 100baseTx-FD, link ok

```
I assume FD stands of Full Duplex. My comps are behind a D-Link 604 Router with the latest firmware. I'm new to Linux, so I guess that I've screwed up some config variable or something(?) I read on the forum that others also have problem with their network speed.
So, how do I fix the speed issue!?

Cheers

---

### Post by dgrafix on 2006-07-19
Getting the same problem, my windows pcs are all fine with each other but when samba tries it tends to fluctuate madly between 0bytes and 5MiB/s sometimes it flatlines totally for ages and windows times out (as viewed from taskmon)

---

### Post by roberthr on 2006-08-29
I have the same problem. Ubuntu out of the box samba settings and it doesn't go anywhere. 

From Windows to Ubuntu Linux horrible. 1 Mb file took 20 minutes to get copied. From Windows to another Linux it went smooth.

---

### Post by dannyboy79 on 2006-08-30
Sorry but I have to say I have the same problem! I was actually thinking it was my router not handling the packets correctly but now I am guessing it's the smb.conf file within Ubuntu. There has got to be a Ubuntu Network person who has setup a home network that is getting way better rwesults than we are all gettings. Hopefully they can help quickly! OH, I am not trying to hi-jack your thread

---

### Post by dgrafix on 2006-08-31
I fixed mine in the end, well...

by fixed i mean ive got it up to about 10Mb and stable.

what i did was went to the junkyard, pulled open an old pc, ripped out the pci 10/100 eth. card, disabled my rotten on board card from bios, put smb.conf back 2 normal and added the commented line (the bit in smb.conf that says ´you may want to add this if on linux´)to the END of the next line (dont just uncomment it)

rebooted and its been joy ever since. I tried copying 1 gig of images across from windows 2 windows and then windows 2 ubuntu. They were about the same time to complete  windows2windows was only slightly faster.

---

### Post by dannyboy79 on 2006-09-01
wait, please explain better what you added to your smb.conf for you to get 10MB and stable transfers? You wrote, put smb.conf back 2 normal and added the commented line (the bit in smb.conf that says ´you may want to add this if on linux´)to the END of the next line (dont just uncomment it)" but I have no idea what line or what exactly you put in the smb.conf file. please explain more. thank you very much

---

### Post by dgrafix on 2006-09-02
10Mb and 10MB are not the same thing (bits & bytes)
(I think if i can remember my skooling :)

from smb.conf

# You may want to add the following on a Linux system:
# SO_RCVBUF=4096 SO_SNDBUF=4096

  socket options = TCP_NODELAY SO_RCVBUF=4096 SO_SNDBUF=4096


Thing is though, i tried that with my old card and there was no change. Replaced the network card and on large files im now getting between 5Mb & 9Mb stable transfer rates (usually)

By stable i mean it doesnt time out, not speed fluctuations (but i think thats probably quite normal).

---

### Post by PryGuy on 2006-09-02
You've saved me!:D

---

### Post by ianbennett on 2007-05-15
Same problem here - slow and fluctuating speeds transferring data to a Windows box.

Did a quick search and found two instances of smb.conf - one in /etc/samba and one in /usr/share/samba.  Which one do I edit?  I suppose I could edit both to be sure :) 

(First post on here, by the way - thanks in advance for any assistance)

Ian

---

### Post by elcasey on 2007-06-03
OK, wait a second. This entire thread is filled with people with slow networking problems, like myself, and the best we got was "I installed an old NIC and it's running at 80% of its rated speed"?! Are you serious??

Why does Ubuntu have these networking problems? I'm using an Intel 10/100 onboard and I'm barely getting 5Mbps. This is completely and utterly unacceptable.

Where are the answers from Ubuntu staff and where is the **fix**, not an 80% workaround?

---

### Post by ianbennett on 2007-06-03
Thanks for the reminder - I forgot to post back here with my results.

What I did was disable the onboard NIC on my motherboard, put in an old SMC PCI network card that I found in the bottom of my 'bits box', and guess what - my network is absolutely flying now! :D

I suppose it's just a case of Ubuntu's driver support not being bang up to date with the latest motherboards.  My mobo is an Asus P5LD2 SE, a fairly recent model with an Intel 945P chipset.  If I was using Windows, I would be able to install Asus's drivers, and everything would work perfectly.  Linux users have to wait until their distro catches up and incorporates the necessary drivers.  It probably won't be long - I would guess that Gutsy will have the support built in.  This is based on the fact that Edgy didn't support the built-in sound card on my mobo.  I was on the verge of rummaging in my bits box for a sound card (I'm sure there's an old SoundBlaster in there somewhere) but then I upgraded to the Fesity beta and, lo and behold, the sound worked perfectly.  I should really have realised that this might be the case with the onboard NIC.

@elcasey - So I don't think that it's a case of Ubuntu needing a 'fix', I guess you and I just need to be patient and wait for Ubuntu to come up with the driver support.  Or we should just use hardware that's not so 'cutting edge'! :rolleyes:

---

### Post by elcasey on 2007-06-03
Uh, isn't a new driver a fix? I spent all day messing around with this damned thing and finally got *acceptable* speeds, but not *good* speeds. I've approached 50Mbps but this is only after swearing a lot, opening my server's case once and using "ethtool" to force both cards into 100baseTx-FD mode.

A fix is definitely needed. 50% of the network speed I *should* be getting just isn't good enough. Moreover, I'm not interested in upgrading my OS every four to six months, especially after upgrading to Feisty (three times) forced me to reinstall (three times). I've learned my lesson about upgrading Ubuntu -- it will never happen again. But should I have to roll an entirely new kernel just to get decent network speeds? I'm not going to to do that.

---

### Post by Nythain on 2007-08-03
hahah... i WISH i could get those speeds... atm im transfering too and from a windows box and fluctuating between 100k and 1meg... im assuming it has to do with the switch from a wired router to the new wireless router and the xp laptop now using its built in wireless nic.

Im still hard wired as i HATE wireless with a passion, and this most recent problem just further perpetuates my hatered for wireless technology.

im not familiar with ethtool, though i gather if i can figure out how to use it it might be my temp solution... i've heard that even going from 100 to 10 with full duplexing, while not allowing me to get teh FULL potential of my card, will at least help get me to a stable 5Mbps (wich would be a whopping 5-50x improvement, no complaints from me)

currently the problem is so bad that watchign a video file over teh network is an impossibility.

I've also read that changing the OS level of samba or wins might help, but once again, i have no experience in that department either.

any clues, suggestions, ideas, or help would be much appreciated

---

### Post by dgrafix on 2007-08-03
I fixed my problem by simply buying a new card. I can understand spending several hours of fighting it as a lot can be learned, but at the end of the day (or should i say, week!), 20 quid for a new one is well worth it.
Mine was a netgear in the end for my laptop (worked out of the box) and my desktop was some unbadged oem PCI one from a junk pc. (the on board one was hopeless and is what started this thread)

---

### Post by Nythain on 2007-08-04
replaced my old wired nic with a new linksys wireless g... got a new wireless g for the laptop and disabled the onboard wireless... all running current drivers and still having this problem.

basically the transfer is fluctuating between 0-600k and frequently stalling and timing out.

made a few adjustments to my smb.conf, and currently making a few more... problem has to lie in the way the ubuntu box and windows machine are communicating because xp to xp is currently running great

---

### Post by dgrafix on 2007-08-06
Lots of cards share the same chipset, you may find your new is the same chipset as before. With me the problem was with a belkin which had a ralink chipset. The one I have had since (and highly reccomend) is the netgear WG511T (atheros based) cards. 
There is a compatibility chart somewhere on these forums showing a full list of cards that work out of the box, ones that work with fiddling and ones that need wrappers/dont work at all.


edit:
that link!
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by TheRealMikeD on 2007-11-10
I had similar problems with my Linksys LNE100TX.  Painfully slow and unreliable file copies to and from Windows.  I tried NFS, Samba, FTP.  Same problems with all protocols.  Which lead me to believe that there was something fundamentally flawed with my networking setup.

That Linksys card works great in Windows and worked with Redhat 9 on another box, but something dgrafix said made me think to check the hardware support list.  Lo and behold the Linksys is NOT supported in Ubuntu.  Not sure why not, but there it is.

I went out and bought a Dynex (Best Buy's house brand) DX-E101.  It uses the VIA VT6105 chipset, which is supported through the via-rhine module.  Just plugged it in a little while ago, and it works great so far.  Light years faster than the Linksys.

BTW, dgrafix posted the link to the list of supported wireless cards.  Here is the list of supported wired cards as well: [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards).

Cheers,
-Mike D.

---

### Post by Whiffle on 2007-11-11
I happen to think there is something else screwy going on here thats ubuntu specific.  My laptop and desktop were running ubuntu.  Copying files between them usually got me about 5 megabytes/s over nfs.  On a whim, I put slackware on my laptop and was copying a 3.6 GB file.  Low and behold, I was getting 10 megabytes/s, over ssh!  Something is definitely screwy here.  The laptop has a broadcom netextreme 10/100/1000 w/ the tg3 driver, and the desktop has a USR997902 us robotics gigabit card.

---

### Post by sethfc on 2008-01-06
> **elcasey said:**
> OK, wait a second. This entire thread is filled with people with slow networking problems, like myself, and the best we got was "I installed an old NIC and it's running at 80% of its rated speed"?! Are you serious??

Why does Ubuntu have these networking problems? I'm using an Intel 10/100 onboard and I'm barely getting 5Mbps. This is completely and utterly unacceptable.

Where are the answers from Ubuntu staff and where is the **fix**, not an 80% workaround?

amen bro.

I TOO am having the same problem.  Except transferring a file from my Mac OS X Tiger to Ubuntu 7.10 yielded:

[img]http://home.comcast.net/~saflores1/hf/Screenshot.jpg[/img]

a 900 MB file taking nearly 2 hours with HORRIBLE fluxuation?  I transferred the file from Mac OS X Tiger to Win XP in 90 seconds...

o_0

---

### Post by JPorter on 2008-01-06
oops, mis-post.  my bad

---

### Post by Farley69 on 2008-02-05
I had a similar problem, and resolved by updating the firmware on my Linksys router.  May not be your solution, but worth a try.

---

### Post by jr mcfly on 2008-02-09
Same issue here.  I'd posted another thread this morning before coming across this one.  Wired network speeds are topping out at around 10Mbps, even though Network Manager and mii-tool claim the NIC is operating at 100Mbps.  The PC also has Fedora 8 installed, & when I boot that I get 100Mbps transfer speeds.  My NIC is a VIA VT6102 (on the mobo).

---

### Post by jr mcfly on 2008-02-11
ok, I threw money at the problem & fixed it.  I went out and bought a Dlink DFE-530TX+ fast ethernet card for 10 bucks and installed that.  Upon booting, I ran lsmod and found, to my horror, that this card uses exactly the same driver as the NIC built into the motherboard (via_rhine).  Crap, thinks I.  Then I run lspci and find that the board in fact uses a slightly different chipset (the VT6105).  With cautious optimism, I fire up a 250MB file transfer from my NFS share, and it transfers in 22 seconds (11.7 MB/s).  Hooray.

The VT6102 is not a new chipset, and according to the Free Software Foundation's list of supported network cards at [https://www.fsf.org/resources/hw/net/wired-ethernet](https://www.fsf.org/resources/hw/net/wired-ethernet), that chipset is "known to work with free GNU/Linux systems".  I would argue that this device does not really "work" under Ubuntu, since although it connects OK it operates 10 times slower than its advertised capacity,  (it works fine with Fedora, by the way.)  But what the hell.  I'm up & running now & it only cost me 10 bucks.

---

### Post by moonlightcheese on 2008-02-15
[http://www.hep.ucl.ac.uk/~ytl/tcpip/linux/txqueuelen/datatag-tcp/](http://www.hep.ucl.ac.uk/~ytl/tcpip/linux/txqueuelen/datatag-tcp/)

---

### Post by mkz on 2008-03-21
Same problem here, but ...

I've been doing some tests and ... it's very very strange.

[http://ubuntuforums.org/showthread.php?p=4532719#post4532719](http://ubuntuforums.org/showthread.php?p=4532719#post4532719)


Any ideas ?

Kind regards,

Mkz.

---

### Post by Amorphous_Snake on 2008-04-06
I had exactly the same problem. I had a Realtek RTL8139 PCI 10/100 ethernet card which is supposed to run fine in Linux. It didn't. I bought a D-Link DFE-520TX (Via Rhine III vt6105) and the problem remains. Horrible speed with samba.

Here is my post:
[http://ubuntuforums.org/showthread.php?p=4657065#post4657065](http://ubuntuforums.org/showthread.php?p=4657065#post4657065)

Any help you can provide will be greatly appreciated.

---

### Post by tropicalfish on 2008-04-12
BUMP Any fix to this?!????

---

### Post by dgrafix on 2008-04-13
These days i buy hardware for my OS as a Mac user would, not the other way round. There is far to much cheap win-only rubbish hardware out there, thats have been made by manufacturers that have to hack around their own product even get it working in windows (usually with a million firmware / driver versions) and a tragic "It will do" attitude.

I would check the compatability chart (round here somewhere) and get a new one. 
$20 is a small price to pay when the entire OS is free.

If its Internal,
PCI Net cards seem to work better in my experience although ive not had this problem with more modern on-boards. I did have an issue with one onboard one (what i posted about above), but on the whole the internal ones  seem to be pretty good.

If its a WIFI card:
From Personal experience stay away from these:
Belkin, D-Link, some of the netgears.

Better to go with these:
Netgear, Proxim, Intel, Intel Centrino, Broadcom, (especially if they have Atheros or Orinoco based chipsets)

Best** check out the compatability chart first.**

---

### Post by Tunaaja on 2008-05-13
I have speed problems too after compelete reinstallation from ubuntu 7.x to 8.04
Network card is intel 1000 pro/gt and i have tested with 2 different drivers e1000-8.0.1 and e1000-7.6.15.4 and d-link dge-528T card that has DLG10028A chipset
With both cards i get about 9-10MB/s transfer rate when i transfer with ftp or samba to windows xp and previous install i got about 40-60MB/s
Other way from xp to ubuntu i get about 30MB/s and that is little slow too.
I have not changed anything else but installed new ubuntu.
Offcourse both computers have gigabit lan and switch is zyxel gigabit switch

---

