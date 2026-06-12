---
title: "I want advice re the best way to install Karmic as a dual boot with Jaunty"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by MisFitt on 2010-03-28
I've attached the screenshot of my hard drive,/dev/sda1 being where I'd like to install Karmic 64 bit.
/dev/sda5 being my Jaunty 64 bit install and /dev/sda2 being media and files/storage
It's taken 2 days sorting files after 2 hard drives were causing major problems-this one appears so far to be doing ok,anyway,I have installed Jaunty and now want to add Karmic which I'm redownloading as it kept saying "kernel" crashes,had all sorts of drama and I had a look at the hard drive with Lucid beta and it showed no obvious problems,unlike the last time I checked.
I'm asking advice because I don't want to screw up a good thing(fingers crossed)
also I see sda1 is the boot.
I had wanted Jaunty on the boot partition,don't understand why Jaunty was installed on sda5.
When I tried to install Karmic next to it it said I had too many...the name escapes me now,primary's?
EDIT:I've just put in the new karmic disk and a "crash report,Serious Kernel Problem
your system encounted a serious kernal problem" shows up so while I'm still interested in the answers this hard drive's cactus it seems.
I ought to be grateful Jaunty's running at all and I am,very.
EDITED EDIT:just a thought,looking for opinion/advice,I do have a shiny bright 320Gib fully healthy external,sata hard drive that's holding my precious,irreplacable files like photos and video and I've had the thought of taking it out of the case after sending over the data to a partition on the pictured drive(attach'd) and using it as my C: operating drive which is what I plan to do when my 2 neweys arrive anyway.Now,how safe would that data be on a sick(early stages) drive used just for storage after formatting?

---

### Post by edgy360 on 2010-03-28
Why not just run one in VirtualBox if you have a fast PC.

---

### Post by oldfred on 2010-03-28
Windows requires a boot flag. Ubuntu does not use the boot flag, but I recently found out that some BIOS (windows centric) will not let you boot unless one partition has a boot flag.

Since you have moved your data from root you are using only 6GB of your Ubuntu install. You can shrink your Ubuntu install to 20GB and leave room from 2 or 3 additional installs. (I have 3 Ubuntu installs, previous, current & beta) and I rotate current & previous so I can go back and find a setting if I miss it in my set up of my new install. Beta is just to learn about the new version before I convert to it. I link all my data into each install. The first time I tried to do as much as I could from command line, then listed history and copied it to a file for conversion to a bash script to semi-automate reinstalls.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

---

### Post by egalvan on 2010-03-28
> **MisFitt said:**
> ,looking for **opinion/advice**
,I have a 320Gib fully healthy external,sata hard drive that's holding my [COLOR="Red"]precious,irreplacable files[/COLOR] like photos and video

.[COLOR="Red"]how safe would that data be on a sick(early stages) drive [/COLOR]used just for storage after formatting?

In **MY** opinion/advice,

[COLOR="Red"]precious, irreplaceable data[/COLOR]

doesn't even belong in the same *time zone* as

[COLOR="Red"]sick drive[/COLOR]

---

### Post by MisFitt on 2010-03-28
Thanks OldFred,a lot to go thru' and that's always a good thing!

---

### Post by MisFitt on 2010-03-28
Absolutely right and very well put by the way.
I've decided tomorrow I'm going to throw Au$75 at a 500GiB WD or Seagate sata2 from the shop down the street.

---

### Post by egalvan on 2010-03-28
> **MisFitt said:**
> I've decided tomorrow I'm going to throw Au$75 at a 500GiB WD or Seagate sata2 from the shop down the street.

A further bit of advice...

on new hardware, there is the small percentage that die an early death.

So install the new drive, then set it to format.
This should take a few hours...
do it again.

leave it connected for a few days, and reformat.

This should reduce the probability of ¨infant death`.


Personnaly, any drive I use for irreplaceable data is allowed to cook for at least a month before that data is entrusted to it.
Call me paranoid, but even I have drives fail. ;)

---

### Post by MisFitt on 2010-03-28
Advice taken onboard.
I have another question for you about partitions.
Can making,deleting,resizing or moving them around have an impact on hard drive health?
I'd never done any of this before Ubuntu
edit:Thanks,again,and I've just purchased a 500g sata2 so hopefully a fresh start'll be just that.
A WD Caviar "Green"-(gee whizz,I'm compromised again)

---

### Post by egalvan on 2010-03-31
> **MisFitt said:**
> A quetion about partitions...
Can **making,deleting,resizing or moving them around** have an impact on hard drive health?

Absolutley YES. A modern hard drive has an estimated life-span of about five years...
** making,deleting,resizing or moving them around ** will use up almost two days of that five years...

Just pulling your leg..;)
not..:D

It's all the same, whatever one is reading or writing to the drive...
it's all Seek and Input/Output.. :)

> edit:Thanks,again,and I've just purchased a 500g sata2 so hopefully a fresh start'll be just that.
A WD Caviar "Green"-(gee whizz,I'm compromised again)

"Green" basically means it uses less energy to operate...
which all drives have been doing... green or not...

Much of the "Green" movement is Advertising Fluff designed to extract the maximum "Green" from un-curious consumers.

Me Myself & I are curious to a fault, and we read all claims carefully. Our money was hard-won.

Stay Frosty.

---

### Post by MisFitt on 2010-04-04
"Stay frosty",I like that.
It happens also to be the exact same model of the burnout,built in obsolesence..........like myself
Karmic's happy and all is well

---

