---
title: "VERY basic information"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by dragonfathom on 2010-12-15
Hi.

I'm honestly not sure if this goes here, but I'm looking for advice. I'm a high school student and recently obtained a laptop (that runs Windows 7). I was wondering about the pros and cons of using Linux- I am tossing it up between Ubuntu and Debian.

I would still like to play games on it, what is Ubuntu like in that field?

Sorry if this shouldn't be here,

Max.

Edit: I'm choosing to use Wubi. It's the sort of thing that I'm looking for.

---

### Post by mastablasta on 2010-12-15
windows based games are so so, there arent' many linux clients for games. some work through wine.
 
what you can do is free up some of the disk space, install ubuntu there. that way you will have both systems on your computer and you can use windows for games and ubuntu to learn something new....
 
have a look at Ubuntu manual linked in my signature to find out more. though manual is for 10.04 LTS, the 10.10 has a bit different install screens/options. most other things are the same and still valid. besides you can go with 10.04 firts it iwll be supported for the next 3 years, while 10.10 (which is not LTS) will be supported 18 months, but has slightly newer drivers and such. choice is yours. 
 
If you go Debian go with Squeeze, it's already in the freeze status and there are now just making it more stable and removing bugs. Lenny is quite old now.
 
EDIT: if you intend to go dual system, it is better to resize the disk with windows disk manager since you are using win7. with XP ubuntu did itperfectly but win7 there were some issues reported.

---

### Post by Rubi1200 on 2010-12-15
Dual-boot sounds like the best option for you.

As mastablasta already said, you need to create the partitions in Windows first, but leave them unformatted for the Ubuntu installer.

Here is some more information:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by NCLI on 2010-12-15
Go with Debian if you value stability over everything else, and with Ubuntu if you like stability, but would also like some up-to-date application. I'd recommend Ubuntu for most people.

I would recommend trying a Live CD of Ubuntu 10.04, the latest long-term support release, and see how it works for you :) The LTS versions are supported for 3 years, and are considered very stable. Once you've gotten used to working with it, you can upgrade to the latest standard release, 10.10, if you feel like it.

---

### Post by cascade9 on 2010-12-15
> **NCLI said:**
> Go with Debian if you value stability over everything else, and with Ubuntu if you like stability, but would also like some up-to-date application. I'd recommend Ubuntu for most people.

Or you can use debian testing/unstable (not that 'unstable' is unstable). That way you get much much newer programs than 'stable'. Of course, a rolling release (like debian  'testing' or 'unstable') isnt for everybody....

BTW, before somebody tells my that testing/unstable arent 'true' rolling releases....if you want to split hairs I'm not going to stop you ;)

---

### Post by bob-linux-user on 2010-12-15
If you are new to Ubuntu you might also want to consider installing via Wubi instead of doing all the repartitioning. Whatever you do, run a live CD first, that will give you a feel for Ubuntu but remember that an installed Ubuntu (whether the normal way or through Wubi) will be a LOT faster and more responsive than the live CD running.

---

### Post by NCLI on 2010-12-15
> **cascade9 said:**
> Or you can use debian testing/unstable (not that 'unstable' is unstable). That way you get much much newer programs than 'stable'. **Of course, a rolling release (like debian  'testing' or 'unstable') isnt for everybody....**

BTW, before somebody tells my that testing/unstable arent 'true' rolling releases....if you want to split hairs I'm not going to stop you ;)
Which is why I'm not recommending it to a user who is new to Linux.

---

### Post by Zzl1xndd on 2010-12-15
If you are new I would probably select Ubuntu (or perhaps LMDE) over Debian.

As for gaming on Linux, Contrary to what most will tell you its rather good. However like many things in Linux will likely have to look for Alternatives to games you already enjoy. 

I have approx 35 commercial games on my Linux box. I am not using Wine all of these games have a Linux Version (Although some of the Vendors used Wine for their Linux port).

---

### Post by NCLI on 2010-12-15
Since we're talking about games, hurry up and buy [this]("http://www.humblebundle.com")!!!

They work on Linux, Windows and Mac.

---

### Post by cascade9 on 2010-12-16
> **NCLI said:**
> Which is why I'm not recommending it to a user who is new to Linux.

I've got people onto debian testing over ubuntu a few times....Its not that bad, most of the breakage occcurs on 'sid', and in some ways its easier to deal with lots of small updates than to deal with moving from one ubuntu to the next.

---

### Post by QLee on 2010-12-16
[QUOTE=cascade9]I've got people onto debian testing over ubuntu a few times....Its not that bad, most of the breakage occcurs on 'sid', and in some ways its easier to deal with lots of small updates than to deal with moving from one ubuntu to the next.[/QUOTE]

I would partially agree with you about Debian testing. It's true when testing is close to release, and especially when frozen close to release. Just after release though, when the old Sid has migrated into the new codename as the new testing, it can be fairly volatile. I have seen big surprises happen, for users who have used "testing" rather than the codename in their sources list, and the accompanying posts for help in the Debian forums .

---

### Post by amjjawad on 2010-12-16
There are the long way and the short way, your call to choose one or both :)

The Short way: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
This page will tell you everything you need to get the Live CD or Live USB.

Make sure your BIOS boots CD/USB first and boot from the LiveCD/USB.
DO NOT install Ubuntu, just have a look. No changes will be made on your machine whatsoever except your BIOS Settings, I mean your machine will boot first from the CD/USB which should be the default option if you ask me.

The Long way (which will end up sooner or later with the Short way):
[https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

And the short way


IMHO, one should start reading about Linux/Ubuntu before anything else. 

Now, your call to take whatever way you like ;)

---

### Post by cascade9 on 2010-12-17
> **QLee said:**
> I would partially agree with you about Debian testing. It's true when testing is close to release, and especially when frozen close to release. Just after release though, when the old Sid has migrated into the new codename as the new testing, it can be fairly volatile. I have seen big surprises happen, for users who have used "testing" rather than the codename in their sources list, and the accompanying posts for help in the Debian forums .

Um, yeah, that can the the issue with testing, it can be more buggy at times than at others. I'm wondering how bad its going to be for sid users when the squeeze freeze is over, I havent lived though a freeze and then restart since I've been using aptosid.

---

