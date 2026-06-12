---
title: "Which &quot;flavor&quot; of Ubuntu Is Best For This Machine"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by cbreezy on 2009-07-01
I have a super old Compaq Presario that I think I could use to run Ubuntu server. Which flavor/version of Ubuntu woud work on the following machine?
 
**Compaz Presario 5190 Minitower**
**Processor: .............. 400 MHz AMD-K6-2 processor with 3DNow! Technology**
 
**Cache: ...................................... 512KB L2 Pipeline Burst Cache**
**System Memory: .............. 128 MB 100 MHz SyncDRAM, upgradable to 384 MB**
**(SyncDRAM DIMM required)**
**Hard Drive: ................................ 10.0 GB(2) UltraDMA hard drive**
**DVD-ROM Drive: ............................ 3rd-Generation DVD-ROM drive(3)**
**System Bus: ....................................... Fast 100 MHz System Bus**
 
Entire specification found at [http://support.radioshack.com/support_computer/doc50/50695.htm](http://support.radioshack.com/support_computer/doc50/50695.htm)
 
I want to use it solely as a server for linux-compatible apps that I'll develop on a different machine, so no GUI necessary.
 
Also, is this at all a feasible plan? 
 
Thanks a heap!:)

---

### Post by psychicsaw on 2009-07-01
I have a similar Presario that I've Linux-loaded for someone in an office.. It runs 9.04 just fine.

---

### Post by Geoff918 on 2009-07-01
Why not use the server edition if you'll be using it solely as a server? I'm assuming that's your question and you're not asking which Ubuntu version number to use.  I've used the server edition successfully for some file hosting on a project I'm working on with a pretty old (comparable to your machine specs) system. I won't claim response is fleet by any means, there's a noticeable lag of a half-second or so after command entry. The server edition seems to be pretty light on resources as even with my 384 MB of RAM the system rarely uses more than a few percent on idle and the most I've ever seen it use is around 40% of available RAM.  My system is very stable, though you can virtually watch programs compile as the hardware is pretty old. Overall, still a viable setup for what it seems you're hoping to accomplish.  I hope this helps!  Geoff  EDIT: It seems you are asking the version number when I re-read your post. I have used 8.04 LTS, 8.10, and 9.04 all successfully on this system.

---

### Post by lemuriaX on 2009-07-01
For a server, why not just use the current LTS - Hardy.

---

### Post by cbreezy on 2009-07-01
Hmm...I guess I assumed that the server install of Ubuntu would have a version number since the desktop install does. Is that correct...i.e. is there an Ubuntu Server 9.04 AND an Ubuntu Desktop 9.04? I'm clearly a newbie still getting the lingo straight. I know I want the server install because I only want to use it for server-like purposes. But that's all that I'm sure of. Flavor and Version are in question. Example: Could there be a Xubuntu Server 7.04 and a Xubuntu Desktop 7.04? Let me know if I need to rephrase that for clarity...

---

### Post by steigerjb on 2009-07-01
> **cbreezy said:**
> I have a super old Compaq Presario that I think I could use to run Ubuntu server. Which flavor/version of Ubuntu woud work on the following machine?
 
**Compaz Presario 5190 Minitower**
**Processor: .............. 400 MHz AMD-K6-2 processor with 3DNow! Technology**
 
**Cache: ...................................... 512KB L2 Pipeline Burst Cache**
**System Memory: .............. 128 MB 100 MHz SyncDRAM, upgradable to 384 MB**
**(SyncDRAM DIMM required)**
**Hard Drive: ................................ 10.0 GB(2) UltraDMA hard drive**
**DVD-ROM Drive: ............................ 3rd-Generation DVD-ROM drive(3)**
**System Bus: ....................................... Fast 100 MHz System Bus**
 
Entire specification found at [http://support.radioshack.com/support_computer/doc50/50695.htm](http://support.radioshack.com/support_computer/doc50/50695.htm)
 
I want to use it solely as a server for linux-compatible apps that I'll develop on a different machine, so no GUI necessary.
 
Also, is this at all a feasible plan? 
 
Thanks a heap!:)

You don't have enough memory for ubuntu. Minimum is 265mb i believe. You could try xubuntu

---

### Post by steigerjb on 2009-07-01
oh, i just saw you upgraded, nevermind.

go ahead and try ubuntu 9.04 desktop edition

---

### Post by lemuriaX on 2009-07-01
> **cbreezy said:**
>  is there an Ubuntu Server 9.04 AND an Ubuntu Desktop 9.04? 

Yes. And the Xubuntu, Kubuntu flavor varieties refer to the different Desktop environments (XFCE and KDE respectively) of the desktop, Gnome being the default for regular Ubuntu.

---

### Post by Geoff918 on 2009-07-01
No, there's only one server version. The "versions" you're discussing are windows managers. Ubuntu uses GNOME, Kubuntu uses KDE, Xubuntu uses XFCE, etc. But, for a server none of these are run, and indeed the kernel is tweaked a bit differently as well, e.g. it is 2.26...-server instead of 2.26.....-generic or whatever.  The server version is what you want if you're running a server simply because the memory and disk caching and all are geared a bit differently (at least that's my understanding, don't quote me on that).

---

### Post by lemuriaX on 2009-07-01
Check out the server guide for whichever release you want to use, for 8.04 it's here:

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

I think you can run a Ubuntu server on 128 megs of RAM -- it says here it's the minimum required:

[https://help.ubuntu.com/8.04/serverguide/C/preparing-to-install.html#system-requirements](https://help.ubuntu.com/8.04/serverguide/C/preparing-to-install.html#system-requirements)

That being said, I would upgrade the RAM though.

---

### Post by bekind2thenoob on 2009-07-01
Other Ubuntu flavours Kubuntu and Xubuntu use different desktop environments.

These are collections of applications (from window managers to file managers to web browsers) which make up the graphical desktop (GUI) which most users choose to interact with.

If you strip away the applications each version uses they are identical underneath, the core system that does all the "work under the hood" so to speak is the same in all flavours.

So... Kubuntu Ubuntu and Xubuntu dsktop editions only vary in the interface.

As Ubuntu's server edition has no GUI in a default install (only a command line interface) there is only one "flavour".

...Ubuntu server

---

### Post by steveneddy on 2009-07-01
I've done the same thing with an old desktop machine and use Harder Server version for the sole fact that it is the LTS version.

Previously I ran 6.06 LTS version, again, solely for the reliability of an LTS for my server.

---

### Post by lemuriaX on 2009-07-01
To be clear, while there are different releases for Ubuntu server, 8.04 8.10 9.04 - the "flavors" like Xubuntu refer to Desktop environments and so don't apply to the server version since there is no GUI by default (though one could be added if someone wanted to do that).

---

### Post by steveneddy on 2009-07-01
I also meant to add that if you need a GUI, then just add

Ubuntu Desktop

```
sudo apt-get install ubuntu-desktop
```

---

### Post by cbreezy on 2009-07-01
Thanks for the feedback, everyone. I think I've got the whole flavor/version confusion straight now. So I don't need to concern myself with Kubuntu, Xubuntu, etc because I want a server install of Ubuntu. So the only question is which release of Ubuntu Server will work on my machine. 
 
I plan to upgrade the RAM but it maxes out at way below 512MB RAM capacity. It's max is something like 343MB.
 
It looks like Ubuntu Server 8.04 will work for me, but what does "LTS" mean?

---

### Post by halitech on 2009-07-01
since you won't be running a GUI then 384 should be fine as you won't be "wasting" any on the desktop.

LTS = Long Term Support

Every few versions the devs decide they are going to completely freeze everything (except updates) and go in a new direction with things. It gets called an LTS version and gets longer support on the desktop and the server.

---

### Post by bekind2thenoob on 2009-07-01
There are two types of Ubuntu release...

"standard" releases are supported (as in security and bugfixing updates are provided by canonical) for 18 months.

LTS or Long Term Support releases are supported for longer 8.04 was the last LTS release and was released in April 2008, it is supported until 2013 on servers.

LTS releases are considered more stable by dint of there maturity compared to standard releases.

---

### Post by cbreezy on 2009-07-01
Ah, I see. I think I've got it now. Thanks, Ubuntu community...now off to buy some memory

---

### Post by stinger30au on 2009-07-01
> **cbreezy said:**
> Ah, I see. I think I've got it now. Thanks, Ubuntu community...now off to buy some memory

good idea

the 10 gig hdd wont worry you, i have crammed ubuntu on to a 4 gig ide hdd before and it ran good enough for what i was needed for

---

