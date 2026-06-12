---
title: "Will Wireless Issues on the main O/S ever be fixed?"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by 786souljah on 2008-02-13
I have a question possibly for developers and just opinion in general. 

There is a LOT of issues with the wireless and internet support being hard to get working. Will this issue be addressed in the future and how long a time will it be? I need my computer up and running and without internet its rendered useless. When will wireless issues be addressed in the main O/S rather than third party installing and creating own drivers etc etc.

---

### Post by Whiffle on 2008-02-13
January 43rd, 2042


Depends on the hardware.  Wireless support on my laptop is essentially flawless, I've got an ipw2200 card.  Works great.  If you own a broadcom card, it might be never before it gets to be reliable.  The wireless "systems" on linux are fine, its the drivers that are hard to come by.

---

### Post by mrsteveman1 on 2008-02-13
Actually the part of the kernel that deals with wireless network chipsets has been a complete mess for a long time, in part because a lot of wireless chips require a significant amount of the network stack to be in software (IE softmac). This required either reimplementing the same functions over and over in each driver, or modifying the drivers to use the intel MAC layer that was donated to the kernel a few years ago.

For a while now the majority of new development has taken place in the mac80211 versions of the drivers, which were not merged until very recently, so users have not yet been able to take advantage of them. As of the 2.6.24 kernel a significant number of wireless drivers now use the new mac80211 subsystem, which will make wireless networking and development much much easier. 

So yes the drivers and the network stack in general are much better right now than they were even 6 months ago. The one thing that will remain the same is this: wireless drivers for linux are always going to come from one of a few places: They can be donated by the manufacturer under a GPL license, which then gets improved and put into the kernel, or they get reverse engineered like the broadcom driver was, or they can be released as binary only by the manufacturer or another party (like linuxant, creative). Ideally you want the manufacturer to support their own hardware, but that doesn't always happen.

The mac80211 broadcom driver is actually ok at this point, but because of the way the kernel is developed, users aren't going to notice any difference for a while (until the next version of ubuntu) unless they manually install the newest kernels, or unless the ubuntu devs backport the newer drivers, which is unlikely.

---

### Post by 786souljah on 2008-02-13
Ah that makes things a tiny bit clearer. But here's my issue.

I am looking to install linux on a laptop now, however the only thing holding me back from purchasing a laptop is internet capability. It most likely will have built in wireless but then how is that goign to work? I dont want to have to buy an aftermarket card to plug in. And im not much of a linux brainer either so i dont know the whole compiling and things that ive read on the forums.

---

### Post by mrsteveman1 on 2008-02-13
You can probably just check which chipset is in the machine when you are looking for your laptop (check in windows, shouldn't be hard). Then you can check online to see if that chipset works well in linux.

---

### Post by 786souljah on 2008-02-13
Are there any known chipsets that will for sure work with ease? That you would recommend to look for?

---

### Post by mrsteveman1 on 2008-02-13
hmmm.

Intel chipsets are always a safe choice because Intel directly supports the drivers. So anything branded Centrino will use intels wifi chips, and lots of others do too.

Atheros would probably also be ok, they seem to at least partially support Linux, and the broadcom driver (as odd as this may seem) has been developed constantly for a while now and is fairly stable as well. By the time you get a laptop the next version of ubuntu will likely be out, which will use all the new drivers from the new kernel.

---

