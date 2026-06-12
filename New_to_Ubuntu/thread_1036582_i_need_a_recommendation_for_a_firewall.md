---
title: "i need a recommendation for a firewall"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by overclock17 on 2009-01-11
hi
im new to ubuntu i had formated my machine and installed ubuntu 8.10 on it
if someone could recommend me a good firewall for it and how i install it
also if there is any other software i should install?
thank you

---

### Post by tuxxy on 2009-01-11
ufw is recommended, open terminal and type ufw for commands and usage.  Also if you prefer a GUI there is gufw.

Note that these firewalls differ from what you will be used to in Windows, you will not have to configure it unless you plan on running services.

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by jerome1232 on 2009-01-11
iptables is installed by default and allows all connections by default. There are no services listening for connections from the Internet by default on Ubuntu. Generally a desktop won't have much use for a host based firewall.

There are a number of utilities to configure iptables. UFW is installed by default, gUFW can be found here [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

For info on ufw take a look at it's man page```
man ufw
``` and take a look at this guide [http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

---

### Post by overclock17 on 2009-01-11
thanks
how do i open  the terminal?

---

### Post by 3rdalbum on 2009-01-11
> **overclock17 said:**
> hi
im new to ubuntu i had formated my machine and installed ubuntu 8.10 on it
if someone could recommend me a good firewall for it and how i install it
also if there is any other software i should install?
thank you

If you have an ADSL modem/router then you likely already have a firewall protecting your whole network.

You don't need a firewall unless you're planning on using software that listens for incoming connections - for instance, an FTP server or web server.

---

### Post by Tatty on 2009-01-11
> **overclock17 said:**
> thanks
how do i open  the terminal?

Applications->Accessories->Terminal

---

### Post by networm1230 on 2009-01-11
hello! and welcome to ubuntu. to get a firewall on ubuntu is vary easy hear are the steps to get a firewall.  1. go to Applications go down to you see add/remove
 click on it. 2. now click all on the lift upper side. 3. now where it says show click on all available Applications. 4. now on the search tool bar type firewall you shod see three firewall software that you can install on your PC. I me using firestarer on my PC.

I hop this helps you

---

### Post by tuxxy on 2009-01-11
> **networm1230 said:**
> hello! and welcome to ubuntu. to get a firewall on ubuntu is vary easy hear are the steps to get a firewall.  1. go to Applications go down to you see add/remove
 click on it. 2. now click all on the lift upper side. 3. now where it says show click on all available Applications. 4. now on the search tool bar type firewall you shod see three firewall software that you can install on your PC. I me using firestarer on my PC.

I hop this helps you

Firestarter is discontinued I believe and ufw is the new inbuilt firewall.  Both of these do the same job of allowing you to configure your IPtables.

---

### Post by Martin Marshalek on 2009-01-11
Actually, Ubuntu already has a firewall that, for most purposes, does not need to be messed with. Also, since you don't dual-boot and most viruses are for Windows, anything you get won't affect you.

---

### Post by kansasnoob on 2009-01-11
> **overclock17 said:**
> thanks
how do i open  the terminal?

Go to Applications > Accessories > Terminal and since this is 8.10 just cut-n-paste into terminal:

```
gksudo gufw
```

Or go to System > Administration > Firewall Config ....

You should see this:

[ATTACH]99442[/ATTACH]

Just make sure that it's "ticked" on!

That is unless you have a complicated network or something!

If gksudo gufw shows nothing then run:

```
sudo apt-get install gufw
```

And repeat! (I don't recall if gufw is installed by default or not).

It can also be downloaded in a .deb:

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

### Post by networm1230 on 2009-01-11
fire starer is working fine look in [http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by kansasnoob on 2009-01-11
Firestarter was last updated in 2005:

[http://sourceforge.net/projects/firestarter/](http://sourceforge.net/projects/firestarter/)

---

### Post by jerome1232 on 2009-01-11
> **kansasnoob said:**
> Firestarter was last updated in 2005:

[http://sourceforge.net/projects/firestarter/](http://sourceforge.net/projects/firestarter/)

That's what I was about to say :p

---

### Post by networm1230 on 2009-01-13
> **kansasnoob said:**
> Firestarter was last updated in 2005:

[http://sourceforge.net/projects/firestarter/](http://sourceforge.net/projects/firestarter/)

I did not know that. I was shore it was still active on updates. thinks man for the hades up.

---

### Post by handydan918 on 2009-01-13
Okay, so firestarted hasn't been updated in a couple years.

So? 
No, really. So what? Are you worried that the code for firestarter may, after all these years, have an undiscovered buffer-overflow vulnerability?

What, then? 

It's just a gui program for configuring iptables. What updates do you want? Different window decorations?

---

### Post by jerome1232 on 2009-01-13
Well as iptables get's new features, firestarter won't be able to take advantage of them.

---

### Post by handydan918 on 2009-01-13
Okay. That at least sounds reasonable.


Any new features in iptables in the last 5 years?

---

### Post by networm1230 on 2009-01-13
> **handydan918 said:**
> Okay, so firestarted hasn't been updated in a couple years.

So? 
No, really. So what? Are you worried that the code for firestarter may, after all these years, have an undiscovered buffer-overflow vulnerability?

What, then? 

It's just a gui program for configuring iptables. What updates do you want? Different window decorations?

Is there a firewall that I can us. that you know of?

---

### Post by handydan918 on 2009-01-14
> **networm1230 said:**
> Is there a firewall that I can us. that you know of?
The core of linux, the kernel, has a component called "iptables". 
iptables routes muchof the internet traffic in the world. It's just fine. 
It's already on your system. If youwant to configure it without learning a foreign language, you'll want a program like guraddog, firestarter or ufw. 

The real issue is that you probably don't need any of this stuff, because unlike windows, Ubuntu isn't sitting there waiting for someone to come sniffing around looking for an open port. There aren't any. 
Also, if you are behind a router, you are already pretty safe.
In short, if your paranoia meter is in the red, check out the programs I suggested, or just search synaptic for "firewall".
Otherwise, relax. Enjoy your system.

):P

---

### Post by bodhi.zazen on 2009-01-14
> **handydan918 said:**
> Okay, so firestarted hasn't been updated in a couple years.

So? 
No, really. So what? Are you worried that the code for firestarter may, after all these years, have an undiscovered buffer-overflow vulnerability?

What, then? 

It's just a gui program for configuring iptables. What updates do you want? Different window decorations?

Firestarter gives access to a limited set of what iptables is capable of , but if it serves your purpose then there is no reason to change.

The major problem with an application no longer under development, IMO, is bug fixes. If you discover a bug in Firrestarter it will not be fixed.

I have found many bugs in firestarter and it will often fail with complex firewall needs such as NAT and virtualization. Because there will continue to be changes in teh linux kernel and iptables there may come a time when firestarter will no longer work on Ubuntu and/or, now that ubuntu is using ufw, will be droped from the repositories.

As has been pointed out, ufw is the default tool in Ubuntu and the gui tool gufw is in the repositories. When you have the time or interest in trying something new consider taking gufw for a spin. It is fairly similar to Firestarter and you might like it, and if so you will have better support going forward.

---

### Post by bodhi.zazen on 2009-01-14
> **overclock17 said:**
> hi
im new to ubuntu i had formated my machine and installed ubuntu 8.10 on it
if someone could recommend me a good firewall for it and how i install it
also if there is any other software i should install?
thank you

In order to answer that question we need to know what you want to use a firewall for.

Most desktop users are behind a router and most routers already serve as a firewall. In addition a default installation of Ubuntu has no open ports. So for most people a firewall is not necessary.

> **networm1230 said:**
> Is there a firewall that I can us. that you know of?

ufw or gufw

but again, what are you wanting a firewall to do for you ?

---

### Post by handydan918 on 2009-01-14
> **bodhi.zazen said:**
> Firestarter gives access to a limited set of what iptables is capable of , but if it serves your purpose then there is no reason to change.That was sort of what I was thinking....It just seems sorta silly for people to act as though it has been officially deprecated just because development has ceased.> 
The major problem with an application no longer under development, IMO, is bug fixes. If you discover a bug in Firrestarter it will not be fixed.
I'm used to that, I used windows since 3.1> 
I have found many bugs in firestarter and it will often fail with complex firewall needs such as NAT and virtualization. Because there will continue to be changes in the linux kernel and iptables there may come a time when firestarter will no longer work on Ubuntu and/or, now that ubuntu is using ufw, will be droped from the repositories.

As has been pointed out, ufw is the default tool in Ubuntu and the gui tool gufw is in the repositories. When you have the time or interest in trying something new consider taking gufw for a spin. It is fairly similar to Firestarter and you might like it, and if so you will have better support going forward.


Appreciate your thoughtful reply. I have little interest in using a (O/S-based) firewall since I am behind a NAT router, and have never in the last decade of Linux use suffered an intrusion.

---

### Post by 73ckn797 on 2009-01-14
I recommend not worrying about it at all.

---

