---
title: "BT Voyager 1010 USB: Newbie needs help."
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by Apocalypse King on 2006-08-20
I originally posted this in the beginners forum, but it might be more apporopriate in here.

I'm a bit of a Linux newbie (although I've dabbled in it in the past), but I've decided to choose Ubuntu (Dapper Drake) as the distribution which I will use.

Unfortunately, every time I try installing Linux, (I've tried Fedora and Slackware in the past), I come across the same problem; I cannot get my BT Voyager Wireless USB adapter to work properly, and as a result, cannot connect to the internet.

Now, I've looked around the internet and I found this very handy troubleshooting guide. I printed out a copy of this and went back into my Ubuntu installation, and went through the steps, and from what I gathered:

* The device is recognised by Linux (however lsusb describes it as a 'Generic USB Device', is this bad? It also needs to be unplugged and re-plugged in before the wireless device appears on the list in the network settings. Is there a way around that? It plugs in at the back and it's fiddly to get to. I don't want to have to plug it back in every time I start the computer up.)

* The device is assigned a driver by Linux, which I *think* is the right driver, but I'm not completely sure. I'll find the name of it later.

* The device is not connecting to the router. When I use the command 'sudo iwlist wlan0 scan' it thinks for a moment and then says that the device is unavailable.

Now, I am not sure what to do. I have tried changing the settings on my router, changing the security settings, even temporarily switching WEP encryption off, but I can't seem to get this device to work in Linux.

Ultimately, this is the same problem that stopped me from using Linux the last few times I've tried it, but this time I am determined!

Specifically, the device in question is a BT Voyager 1010 USB adapter, which connects to a BT Voyager 2000 router (I am assuming that the type of router isn't really important, and that the wireless USB adapter is the important part to configure in Linux).

Any help here would be wonderful. Apologies if this seems newbie-ish, I don't know too much about Linux yet, and it's hard to really learn much when I have to log out of Linux and back into Windows to look up information on the internet! Also, sorry if this post is rather long-winded. Hopefully someone out there will make sense of it. Thanks in advance for any help, and if any more information is needed, I will try my best to find it.

---

### Post by greatmetal on 2006-08-20
give linuxant a try didnt work for me though :(

---

### Post by SandersCraddock on 2006-12-12
I would also appreciate any help on this as I have been struggling to find anything to help. Theoretically this device should work out of the box but does not seem to want to connect to the internet.

---

### Post by Apocalypse King on 2006-12-13
I'm afraid I'm still stumped with it. I managed to connect to the internet using a Belkin wireless adapter instead of the BT one, and it works perfectly without needing anything adjusted (although for some reason it crashes the network tool in Ubuntu, I had to set it up using iwconfig, no biggie though).

No idea why the BT one didn't work though. Not sure if [ndiswrapper]("http://ndiswrapper.sourceforge.net/") would help it though, can't remember if I tried that or not. Might be worth a look if you're still stuck. I think it needs you to have the windows driver handy.

---

### Post by SandersCraddock on 2006-12-13
Ndiswrapper shouldn't theoretically be needed as the bt voyager chipset is supported out of the box.

---

### Post by cawill on 2006-12-17
Hi, what wireless router are you using?
Is it the bt voyager 2000?

Thanks

---

### Post by hessiess on 2007-05-13
have you solved this problem? ive got the exact same problem.

---

### Post by Lifeis on 2008-06-29
I have the exact same problem too guys.
Cant get my Voyager 1010 adapter to work at all. I tried downloading the windows driver from BT's website, and installed it with wine, then used Ndiswrapper to install the driver but it wont work. Ndiswrapper says: 'Invalid Driver!'
Which is strange.

Running Iwconfig I get:
> 
ubuntu@ubuntu-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan2     IEEE 802.11b  ESSID:off/any  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu-laptop:~$ 

I run Ubuntu Hardy Heron, dunno if that makes a difference.
Also the laptop I have is a HP G6000. It has a built in Wlan adapter, I had that connected twice, and worked perfectly however when I retstarted my pc, Ndiswrapper just says 'Hardware Present: No'
And it wont connect. So I gave up on the inbuilt card, now I decided to use the USB adapter.
Any help would be great.
Thanks

---

