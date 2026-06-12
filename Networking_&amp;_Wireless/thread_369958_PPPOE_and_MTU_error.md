---
title: "PPPOE and MTU error"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by yme on 2007-02-25
Hello:

I have a new Ubuntu installation I've been playing with this week. From the fresh install I had no problem running pppoeconf at the terminal and connecting. 

But the next time I start up the connection doesn't work. I've tried rerunning pppoeconf and on the second screen get a warning that my MTU is 1492 and it should be 1500 and that I might have serious connection problems.

What is going on? I don't want to have to reinstall every time I want to use the internet :) 

me!

---

### Post by zvacet on 2007-02-25
[http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe]("http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe")

---

### Post by yme on 2007-02-26
> **zvacet said:**
> [http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe]("http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe")

I saw this How to but it simply presumes that the pppoeconf installed as standard with Ubuntu is no good and that you need a different programme. 

Perhaps there is a simple fix? Some option to change MTU perhaps?

---

### Post by Rui Pais on 2007-02-26
hi,
check if [this article]("http://glasnost.beeznest.org/articles/290") can help you.

good luck.

---

### Post by yme on 2007-03-03
> **Rui Pais said:**
> hi,
check if [this article]("http://glasnost.beeznest.org/articles/290") can help you.

good luck.

At the moment every time I want to access the internet I am reinstalling Ubuntu. It gives in the MTU error message when I run pppoeconf but it still works immediately although not on the next startup. 

I tried:
/sbin/ifconfig eth0 mtu 1492

It didn't work immediately but did when I next restarted. Restart after that it didn't. Back to reinstalling ...

I'd be grateful for some help with understanding, at a basic level, what is going on and why. Also some explanation of what to do for someone who is not initiated into the mysteries of the terminal.

---

### Post by Mr. C. on 2007-03-03
> **yme said:**
> At the moment every time I want to access the internet I am reinstalling Ubuntu. It gives in the MTU error message when I run pppoeconf but it still works immediately although not on the next startup. 


Reinstalling Ubuntu ? Huh?

> **yme said:**
> 
I tried:
/sbin/ifconfig eth0 mtu 1492

This affects the interface now, not upon reboot.  Other connected ethernet devices will learn this as well (like switches, routers, etc.), and they will retain this information until told otherwise.

> **yme said:**
> 
It didn't work immediately but did when I next restarted. Restart after that it didn't. Back to reinstalling ...


This takes affect as soon as other devices learn of the change as well.  And bring the device down and up with the correct MTU will ensure other devices see it.

> **yme said:**
> 
I'd be grateful for some help with understanding, at a basic level, what is going on and why. Also some explanation of what to do for someone who is not initiated into the mysteries of the terminal.

You need to configure the correct configuration file by adding the MTU value you wish set when the devices is brought up.

MrC

---

### Post by yme on 2007-03-05
> **Mr. C. said:**
> You need to configure the correct configuration file by adding the MTU value you wish set when the devices is brought up.

As /sbin/ifconfig eth0 mtu 1492 has only worked one of the many times I have tried it, it seems a bit pointless to start trying to 'configure the correct configuration file'. If trying that at the prompt doesn't solve things mucking around with configuration files seems unlikely to.

What I want to understand is why my connection always works when I have freshly installed but does not work on further start-ups? 

And why is the level of MTU is an issue, am I not offered an option of setting it when I run pppoeconf? 

me!

---

### Post by yme on 2007-03-13
I've tried following the guide posted above but the connection still doesn't work. It only works on the first try after a fresh reinstall and then once, but only once, if I type the following in the terminal:
/sbin/ifconfig eth0 mtu 1492

After that nothing will get me a connection and I have to reinstal! I have tried altering etc/network/interfaces. It looks like this when I open it:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf 

In the last line after 'up' I add 'MTU 1492' as the guide suggests but this has no effect.

me!

---

### Post by Rui Pais on 2007-03-13
> **yme said:**
> I've tried following the guide posted above but the connection still doesn't work. It only works on the first try after a fresh reinstall and then once, but only once, if I type the following in the terminal:
/sbin/ifconfig eth0 mtu 1492

After that nothing will get me a connection and I have to reinstal! I have tried altering etc/network/interfaces. It looks like this when I open it:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf 

In the last line after 'up' I add 'MTU 1492' as the guide suggests but this has no effect.

me!
hi again,
i point you to that article to you see how you may change the mtu on your network config file. 
It was supposed that you adapt to your needs.

You say in your fist post that your mtu are 1492 and it warnings you it should be 1500, so adding mtu 1492 it only gives what you already have :)

You should add mtu 1500 and maybe it needs to be before the ifconfig line (don't know if that matters...) 
try editing to:

> auto eth0
iface eth0 inet dhcp
mtu 1500


reboot (to be sure that your hardware setting are redone) and check if it works.



btw, what do you mean by reinstall? Do you reintall the all ubuntu?!?

---

### Post by yme on 2007-03-16
> **Rui Pais said:**
> It was supposed that youYou say in your fist post that your mtu are 1492 and it warnings you it should be 1500 

Yes, I did try both. The guides seem to presume you want it to be 1492 and I can't find anywhere anything about a problem that requires it to be 1500.


> **Rui Pais said:**
> You should add mtu 1500 and maybe it needs to be before the ifconfig line (don't know if that matters...)  

I put it just where you suggested, after eth0 but no luck after rebooting.. 

> **Rui Pais said:**
>  btw, what do you mean by reinstall? Do you reintall the all ubuntu?!?

Yes! It seems clear that the settings are OK in the default and reinstalling seems to be the only way to get them. Stupid I know but there seems to be no other way to get internet at the moment! Btw, I used Fedora3 for six months and had many glitches and problems but not this one ....

I can't understand why there is no nice GUI interfaces that can be used to do all the pppoe settings. The only one I can find is for ppp dialup ...

---

### Post by yme on 2007-03-26
I’m still totally stuck on this one and having to reinstall - yes, reinstall - in order to get a working internet connection!

Wikipedia’s entry on MTU doesn’t answer any of my questions:
[http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)

I can’t see why the pppoeconf program suggest that my MTU should be 1500 when all of the online how-tos presume you want it to be 1492. What is the big deal about those 8?

Why does my system work when freshly installed and not later? Is my ISP resetting something? pppoeconf does get them to set the DNS …

I found an MTU debug programme but can’t see this is any use as pppoeconf is already telling me how things should be, the problem is getting them that way:
[http://www.elifulkerson.com/projects/mturoute.php](http://www.elifulkerson.com/projects/mturoute.php)

Finally, why was everything OK with Fedora3 and not with Ubuntu?

---

### Post by Mr. C. on 2007-03-26
Your rhetorical question about "What is the big deal about those 8?" is about as silly as saying what's the big deal about trying to fit 8 more gallons/litres in a fixed-sized fuel tank.

Without understanding how packets are created, MTU will be meanless to you.

For a quick overview, see week 1 and week 2 Notes "CP/IP Networking Intro" and "Data Delivery" at:  [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

Because PPPoE is another encapsulation layer, MTU must be reduced to prevent fragmentation.  The PPPoE encapsulation data requires... guess what.... 8 bytes.

To avoid fragmentation, your PPPoE host must communicate to its partner that it cannot handle payloads larger than 1492 w/out fragmentation. 

If you really want the good details: [http://www.ietf.org/rfc/rfc2516.txt](http://www.ietf.org/rfc/rfc2516.txt)

MrC

---

### Post by yme on 2007-05-29
There must have been some bug in Dapper as as soon as I switched to Feisty the whole problem disappeared ....

---

