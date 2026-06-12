---
title: "can a VM give my Ubuntu a virus???"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by Johnny420 on 2010-12-22
I hate w*****S but i need an xp machine for some stuff that my friend sends me to work on so I am installing a Virtual xp slow (pro) and as I was watching it install IT hit me that I might be opening myself up to viruses and the like. SO can my  VM xp give my ubuntu viruses? should I worry about anti virus on a VM if so I'm just gonna have to figure out another way because I love the felling of security that linux has given me for free (and a small donation)..lol while microsoft charged me an arm and a leg to get raped by viruses wearing trojans...lol

---

### Post by cariboo on 2010-12-22
Windows viruses won't have any affect on your Ubuntu installation. The thing to do is create a snapshot just after doing the xp install, so you've always got a clean system if you need one.

---

### Post by sammiev on 2010-12-22
It's possible that you can send your friend a virus. LOL If sending files back to a windows base system, it's only right to scan it with a virus detection 1st unless you don't care about your friend. :popcorn: Viruses seem to have little to no effect on Linux but can be passed from Linux to windows. GL :)

---

### Post by Johnny420 on 2010-12-23
Thanx for the advice and I hadn't thought far enough ahead to think about sending him a virus so good looking out 
And I just wanted to say that i spent years on w*****s machines and never had a community that helped one-another out like this and I think that I love all of you :P

---

### Post by amjjawad on 2010-12-23
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by Johnny420 on 2010-12-23
any suggestions on other distros a NooB should run 
right now I'm very happy with Ubuntu but I would like to try some of the other flavors to see what else tastes good

---

### Post by amjjawad on 2010-12-23
> **Johnny420 said:**
> any suggestions on other distros a NooB should run 
right now I'm very happy with Ubuntu but I would like to try some of the other flavors to see what else tastes good

[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by waynefoutz on 2010-12-23
If you are running Windows in a VM like Virtualbox, on a Linux host,or even a Windows host, the  Windows guest OS can get a virus, but, it cannot leave the virtual machine. So no, it cannot infect the host OS. It's the same reason you cannot move or copy a file from your desktop into the desktop of the virtual machine. Nothing gets in, nothing gets out

---

### Post by zigzag77 on 2010-12-23
Virtual machines can also be virus infected and can also be part of bot networks. Virtual machines can also send spam and can be part of cyber attack networks. They can do all the things that physical machines can do.

From a botnet commander's point of view, he is as happy to infect your virtual machine as he would be to infect your physical machine.

Once in a while, virtual machine host software has vulnerabilities that allow an attacker to break out and infect the host. In case of zero day exploits, you have no chance to protect your host.

So be careful and protect your virtual machine as well as you would protect a physical machine. You might consider some of the following:

[LIST]
[*]Isolate the virtual machine from the network if possible
[*]Do not share directories or USB media
[*]Regularly use virus and malware scanners
[*]Regularly apply security patches
[*]Harden the machine
[*]Do not use accounts with admin privileges, if not necessary
[*]Limit surfing to safe sites 
(even safe sites have been distributing drive-by malware that infected clients just by visiting the site...)
[*]Start over from safe snapshots
[/LIST]
If you follow these tipps, your virtual machine is safe, but is maybe not very useful... You have to find a compromise between security and usefulness for yourself.

---

### Post by zigzag77 on 2010-12-23
I think one part of the initial question was: Are there any reports of malware and root kits for Linux / Debian / Ubuntu? Or of Linux machines unintentionally being part of botnets?

---

### Post by Sotanaht on 2012-01-05
> **zigzag77 said:**
> I think one part of the initial question was: Are there any reports of malware and root kits for Linux / Debian / Ubuntu? Or of Linux machines unintentionally being part of botnets?

I could use an answer to this question, because I'm thinking of infecting my own windows vm because I'm curious about the viruses I've avoided getting for so long.  I'd restore a backup afterwards, so no harm would be done.

---

### Post by sffvba[e0rt on 2012-01-12
> **Sotanaht said:**
> I could use an answer to this question, because I'm thinking of infecting my own windows vm because I'm curious about the viruses I've avoided getting for so long.  I'd restore a backup afterwards, so no harm would be done.

As this is an old thread and not going anywhere I would suggest starting a new one if you want to pursue this course of action.

Thread closed.


404

---

