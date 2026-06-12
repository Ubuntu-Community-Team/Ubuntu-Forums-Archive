---
title: "Why install Ubuntu on my HDD?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Andy06 on 2009-01-19
I've had quite a few ubuntu installations in the past few weeks on more than 20 computers and am beginning to wonder why should I bother installing on HDDs when the LiveUSBs work so well now. I know there are advantages to HDD installs but want to know from more knowledgeable members as to what they specifically are.


So far I have this in favour of LiveUSBs:

1) Mobility = most new and similarly configured comps can use them

2) Starting from scratch isn't that hard

3) Saves heaps of disk space and all the associated trouble with partitioning and MBR issues

4) Much Much faster if you have enough RAM and a fast flash drive, this should get even better with USB3.0

5) With persistence, it behaves like a normal install and you can copy the casper file over to a new LiveUSB and it'll take you programs and settings with it. (A bit like having a separate home partition)

6) No issues with root elevation 

7) Ability to demonstrate pre configured desktop effects to lots of people

Thanks for the help

---

### Post by stefangr1 on 2009-01-19
But if someone at your house 'borrows' the usb stick to go to a presentation, you'll be without operating system :).

USB sticks aren't really meant to serve as a harddisk, because they can be overwritten only a limited number of times. It takes (apparently) quite some effort to build a good ssd disk, because smart electronics need to correct issues with flash. The operating system performs a lot of small read/write operations. When it (to give an example) contiuously changes the same 1 to a 0 and vv., that will eventually corrupt your usb stick. The more expensive flash memory often comes with claims like "can be overwritten 1.000.000 times", but what if the os overwrites the same bit every 2 seconds?

---

### Post by arjuntank on 2009-01-19
> **Andy06 said:**
> I've had quite a few ubuntu installations in the past few weeks on more than 20 computers and am beginning to wonder why should I bother installing on HDDs when the LiveUSBs work so well now. I know there are advantages to HDD installs but want to know from more knowledgeable members as to what they specifically are.


So far I have this in favour of LiveUSBs:

1) Mobility = most new and similarly configured comps can use them

2) Starting from scratch isn't that hard

3) Saves heaps of disk space and all the associated trouble with partitioning and MBR issues

4) Much Much faster if you have enough RAM and a fast flash drive, this should get even better with USB3.0

5) With persistence, it behaves like a normal install and you can copy the casper file over to a new LiveUSB and it'll take you programs and settings with it. (A bit like having a separate home partition)

6) No issues with root elevation 

7) Ability to demonstrate pre configured desktop effects to lots of people

Thanks for the help

You can go both ways!
Install ubuntu in hdd and use usb-stick too
you can lock(grub password) the hdd ubuntu and open up in case u have problems with usb
also, you can backup ur data on ur hdd viz. certain packages, so that u can run thru the live version too 
well this was just a suggestion,living with live usb version is of course easier
as previous reply, ur usb-drive can be stolen or u gave it to somebody.
but hey you can sync data from ur usb-drive to hdd too :)

whatever, this depends on how u use the system,
if its a heavy workstation u obviously need to install in the system for heavy hdd consuming apps.

---

### Post by RyanVanDiemen on 2009-01-19
It`s hard to argue with you Andy06, all your points are true to be perfectly honest. But why should I use memory-stick as my primary system drive if I can use built-in HDD (it`s still faster than any memory key, isn`t it). It`s perfect option if you want to show your friends how linux looks or if you want to use linux on the computer where you are not allowed to re-install system (internet cafe, work computer etc.), but all this is just as a secondary system and that`s what we use it for. But again as a primary system, I don`t see a reason why... If you want to have all your documents with you on any computer, you can still have them on your key with or without the system on it... SSD drives have come a long way for last few months so I wouldn`t be too worried about the re-writing constraints...

---

### Post by stefangr1 on 2009-01-19
No, with state of the art ssd drives I wouldn't worry (though tests show that they still have a long way to go with respect to getting the failure rates down!), but that's because the electronics regulate what is written where. An usb stick lacks these electronics, and is therefore much more vulnerable.

---

### Post by billgoldberg on 2009-01-19
> **Andy06 said:**
> I've had quite a few ubuntu installations in the past few weeks on more than 20 computers and am beginning to wonder why should I bother installing on HDDs when the LiveUSBs work so well now. I know there are advantages to HDD installs but want to know from more knowledgeable members as to what they specifically are.


So far I have this in favour of LiveUSBs:

1) Mobility = most new and similarly configured comps can use them

2) Starting from scratch isn't that hard

3) Saves heaps of disk space and all the associated trouble with partitioning and MBR issues

4) Much Much faster if you have enough RAM and a fast flash drive, this should get even better with USB3.0

5) With persistence, it behaves like a normal install and you can copy the casper file over to a new LiveUSB and it'll take you programs and settings with it. (A bit like having a separate home partition)

6) No issues with root elevation 

7) Ability to demonstrate pre configured desktop effects to lots of people

Thanks for the help

A persistent live usb is good to use in times of trouble or when at a friends house, but not really suited for daily use.

As mentioned before, flash drive have a limited number or write cycles.

Also, the live usb way will be slower, even though you claim it isn't.

---

### Post by Andy06 on 2009-01-19
Thanks for the responses, your counter points are what I needed.

Me and my frs have been discussing this for a long time and are indeed using both LiveUSBs and full HDD installations currently but are finding the LiveUSBs so much easier to work with (not root issues etc).

> But if someone at your house 'borrows' the usb stick to go to a presentation, you'll be without operating system .

USB sticks aren't really meant to serve as a harddisk, because they can be overwritten only a limited number of times. It takes (apparently) quite some effort to build a good ssd disk, because smart electronics need to correct issues with flash. The operating system performs a lot of small read/write operations. When it (to give an example) contiuously changes the same 1 to a 0 and vv., that will eventually corrupt your usb stick. The more expensive flash memory often comes with claims like "can be overwritten 1.000.000 times", but what if the os overwrites the same bit every 2 seconds?

The consistent reading/writing operations on a HD are associated with a full blown install, a live USB system with persistence uses the RAM as the swap space for OS operations and the user data will be written to you data partition (on the actual hard disk), do not use the LiveUSB for /home or for Docs, Pics, Music, Videos. 

Losing or lending it is not really that much of an issue coz like I said, all the data is on the actual HD, only the OS is on the USB. Even my Firefox profile is on the HD data partition (so I use the exact same profile files for both windows and ubuntu and do not have to bother with syncing). Also you can create lots of LiveUSBs, and simply copy the casper file into each one and they will be configured the same way (programs, settings, wallpaper, themes, fonts, even compiz configuration). Instead of making backups of the whole OS, now you only need a backup of this casper file.

> You can go both ways!
Install ubuntu in hdd and use usb-stick too
you can lock(grub password) the hdd ubuntu and open up in case u have problems with usb
also, you can backup ur data on ur hdd viz. certain packages, so that u can run thru the live version too
well this was just a suggestion,living with live usb version is of course easier
as previous reply, ur usb-drive can be stolen or u gave it to somebody.
but hey you can sync data from ur usb-drive to hdd too

whatever, this depends on how u use the system,
if its a heavy workstation u obviously need to install in the system for heavy hdd consuming apps. 

The thing is, we're in a dorm, I first used linux back in july 08, loved it and hit upon the idea of configuring compiz to the max and doing a presentation. Once that was done, a 100 people wanted ubuntu on their system. Now instead of going to everybody and doing installs on their HDDs, we're thinking of just having them make LiveUSBs which is infinitely easier. The best thing though is that once they screw their OS up, they can start again in 2 mins rather than a full install all over. It really eases the pressure on the people who are troubleshooting their problems.

> But why should I use memory-stick as my primary system drive if I can use built-in HDD (it`s still faster than any memory key, isn`t 
it).

This is the critical issue IMO. I always thought that in terms of speed, it went something like this Full HD install > External HD install > Flash USB install > Live CD

In my very recent (and perhaps incomplete/inaccurate) understanding, apparently this is not the case, the major thing here is when we talk about external drives, there are 2 types, the flash drives(or pen drives or USB drives) and the external hard disks (2.5" or 3.5"). The flash drives are much faster than the external hard disks so while an external hard disk might be slower than an internal hard disk, the same isnt exactly true for flash drives. But it gets even muddier. Two factors affect whether or not a flash install is fast or not:

1) The quality (speed-wise) of your flash drive. Not all are born equal and most read faster than HDDs but do sometimes write slower.

2) The amount of RAM in you system. This is what really makes LiveUSBs fast, if you have 3 or 4 GB of RAM, everything is pre loaded and then comes up as if you are opening up notepad. Live systems use the RAM for everything and avoid read/write operations from the loading media. (LiveCDs cant be written onto anyway). 

So if you have 1 GB of RAM, you might find your LiveUSB slower or equivalent to the full HDD install but if you have 3 or 4GB, the tables turn in favour of the LiveUSB system. 

This isn't what I thought would be the case until about a month ago when we started experiencing the speed advantages of LiveUSBs first hand. I'm sure more experienced members will confirm/correct me on this.

> No, with state of the art ssd drives I wouldn't worry (though tests show that they still have a long way to go with respect to getting the failure rates down!), but that's because the electronics regulate what is written where. An usb stick lacks these electronics, and is therefore much more vulnerable.

Yes. So if using LiveUSBs, standard procedures will be modified slightly. The casper file is to be backed up religiously but otherwise the rest of the installation is almost of throwaway value since it will take 2 mins to create it again.

> 
Also, the live usb way will be slower, even though you claim it isn't. 

My impressions are from first hand experience and could very well be wrong. But even the other Linux users in the dorm feel the same way but we have done no rigorous testing to verify it. I might add though that the speed difference is noticeable and that Live USB systems in conjunction with lots of RAM feel a LOT faster. Please see above for why I think this might be the case and do let me know if I have got this wrong.

Also, external HD installs are slower than internal HD ones right? Why is this? Is the USB interface the bottleneck? Will this change with USB3.0?
From an initial look at max USB2.0 transfer rates, it would seem that the actual external HD should be the weakest link and therefore the performance of external and internal HDDs should be the same.

Quite confused hehe.

Thanks a lot for your responses. Keep them coming

---

### Post by mikewhatever on 2009-01-19
> **Andy06 said:**
> 

6) No issues with root elevation 


If that means running as root all the time, then it is the reason not to use liveUSB.

---

### Post by MrKlean on 2009-01-19
If you have a system set up the way you like....try remastersys.  You can make a live cd of your setup, and not have to install on the HD.. although I use it to back up my setup.  If i crash or screwup....I can reinstall my system exactly like it was ; )

---

### Post by lykwydchykyn on 2009-01-19
Updating or adding software might be an issue.

---

### Post by Andy06 on 2009-01-20
> If you have a system set up the way you like....try remastersys. You can make a live cd of your setup, and not have to install on the HD.. although I use it to back up my setup. If i crash or screwup....I can reinstall my system exactly like it was ; )

Thanks, how do I go about this? This would be perhaps the most important advice I have ever received, I can now distribute LiveUSBs with Compiz Fusion pre configured and all codecs loaded for total out of the box usability.

---

### Post by tea for one on 2009-01-20
I used this information for Remastersys

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

It was easy to follow and worked perfectly for me

---

