---
title: "WLAN situation is absolutely unacceptable"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by johann_p on 2007-07-25
I find it amazing how easy Linux'ers put up with all the trouble that lacking Linux driver support from hardware vendors cause. I find it utterly unacceptable that vendors like Netgear simply ignore the problem and that Linux users have to rely on either solutions like ndiswrapper or hacked, reverse-engineered drivers by third parties.

I think that might change if hardware vendors realize that there is a potential market and that Linuxers will not simply accept the situation and do the work themselves. I think each and every user who is disappointed by these companies should contact their customer support and complain. Complain about the lack of maintained drivers, about the lack of usable information on the hardware boxes (so that at least the chipset can be found out).

I am especially disappointed by Netgear: their reaction to inquiries has been arrogant to hostile and I will probably simply throw away the stuff I have bought from them.

---

### Post by tgoose on 2007-07-25
The Belkin PCMCIA card is fine - I bought it from linuxemporium for just that reason and as soon as I plug it in it comes up as ra0. The USB equivalent is another story...

Anyway I assumed the Dell Ubuntu machines have internal WLAN and work fine? If that's the case it shouldn't be too hard to use the same chips in other machines.

---

### Post by johann_p on 2007-07-25
> **tgoose said:**
> The Belkin PCMCIA card is fine - I bought it from linuxemporium for just that reason and as soon as I plug it in it comes up as ra0. The USB equivalent is another story...

Anyway I assumed the Dell Ubuntu machines have internal WLAN and work fine? If that's the case it shouldn't be too hard to use the same chips in other machines.

I do not know what driver this uses and who developed/maintains this drivers, but part of what I find unacceptable is that none of these companies actually provides their own drivers but relies on people reverse-engineering drivers (naturally, with the effect that many features or additional program options, or add-on programs available for Windows are non-existent for Linux users).

I find it unacceptable to mess with chipset names and downloading firmware etc. when all that is missing is a the same support for the pricey hardware I bought that I would get for Windows.

I find it unacceptable that obviously Linux users are expected by these companies to go through hacks and write their own drivers and still pay the same amount of money.

I find it disappointing that so many Linux users actually play along with this expectations instead of putting some pressure on these companies.

And I think it is no wonder when people eventually give up  and go with Windows when it is so much hassle and requires so much research to get something as mundane as a WLAN connection to work (but the situation is not different with TV cards, many printers and practically all more exotic hardware).

It looks nearly as if MS would actually pay these companies to show that much arrogance towards Linux users.

---

### Post by madcow72 on 2007-07-25
You know what, Johann_p?  I totally agree with you.  There are numerous things about open-source that I don't totally understand, and you've hit on one of the major ones.  

I'll write D-Link today.  I like the cause.

---

### Post by tgoose on 2007-07-25
> **johann_p said:**
> I do not know what driver this uses and who developed/maintains this drivers, but part of what I find unacceptable is that none of these companies actually provides their own drivers but relies on people reverse-engineering drivers 

They were either written by the chipset manufacturers, or by the OSS community based on an open firmware.

I found the Dell model, it's Intel® 3945 802.11a/g Mini-card. Now I don't know if that's closed or open source, but I know Intel have been working on opening stuff like this. 

> 
(naturally, with the effect that many features or additional program options, or add-on programs available for Windows are non-existent for Linux users).

I don't think that's fair at all: the add-on programmes all seem to be bloatware, for example both Netgear and Belkin replace the perfectly adequate Windows XP wireless connection manager with their own one, which just takes up more resources and looks out of place. I *much* prefer the Linux way, where I wouldn't even know I was using a wireless card except that I can get on the Internet! That even holds for ndiswrapper!

> 
I find it unacceptable to mess with chipset names and downloading firmware etc. when all that is missing is a the same support for the pricey hardware I bought that I would get for Windows.

Absolutely, I couldn't agree more with you there.

> 
I find it unacceptable that obviously Linux users are expected by these companies to go through hacks and write their own drivers and still pay the same amount of money.

Linux **users** yes, Linux **developers** no. I personally don't mind if the community supplies drivers, so long as they work well!

> 
I find it disappointing that so many Linux users actually play along with this expectations instead of putting some pressure on these companies.

And I think it is no wonder when people eventually give up  and go with Windows when it is so much hassle and requires so much research to get something as mundane as a WLAN connection to work (but the situation is not different with TV cards, many printers and practically all more exotic hardware).


> 
It looks nearly as if MS would actually pay these companies to show that much arrogance towards Linux users.
That wouldn't surprise me in the least.

---

### Post by brander on 2007-07-26
M$ will get their comuppance as more and more people switch to Linux which gets more friendly by the minute. Also, their Vista was a terrible mistake and has huge problems mainly associated with copyright protection.

It is still very difficult to persuade users of XP to change to Linux, but as its UI improves and the Linux community continues to make it easier to use despite hardware manufacturers` disinterest , then many Vista users will end up with it.

---

### Post by johann_p on 2007-07-26
> **tgoose said:**
> They were either written by the chipset manufacturers, or by the OSS community based on an open firmware.

I found the Dell model, it's Intel® 3945 802.11a/g Mini-card. Now I don't know if that's closed or open source, but I know Intel have been working on opening stuff like this. 


I think that is interesting information (haven't verified it yet). I think linux distros should give more cudos to those companies that actually support their hardware on Linux (and that includes *closed source* drivers!). I'd rather have my WLAN card work auto-magically with some closed source driver than go through an endless hassle of browsing through crypting HOWTOs, downloading strange tars, messing with kernel modules, figuring out the incompatibilities between network manager, wireless lan GUI and using WPA etc.

Linux distros should provide information about what companies support Linux and what companies suck prominently and visible for everyone so that we can at least make an informed choice when shopping for this. And that does not mean "chipset xxxx" which is not printed on any box anyways.

> 
I don't think that's fair at all: the add-on programmes all seem to be bloatware, for example both Netgear and Belkin replace the perfectly adequate Windows XP wireless connection manager with their own one, which just takes up more resources and looks out of place. I *much* prefer the Linux way, where I wouldn't even know I was using a wireless card except that I can get on the Internet! That even holds for ndiswrapper!
I agree to some extend and I also think that the crap Netgear puts on a customers computer is more than useless. But I was thinking in more general terms here when I compare Windows support and Linux support, and in many cases, the additional programs ARE valuable. For example, my Garmin GPS is practically unusable under Linux -- with a lot of hassle I can transfer raw data to my disk. In comparison, I get graphical mapping programs and much more for Windows and of course, actual topological or routing maps only work under Windows either.

> 
Linux **users** yes, Linux **developers** no. I personally don't mind if the community supplies drivers, so long as they work well!
As a user, I am of course not really concerned where the drivers come from as long as they work well. BUT: many drivers do not work well or not as well as they could, simply because the hardware company not only did not do their homework and develop their own drivers, but they also actively hide information about the hardware. Time and again, linux drivers suffer from the fact that no documentation about the hardware is available. So even if Linux developers invest the work and money of development that should be invested by the hardware manufacturers (from the money I gave them when I bought the hardware), they still cannot compete because they simply do not have the necessary information.

Here some examples: 
* on all computers/laptops (6 in all) I have tried, WLAN does not work with WPA for some reason. on one computer I was partly successful with ndiswrapper, but using that causes hangs of the whole OS.
* My Garmin GPS is practically unusable under Linux
* A wlan bridge cannot be configured without Windows.
* My Canon Powershot camera can be remotely controlled (including a live view of what the camera sees) from Windows, but none of this works from Linux (I am especially pissed off by this one :( )
* Many printers produce inferior results when used from Linux, some do not work at all
* many Combo FAX/Scanner/Printer/Copier devices cannot be used fulyl from Linux
* Bluetooth/IR communication and functions with mobile phones is limited under Linux (e.g. synchronisation of address books, calender etc with some smart phones)

---

### Post by johann_p on 2007-07-26
> **brander said:**
> M$ will get their comuppance as more and more people switch to Linux which gets more friendly by the minute. Also, their Vista was a terrible mistake and has huge problems mainly associated with copyright protection.

It is still very difficult to persuade users of XP to change to Linux, but as its UI improves and the Linux community continues to make it easier to use despite hardware manufacturers` disinterest , then many Vista users will end up with it.
What I brought up here is not a problem or the fault of MS, I think. It is the fault of HW manufacturers and I think Linux users should voice their anger about this towards hardware companies.

Even if Vista might not be as good as expected -- why should people use Linux if their HW does not work properly under Linux? (See my post above for only a short selection of what does not work under Linux, but works under Vista and all other Windows versions).

My argument would be that this can only get better if hardware companies actually hear it from (potential) linux users.

And to some extend, if Linux developers finally give up their silly agenda that everything must be free and open and allow HW manufacterers to provide closed source drivers and DRM protected software: I'd rather use Garmin's protected topological maps on my Linux computer than not use it at all because it only runs under Windows.

---

### Post by srt4play on 2007-07-26
> **johann_p said:**
> * A wlan bridge cannot be configured without Windows.

That's not true.  I've configured many linksys wireless bridges with my Ubuntu laptop.

---

### Post by johann_p on 2007-07-26
> **srt4play said:**
> That's not true.  I've configured many linksys wireless bridges with my Ubuntu laptop.

You misunderstood: I did not say that no wlan bridge can be configured, but that some wlan bridge I have used a while ago could not -- I think it was Netgear, again.

---

### Post by variona on 2007-07-26
> **johann_p said:**
> 
And to some extend, if Linux developers finally give up their silly agenda that everything must be free and open and allow HW manufacterers to provide closed source drivers and DRM protected software: I'd rather use Garmin's protected topological maps on my Linux computer than not use it at all because it only runs under Windows.
I must contradict. Opensource is not a silly agenda.
a) AFAIK you can use closed source drivers at your own risk - providing they match your kernel. Which leads to b)
b) Each kernel upgrade could lead to inoperability of the driver, as it would be the hardware manufacturers duty to compile a new driver. You probably know that there are many flavours of linux out there. OTOH windos comes with less kenel updates (i.e new versions) therefore it is easier to provide drivers - but if you'd like to use windows 3.1 or windows 98 you'd be amazed how little hardware support you get!
c)HW manufacturers don't like to open their code as it would give away too much of their development secrets too soon.
Correct me if I'm wrong
variona

---

### Post by srt4play on 2007-07-26
I'd like to add to variona's last post that AFAIK Linux developers are not preventing hardware manufacturers from providing drivers whether they be closed-source or open. The hardware vendors are the ones with the silly agenda because there is no excuse for not being able to provide drivers for an open source OS.  The only reason they can give is that the user base is too small so it's not worthwhile.

---

### Post by johann_p on 2007-07-26
> **variona said:**
> I must contradict. Opensource is not a silly agenda.

I did not say that and I am somebody who actively promotes OS and contributes to OS projects.
What I said is that it is a silly agenda trying to force everyone to use/develop OS and this is what a part of kernel developers and prominent OS people actually do.

> 
a) AFAIK you can use closed source drivers at your own risk - providing they match your kernel. Which leads to b)
b) Each kernel upgrade could lead to inoperability of the driver, as it would be the hardware manufacturers duty to compile a new driver. You probably know that there are many flavours of linux out there. OTOH windos comes with less kenel updates (i.e new versions) therefore it is easier to provide drivers - but if you'd like to use windows 3.1 or windows 98 you'd be amazed how little hardware support you get!

This is why providing a stable, well-documented, safe interface for HW vendors to plugin closed source drivers should be of utmost importance in Linux development. Unfortunately, the opposite is happening, with people who have an agenda trying to enforce driver-openness.

Again, personally I would love to see every HW manufacterer provide an open, well documented driver for each peace of their hardware, but anyone who thinks this is realistic or it is realistic to *force* companies to do that is just incredibly naive. And counterproductive when it comes to making Linux more relevant as an OS competitor on the desktop.

> 
c)HW manufacturers don't like to open their code as it would give away too much of their development secrets too soon.

Exactly. More often than not, this might just be some cheap excuse or PR gag, but still: invite and motivate them to provide OS drivers, but do not force them. Make it easy to allow for the coexistence with closed source drivers. This is happening to some extend with the NVidia driver in Ubuntu.

The bottom line should of course be that an end user need not bother about drivers at all.

> 
Correct me if I'm wrong
variona

Who am I to do that -- I dont know a thing myself. I know what I would like though: I would like to continue using Linux and be able to use those WLan cards, printers, GPS devices, cameras, just as and with the same range of features as Windows users.
And I would like Linux developers to work towards that goal, not towards an utopia of everything being GPLV3 compatible open source.

---

### Post by Saner on 2007-07-26
Do Netgear really not provide drivers ?


thats laughable when the base of one of my netgear routers is linux

---

### Post by johann_p on 2007-07-26
> **Saner said:**
> Do Netgear really not provide drivers ?

Well, the simplest thing would be you send them an email and ask them :)

---

