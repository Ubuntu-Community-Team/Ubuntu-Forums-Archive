---
title: "swap?"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by muxenle on 2009-07-10
I'm going to be refomating my entire drive and set up a dual boot with xp and ubunutu studio(the newest version 9.04 I think). \

I'm wondering how big I should make my swap partion, and how big I should make it.


HD is 200 gigs
I have 2 gigs of ram( in case it matters)
and also in case it matters it will be on a Acer Aspiren5720Z( its a notebook)

Also any opinions on if I should do XP or ubuntu first?

---

### Post by jlhaslip on 2009-07-10
The swap file is typically 1 and a half times your RAM, so 3 gigs in your case.


And I'm pretty sure you will need to install the Windows system first, because it doesn't play nice with others.

---

### Post by earthpigg on 2009-07-10
install XP, then ubuntu.

if it needs it, defrag XP before you install ubuntu.... defragging xp AFTER ubuntu wont be as effective as it would have been before ubuntu was there.

2 gigs of swap space should be fine. you have enough ram that it should not be a huge issue.

edit: 3 gigs works, too, as the user above me posted.

if you plan to use virtual machines, make it bigger. if you have no idea wtf a VM is, then dont worry about it :D

---

### Post by muxenle on 2009-07-10
thanks :)

and in my OP I meant to say what does the swap partition do, and how big should I make it

making posts and don't double checking them isn't a good ideawhen you're hot, thirsty, and fighting of a cold.

and I've grown up with computers, and spend way to much time on the interwebs, of course I know what a VM is :P though I don't really have a plan on using one, though I have messed around with(usually just getting frustated with them making me want to throw my laptop out of a window)

---

### Post by kandieyman on 2009-07-10
You need to make sure that you have a larger swap than your RAM, otherwise you will not be able to hibernate. Swap does not really serve any other purpose, anymore, for two reasons.

1) RAM sizes and speeds are so great now, that computers don't need to swap.
2) If swapping is needed, Ubuntu has the ability to create a file on the hard drive that acts like a swap partition (this does not apply to hibernation, that must be a separate partition)

---

### Post by raymondh on 2009-07-10
> **muxenle said:**
> I'm going to be refomating my entire drive and set up a dual boot with xp and ubunutu studio(the newest version 9.04 I think). \

I'm wondering how big I should make my swap partion, and how big I should make it.


HD is 200 gigs
I have 2 gigs of ram( in case it matters)
and also in case it matters it will be on a Acer Aspiren5720Z( its a notebook)

Also any opinions on if I should do XP or ubuntu first?


hello Muxenle,

You can install either first.  Even if you install XP (last which will overwrite the MBR) you can easily recover grub.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

As for SWAP, 1.5GB is OK... unless you plan to use heavy, resource instensive apps and suspend/hibernate a lot whilst using those apps.  The rule of 1-2X RAM is still valid in low RAM situations and, using intensive applications. 

As for your Acer Aspire ... check the compatibility list.

[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops?action=show&redirect=HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops?action=show&redirect=HardwareSupportMachinesLaptops)

Back up your files.  Good luck.

---

### Post by LewRockwell on 2009-07-10
Easy swap computation:

to be safe, ALWAYS 1xMAXram...easy to remember "maxram"

Note: the reason you should make this a habit and rule of thumb is because most computers do NOT ship with maximum ram installed...so just because you have 1GB now...doesn't mean that you won't add more later...then, if you didn't create a swap at "maxram" then you'll have 3GB of ram and only 1GB of swap

sure, you can find a spot to add another swap partition in the future IF YOU'RE STILL THE ONE USING THAT COMPUTER...

but if you are helping out friends/customers/acquaintances/relatives then you SHOULD DO IT RIGHT THE FIRST TIME!

hopefully this will make sense to some...for others, there is no hope...

.

---

### Post by LewRockwell on 2009-07-10
and...while I'm here...

Partitioning:

It's best to plan ahead while your hacking out the partitions on your drive(s)

Hard drives may have from one to four primary partitions and no more than one extended partition(which can be divided into many logical partitions)

For more reference:
[http://www.downloadsquad.com/2007/09/13/how-to-install-145-operating-systems-on-one-pc/](http://www.downloadsquad.com/2007/09/13/how-to-install-145-operating-systems-on-one-pc/)
[http://www.justlinux.com/forum/showthread.php?threadid=147959](http://www.justlinux.com/forum/showthread.php?threadid=147959)

So...

for a 200GB hard drive I partition them as follows:

One 20-30GB primary partition which will be for windows
One primary swap partition equal to the maximum amount of ram your machine can handle
One 20-30GB primary partition which will be for Ubuntu
One extended partition which can be internally managed either now or at a later time(don't worry, it'll be there for you when you're ready for it)

Here we see that we've built expansion and livability into the drive partitioning from the very beginning...a little pre-planning goes a long way!

.

---

### Post by muxenle on 2009-07-10
> **LewRockwell said:**
> and...while I'm here...

Partitioning:

It's best to plan ahead while your hacking out the partitions on your drive(s)

Hard drives may have from one to four primary partitions and no more than one extended partition(which can be divided into many logical partitions)

For more reference:
[http://www.downloadsquad.com/2007/09/13/how-to-install-145-operating-systems-on-one-pc/](http://www.downloadsquad.com/2007/09/13/how-to-install-145-operating-systems-on-one-pc/)
[http://www.justlinux.com/forum/showthread.php?threadid=147959](http://www.justlinux.com/forum/showthread.php?threadid=147959)

So...

for a 200GB hard drive I partition them as follows:

One 20-30GB primary partition which will be for windows
One primary swap partition equal to the maximum amount of ram your machine can handle
One 20-30GB primary partition which will be for Ubuntu
One extended partition which can be internally managed either now or at a later time(don't worry, it'll be there for you when you're ready for it)

Here we see that we've built expansion and livability into the drive partitioning from the very beginning...a little pre-planning goes a long way!

.

hhmmm... that plan interests me, though I'll admit I'm slightly confused on the extended partition(as to what exaclty it is, and how to use it) I'd be using XP for games(mostly likely just morrowind, microsoft flight sim X, and guild wars) and I'd be using ubuntu for everything else(basicly college, and personal witting and minor art needs)

well basically all that is asking for more info what/how exactly to use a extended partion(which I would be roughly 137 GB)...


and I must say I forgot how helpfully refreshing these forums are... most of my other forum life has been spent on the world of warcraft forums(largely on the off-topic.... *shudder*)

---

### Post by raymondh on 2009-07-10
> **muxenle said:**
> hhmmm... that plan interests me, though I'll admit I'm slightly confused on the extended partition(as to what exaclty it is, and how to use it) I'd be using XP for games(mostly likely just morrowind, microsoft flight sim X, and guild wars) and I'd be using ubuntu for everything else(basicly college, and personal witting and minor art needs)

well basically all that is asking for more info what/how exactly to use a extended partion(which I would be roughly 137 GB)...


and I must say I forgot how helpfully refreshing these forums are... most of my other forum life has been spent on the world of warcraft forums(largely on the off-topic.... *shudder*)

On EXTENDED partitions and its' uses:

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[http://www.faqs.org/docs/linux_admin/x1139.html](http://www.faqs.org/docs/linux_admin/x1139.html)
[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

You start with a  4-max limit per HD (4 Primary or 3 Primary + 1 Extended).  The EXTENDED partition allows logical partitions within/inside it where the only limiting factor is the OS (16 logicals for Linux, I think).  Those logical partitions thus allow you to overcome the 4-max limit.

It has many uses, depending on your creativity and requirements.  On a Ubuntu install, you can have a partition for SWAP, for ROOT (/), for /home (where your files & settings are stored), for /USR, for /Data, etc.  
Outside Ubuntu, you can use those logicals to store files/data/media that could be read by both OS', for example.  Or, you can also use that to install another OS, if you wish.

---

### Post by LewRockwell on 2009-07-10
> **raymondhenson said:**
> 
...

You start with a  4-max limit per HD (4 Primary or 3 Primary + 1 Extended).  The EXTENDED partition allows logical partitions within/inside it where the only limiting factor is the OS (16 logicals for Linux, I think).
...

[http://www.justlinux.com/forum/showpost.php?p=861282&postcount=1](http://www.justlinux.com/forum/showpost.php?p=861282&postcount=1)

fun stuff!

.

---

### Post by raymondh on 2009-07-11
> **LewRockwell said:**
> [http://www.justlinux.com/forum/showpost.php?p=861282&postcount=1](http://www.justlinux.com/forum/showpost.php?p=861282&postcount=1)

fun stuff!

.

Wow.

---

