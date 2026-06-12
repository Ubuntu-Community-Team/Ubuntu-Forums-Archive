---
title: "Edgy Eft Keyboard hang after &quot;bcm43xx: Controller RESET (TX timeout)&quot;"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by jon_herr on 2006-11-07
"bcm43xx: Controller RESET (TX timeout)"

When it happens my keyboard is frozen - my mouse works - but sometimes the only way to shutdown or reboot is a hard reset.

Menus respond but don't do anything.

I'm trying a different kernel.

Edgy is purty.  Really nice except for this issue.

Jon

---

### Post by ominolore on 2006-11-08
Same problem here.

I installed edgy on my friend's pc with bcm43xx fw_cutter driver and network manager.

I experienced some keyboard hangups and often when shutting down the message "bcm43xx: Controller RESET (TX timeout)" is repeated.

Furthermore network manager hardly succeeds in connecting to wireless networks (many many tries are needed).

---

### Post by jon_herr on 2006-11-08
I have that symptom too...  Establishing the first connection to my wireless network is irregular at best.  Once connected it works until it hangs.

It seems to be a timing issue?  This is a single core Athlon 64 running 32 bit Ubuntu Edgy.  Entries that I've found with Google seem to point to these types of problems happening in SMP kernels.  

I guess it goes without saying that this problem didn't exist before I upgraded from Dapper to Edgy.  Dapper was solid as a rock.

Jon

---

### Post by jon_herr on 2006-11-08
Anyone have ideas on this issue?

---

### Post by jon_herr on 2006-11-09
Still no news on this one?

I'm about to go back to Dapper...  I like Edgy but I get hung up everyday and have to hard - reboot.  Dapper didn't do this.

Is this even being worked on?

Thanks,
Jon

---

### Post by jon_herr on 2006-11-10
Well I've switched back to Dapper...

I'll be looking for an update related to this problem to come in before moving on to Edgy.

Edgy is pretty but wireless is apparently broken for the bcm43xx.

Jon

---

### Post by Julolidine on 2006-11-12
I have this problem as well...I'm going to blacklist bcm43xx and try with ndis, let you guys know how that goes.

---

### Post by Julolidine on 2006-11-12
OK, got everything up and going.  Wireless is flawless now.  :-D   55MB/s also, no keyboard hangs.

blacklist bcm43xx and install ndiswrapper.  I compiled the latest from sourceforge, I'm not sure whether or not 1.18 or whatever the repo's have work.

---

### Post by srafx on 2006-11-14
I have the same problem, might be time to make the switch too.  Can you link me to the guide that you used to switch to ndiswrapper?

Thanks for this post guys...I was having trouble figuring out what was going on!

---

### Post by PriceChild on 2006-11-14
Guys at the end of the day this is why Edgy is called "edgy".

Please take part in testing Feisty to help get issues like this completely ironed out.

Pricey

---

### Post by Julolidine on 2006-11-15
Sorry for the delay, I didn't see that somebody wanted it

SO, this will be my first howto, and I'm going on vacation tommorow, so I don't know how much I'll be able to respond to any questions.  

I previously had ndiswrapper installed from dapper, so first order of business was to remove the old install

```
sudo rm -r /etc/ndiswrapper/bcmwl5 
```

then I downloaded ndiswrapper 1.28 from here
[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=459309](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=459309)

Also you will need bcmwl5.inf, which I found just trawling around on my windows partition, however its available in other threads and in various places on the internet.  

in order to compile it you need the basic make stuff which I'm going to assume you have, if not, you can find it elsewhere what you need

however, I didn't have this
```
sudo aptitude update
sudo aptitude install linux-headers-`uname -r`
```

next, I extracted the ndiswrapper, made and installed it
```

cd Desktop/
tar xvfz ndiswrapper-1.28.tar.gz 
cd ndiswrapper-1.28.tar.gz
make
sudo make install

```

next came the task of removing bcm43xx and getting it out of there
```
 
sudo gedit /etc/modprobe.d/blacklist
```

to which I added the following text at the very end

```

#blacklisting drivers
blacklist bcm43xx

```

Now note, after you type this, your wireless will completely stop, so be sure you're ready

```

sudo rmmod bcm43xx

```

Now, the last steps was ndiswrapping the drivers and getting it up

```

sudo ndiswrapper -i ~/Destop/bcmwl5.inf
sudo gedit /etc/modules

```

to /etc/modules, I added "ndiswrapper" to the very end (without quotes of course).

Then last thing
```

sudo modprobe ndiswrapper

```

and a restart of the computer.  :-D

---

### Post by srafx on 2006-11-15
Will this work with a linksys WMP54GS?  That is the pci card with speed booster.  I know i did a few of those steps (wiped out my current config..lol) and installed the new driver, but it said no hardware found.  I will try it again later tonight if you think it will work.

---

### Post by Julolidine on 2006-11-15
what is the result of 

```
lspci | grep Broadcom\ Corporation
```

??


Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

mine is 4306, and if yours is as well, it should work.  4318 apparently also works according to another thread.

---

### Post by srafx on 2006-11-15
> **Julolidine said:**
> what is the result of 

```
lspci | grep Broadcom\ Corporation
```

??


Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

mine is 4306, and if yours is as well, it should work.  4318 apparently also works according to another thread.

```
$ lspci | grep Broadcom\ Corporation
08:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

I guess I did something wrong then.

---

### Post by srafx on 2006-11-15
Well, I tried it...doesn't work.  I just get no wireless devices so im guessing it doesn't work with my card?

Anyone else having this problem?

---

### Post by jon_herr on 2006-11-17
When using ndiswrapper can you use WPA encryption?  If not then this solution is only partial.  I can't go back to WEP.

WEP is so easy to break in to they now teach it in Kindergarden after A, B, C s!

---

### Post by FrodoB on 2006-11-17
Have you seen this information?

Shows WPA and ndiswrapper:
[http://www.neowin.net/forum/lofiversion/index.php/t399787.html](http://www.neowin.net/forum/lofiversion/index.php/t399787.html)

---

### Post by srafx on 2006-11-17
> **FrodoB said:**
> Have you seen this information?

Shows WPA and ndiswrapper:
[http://www.neowin.net/forum/lofiversion/index.php/t399787.html](http://www.neowin.net/forum/lofiversion/index.php/t399787.html)

That is how I am using WPA with the bcm43xx driver so It looks like it will work.  I will be installing the ndiswrapper driver tomorrow, so I will let you know if it works or not.

---

### Post by FrodoB on 2006-11-17
Great, I have one of those that I have not yet setup on Linux, so I am anxious to hear how it goes.

---

### Post by jon_herr on 2006-11-18
Frodo,
Did you have to change the instructions in any subtle way?

I've tried it but all I get is:

jherr@mythbox:/etc$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:0f:66:70:4a:c4
Sending on   LPF/eth1/00:0f:66:70:4a:c4
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Javaddiction on 2006-11-24
I'm currently having the same issues with the error message as well. I tried using ndiswrapper already, but was having one heck of a time connecting to my WPA network and keeping it connected.

fwcutter has worked wonderfully for me with few complaints until the last few days when i noticed this error popping up. 

Does anyone actually have an idea as far as the problem yet or is everyone abandoning ship and once again going back to ndiswrapper?

I'll keep trying to do some research and see what i can come up with.

---

### Post by Javaddiction on 2006-11-24
This might be the reasoning for the error:
[http://www.mail-archive.com/bcm43xx-dev@lists.berlios.de/msg02434.html](http://www.mail-archive.com/bcm43xx-dev@lists.berlios.de/msg02434.html)
which i found via
[http://www.kernel.org/pub/linux/kernel/v2.6/snapshots/patch-2.6.19-rc4-git12.log](http://www.kernel.org/pub/linux/kernel/v2.6/snapshots/patch-2.6.19-rc4-git12.log)

So if this information is in any way related to the problem, it seems that this is a kernel issue and we'll have to wait until 2.6.19 becomes available (although i have found posts in this forum and others that indicate this error is occasionally triggered when having nvidia drivers loaded.)

Dunno if it's helpful, but hopefully someone more knowledgeable can take this ball and run with it.

---

### Post by FrodoB on 2006-11-24
I will check my instructions with a reinstall and let the list know.

---

### Post by srafx on 2006-11-26
Here was my solution to my timeout problem:
[http://ubuntuforums.org/showthread.php?t=305369](http://ubuntuforums.org/showthread.php?t=305369)

---

### Post by Lfrb on 2006-11-29
I also got the crash "Controller RESET" and my keyboard hangs up too.

Is there a new solution or the only solutions are to get back to ndiswrapper or to buy another wifi card ?

Thanks a lot

--
Lfrb

---

### Post by trubblemaker on 2006-11-29
Great howto from source.  I worn ya'll not to use the repository, packages they aren't batting 100% for upgrades.  Clean installs they work great, just a warning.

---

### Post by bbogart on 2006-12-22
Hey all,

Just wanted to say that this also happens on my powerbook with the same kernel module.. I have connection problems though, but after getting the wireless to work, I started getting the freeze. Looking into Ndiswrapper now...

too bad...

---

### Post by j.d.meisner on 2007-03-01
I have discovered a work a round the timeout problem of the bcm43xx driver. From a terminal session, ping your router: nohup ping -i 5 nnn.nnn.nnn.nnn &
Where nnn.nnn.nnn.nnn is the ip address of your router/gateway. You can of course start the ping instruction automatically by putting it in your .profile file. The nohup command makes sure the ping stays active, even when you log off.
It may not be a very elegant solution, but it works for me!

---

### Post by teet on 2007-03-03
Thanks for posting your update.  I may give it a whirl.

I've been having this same problem ever since I upgraded to edgy (over 4 months ago!).  I only use my desktop for 2-4 hours in the evenings so I'm usually not logged on long enough to have a freeze, but it's still very annoying when it occurs.

Does anybody have a "real" solution to this or will I just have to wait and upgrade to Feisty?  I have everything set up just the way I like it on edgy (except for this annoying problem) and was actually considering skipping the Feisty upgrade.  

-teet

---

