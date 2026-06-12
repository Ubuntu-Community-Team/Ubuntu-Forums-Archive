---
title: "Ubuntu hangs wireless router!"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by bogoliubov on 2007-09-26
Hello. I have a Netgear wireless router (wgt624 v2). For some reason I can surf without any problems, but if I want to install or update anything with Apt, the connection is lost and I have to restart the router. 

I've used the router with OS X without any problems, but with Ubuntu it's really annoying! I've had this problem on an iBook (Edgy and then Feisty) and a Clevo (intel wireless). So it shouldn't be the computer hardware that is at fault.


Anyone experienced this? Any solutions? I find it really stupid that I have to take my laptop to work just to install something!

---

### Post by bogoliubov on 2007-09-27
shameless bump...

---

### Post by bogoliubov on 2007-09-27
No-one? I have no idea what to do about it

---

### Post by SpiritIsReality on 2007-09-27
howdy
well google isn't helping me much because I don't know what to ask properly.
I can't find anybody saying apt-get causes lost connection.
are you using your router wirelessly ?
what I've seen guys ask for is to 
open up a terminal and give the command there, and see if there are any error messages.
and then there's the /var/log/ files to see if anything shows up there.
could be a bad configuration in apt.?
no...otherwise it wouldn't work at work. haha!

if we can think of some way of getting your pc to tell us what's wrong.
ok. it's something I have no experience with, but there's such a thing as setting a debugging
level on apps. I think if we can search for how to debug the apt-get  or the wlan0 connection
somehow.?
check your router's log files?

trails

---

### Post by SpiritIsReality on 2007-09-27
there's dpkg.log faillog debug messages user.log syslog
in /var/log
traceroute or something when run sudo apt-get install ...
when apt-get causes you to lose internet connection, can you ping router?
no, you said you have to reconnect.
edit : you said you have to restart the router.

[http://www.stanford.edu/~fenn/linux/]("http://www.stanford.edu/%7Efenn/linux/")
[http://www.google.ca/search?hl=en&q=wgt624+v2&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=wgt624+v2&btnG=Google+Search&meta=)
I'm thinking it's the router getting in the way of gnu/linux.
what kind of router do they have at work?
I'm using a linksys wrt54g but a wrt54gl, that's an L, is needed now, 
running openwrt.org , to wireless bridge/client to a di-524 d-link.
no problems with them. I'm sure there's better around.
[http://www.google.ca/search?hl=en&q=linux++router+troubleshooting&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux++router+troubleshooting&btnG=Google+Search&meta=)
a suggestion :
contact netgear , and report your problem.
[http://www.netgear.com/About/ContactUs.aspx](http://www.netgear.com/About/ContactUs.aspx)
they probably won't like the part about having no trouble at work,
compared to their router at your place.
there's a support page too. if you want to look thru there.
edit : my 2 cents worth.
found a bit about logs here
[https://help.ubuntu.com/community/SystemAdministration](https://help.ubuntu.com/community/SystemAdministration)
edit: wicd is recommended as a wireless manager, better than network manager for some cards. might help?
trails

---

### Post by bogoliubov on 2007-10-01
Hmm, I'm not sure I understand all you said, but I'll have a look around. Logs from apt will probably only tell me that the network didn't work..., but perhaps some network log can give me a clue...

---

### Post by SpiritIsReality on 2007-10-01
howdy
ya you're right.
There are some using openwrt.org on your router, even though it is a workinprogress for v1 on the table of hardware.
It may be worth a try.[http://www.google.ca/search?hl=en&q=site%3Aopenwrt.org+wgt624+v2&btnG=Google+Search&meta=]("http://www.google.ca/search?hl=en&q=site%3Aopenwrt.org+wgt624+v2&btnG=Google+Search&meta=")
[http://openwrt.org/](http://openwrt.org/)
here's a thread that might apply [http://ubuntuforums.org/showthread.php?t=566750](http://ubuntuforums.org/showthread.php?t=566750)
buds

---

### Post by bogoliubov on 2007-10-07
But the router worked OK in OS X. I don't see any reason why it should not under Linux! Also, changing OS on the router seems a bit of a long shot to me...

---

### Post by SpiritIsReality on 2007-10-07
ok
if you want to start another thread, cause I kinda messed this one up when I got here, please fly at it.
I'm thinkin a linux router box has got to be the caddilac router.
afraid to say what to do, cause I don't know, except that it's not much good the way it is is it>
buds

---

### Post by SpiritIsReality on 2007-10-07
why does the router at work work ok, and the one at home doesn't. it's the same comp makin' the requests.

---

### Post by mblackwell8 on 2007-10-07
do you have any further clues on how to solve this?

I have precisely the same symptoms, but I've only just started using Ubuntu/Linux and can't help... but I'd love a solution!

I have a Netgear RangeMax (WPN824) wireless router and I'm using a fairly stock Feisty installation on a Dell 630m (Intel wireless 2200BG chipset using the IPW2200 driver). I think that I'm using a native driver because lsmod | grep ndiswrapper returns nothing... but when I first set up Ubuntu I blindly followed several howto's to get my environment working.

This problem is driving me crazy and it essentially means that I can't install any software or upgrades...

---

### Post by SpiritIsReality on 2007-10-07
howdy
I would suggest starting a new thread in the forum of your choice, and hope for the best. I got nothin' but there's people round here that got lots.
buds

---

### Post by bogoliubov on 2007-10-08
> **mblackwell8 said:**
> do you have any further clues on how to solve this?

I have precisely the same symptoms, but I've only just started using Ubuntu/Linux and can't help... but I'd love a solution!

I have a Netgear RangeMax (WPN824) wireless router and I'm using a fairly stock Feisty installation on a Dell 630m (Intel wireless 2200BG chipset using the IPW2200 driver). I think that I'm using a native driver because lsmod | grep ndiswrapper returns nothing... but when I first set up Ubuntu I blindly followed several howto's to get my environment working.

This problem is driving me crazy and it essentially means that I can't install any software or upgrades...

Sometimes I can update Ubuntu using the wireless, but most often I have to restart the router so many times it's just simpler to use a cable for the update process. I can surf, but the connection is not very stable.

But since I had not problems in OS X, it shouldn't be the router..., but I have really no idea what
s going on..., and I agree, it's really frustrating!

---

### Post by sageb1 on 2007-10-08
How close r u to the router? Is the USB wireless adapter a, b, g or n?

Dropouts are sometiles due to interference from an electronic device using the same bandwidth. The wireless frequency is 2.4GHz which some cellular phones use too.

If you live in an urban area, then there may be a cell tower nearby or even on the top of your apartment building. This allows certain carriers to give good signals without dropping. However, it will interfere with wireless computing.

My guess is, the wireless router is being overwhelming by having to handle sustained traffic during update downloads. Linux by default places the wireless lan adapter into promiscuous mode.  What this means is almost maximum bandwidth during downloads (3 MB/s for 802.11b for maximum throughput of 11 MB/s or 25 percent of maximum throughput. 

Why the Mac had no problems:  Airport and OSX are kinder to networks and probably have preprogrammed throttling.

Proof of my argument:  use ping from command line and compare to OSX BSD command line.

$ ping -c 5 192.168.0.1

[I]-c 5 sets number of pings to 5.
192.168.0.1 is the internal Ip number of the router. Change to what your router uses.
[/I]

Hope this helps.

:guitar:

---

### Post by bogoliubov on 2007-10-08
> **sageb1 said:**
> How close r u to the router? Is the USB wireless adapter a, b, g or n?

Dropouts are sometiles due to interference from an electronic device using the same bandwidth. The wireless frequency is 2.4GHz which some cellular phones use too.

If you live in an urban area, then there may be a cell tower nearby or even on the top of your apartment building. This allows certain carriers to give good signals without dropping. However, it will interfere with wireless computing.

My guess is, the wireless router is being overwhelming by having to handle sustained traffic during update downloads. Linux by default places the wireless lan adapter into promiscuous mode.  What this means is almost maximum bandwidth during downloads (3 MB/s for 802.11b for maximum throughput of 11 MB/s or 25 percent of maximum throughput. 

Why the Mac had no problems:  Airport and OSX are kinder to networks and probably have preprogrammed throttling.

Proof of my argument:  use ping from command line and compare to OSX BSD command line.

$ ping -c 5 192.168.0.1

[I]-c 5 sets number of pings to 5.
192.168.0.1 is the internal Ip number of the router. Change to what your router uses.
[/I]

Hope this helps.

:guitar:


Ok, I'll have a look at this when I get home. Generally my connection is very good (I'm only about 4 meters from the router, without any walls between). 

Would it be an idea to switch the router to 12 MB/s mode? It's slow as a pig, but perhaps more stable?

Hmm, on the other hand, I can copy files from another PC (running Feisty) that is connected to the router (by wire) without any problems. Shouldn't this put at least as much "pressure" on the router as downloading stuff from the internet?

---

### Post by SpiritIsReality on 2007-10-08
> **sageb1 said:**
> How close r u to the router? Is the USB wireless adapter a, b, g or n?

Dropouts are sometiles due to interference from an electronic device using the same bandwidth. The wireless frequency is 2.4GHz which some cellular phones use too.

If you live in an urban area, then there may be a cell tower nearby or even on the top of your apartment building. This allows certain carriers to give good signals without dropping. However, it will interfere with wireless computing.

My guess is, the wireless router is being overwhelming by having to handle sustained traffic during update downloads. Linux by default places the wireless lan adapter into promiscuous mode.  What this means is almost maximum bandwidth during downloads (3 MB/s for 802.11b for maximum throughput of 11 MB/s or 25 percent of maximum throughput. 

Why the Mac had no problems:  Airport and OSX are kinder to networks and probably have preprogrammed throttling.

Proof of my argument:  use ping from command line and compare to OSX BSD command line.

$ ping -c 5 192.168.0.1

[I]-c 5 sets number of pings to 5.
192.168.0.1 is the internal Ip number of the router. Change to what your router uses.
[/I]

Hope this helps.

:guitar:awesome thanks

---

### Post by sageb1 on 2007-10-08
No, pumping bytes at 54 MB via G protocol is what is causing the router to shutdown.

If you go to 11 MB/s the route will be more stable.  Use a slower wireless LAN adapter, or switch the router to 11 MB/s.

A switching wireless router would be better.

Yes, 11 MB/s will be much reliable.

:guitar:

---

### Post by bogoliubov on 2007-10-08
> **sageb1 said:**
> No, pumping bytes at 54 MB via G protocol is what is causing the router to shutdown.

If you go to 11 MB/s the route will be more stable.  Use a slower wireless LAN adapter, or switch the router to 11 MB/s.

A switching wireless router would be better.

Yes, 11 MB/s will be much reliable.

:guitar:

Ok, but I still have no problems copying files on the LAN, without setting the router to 11 MB/s?! It seems to me that the problem should be something else...

---

### Post by sageb1 on 2007-10-14
LAN traffic is through the wired ports so speed does not saturate the ports. The LAN hardware is designed to handle side effects of 100 Mbps traffic - which usually never is 100Mbps except at peak. Most of the time it is 100/(n+1) percent of 100 Mbps, where n == number of ports used excluding wan port.

It is the wireless part of the router that crashes due to overheating.

---

### Post by bogoliubov on 2007-10-15
> **sageb1 said:**
> LAN traffic is through the wired ports so speed does not saturate the ports. The LAN hardware is designed to handle side effects of 100 Mbps traffic - which usually never is 100Mbps except at peak. Most of the time it is 100/(n+1) percent of 100 Mbps, where n == number of ports used excluding wan port.

It is the wireless part of the router that crashes due to overheating.

But I can copy things from one wired to one wireless computer! Whatever LAN means, this is done through the wireless port.
Copying files locally has never caused the router to hang, but downloading stuff from internet does. To me it would seem to be a problem with the router connecting to the ADSL modem, but I don't know much about this...

---

### Post by htvl5 on 2007-10-21
Hello, I've got the same problem with my wireless Netgear router when Im trying to download things via APT. Then the router hangs... And only if I use the wireless I work just fine with the cable.. I didn't have this problem with debian, so I think this is very very strange. Maybe Ubuntu sends out some strange ACK message that hangs the netgear router?

Does anyone know how to fix this problem?

---

### Post by mblackwell8 on 2007-10-28
i was having the same problems with my netgear wpn 824 router. this is probably not the solution you want to hear, but i replaced it today with a d-link router and have thrown everything at it this afternoon... all the stuff that would quite reliably crash the netgear router (apt-get, update manager, youtube) has no effect on the d-link.

basically the netgear constantly crashed under high traffic from ubuntu (using ipw2200 driver and centrino wireless hardware)

i'd love to know what the problem really is, but from my point of view A$200 to fix the problem and stop needing to reboot the netgear is a good deal!

---

### Post by SpiritIsReality on 2007-10-28
howdy
mblackwell8 ... I was kind of leaning toward that solution too.
we use linksys and dlink, no problems
I'm sure the netgear can be useful as a wireless bridge client or so, a backup, or a challenge in the waiting, not realy wasted. If I was a netgear exec and got a copy of this thread, it'd have the same effect as sitting on a red hot poker.
trails

---

### Post by bogoliubov on 2007-10-31
Yesterday I switched the router to 11Mb/s only. If this makes it more stable, I at least know a little bit more. But I still have to try my wireless card somewhere else to see if it's causing the trouble or not...

---

### Post by bogoliubov on 2007-11-05
As far as I can tell, the router is much more stable when locking it to 11 MB/s. But I don't understand this, since I can copy things locally without any problems (when at 54 MB/s setting), but not from the internet.


Will getting another router solve this?

---

### Post by Lambert on 2007-11-05
> **bogoliubov said:**
> As far as I can tell, the router is much more stable when locking it to 11 MB/s. But I don't understand this, since I can copy things locally without any problems (when at 54 MB/s setting), but not from the internet.


**Will getting another router solve this?**

It's hard to say if another router would solve this. If it's working with another machine I would lean towards no but couldn't say that definitevly.

Try this to see if it help.

If you don't know the interface name, look it up with this command.

```

sudo iwconfig

```

Take that interface name and run this command.

```

sudo iwconfig wlan0 mtu 1400 commit

```

this is just one small possibility of what could be causing problems. 

The router may also contain a log or a way to email a log somewhere to help troubleshoot what is happening. Look in your documentation or search around the web interface of the device.

Check your firmware version. If it's old update to the latest which I see 4.2.11 as the latest for your device. One of the fixes listed is 

> 
Fixes issue with PPPoE that the router loses WAN connection after the ISP clears the circuits ( a reboot of the router was required with older firmware).


this may not be related to you or your problem but it tells me there are some fixes related loss of connection.

[http://kbserver.netgear.com/products/WGT624v2.asp](http://kbserver.netgear.com/products/WGT624v2.asp)

---

### Post by bogoliubov on 2007-11-07
Hmm, this is a bit silly, but it seems that the Netgear automatic search for firmware updates didn't work. Originally I thought that my problems could be solved by updating the router. Since the router had a built-in tool to check for updates, I used this. But now when I looked at the Netgear webpage, it turns out that the update-tool didn't work, because I could find several updates to the firmware.

So, now I just have to wait and see how it behaves!

Thanks alot for the help!

---

