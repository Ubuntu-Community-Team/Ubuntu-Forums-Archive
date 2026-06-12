---
title: "How To Get Back Windows"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by baiserabies on 2009-04-05
Hi, I just need some help on how to get back windows on my laptop (HP Pavillion dv6000) preferably vista.
What's the easiest way to do so?

Thanks for your help!

---

### Post by Elfy on 2009-04-05
Well, what have you done to lose it?

HAve you just installed ubuntu and there is no option to boot windows?

A bit more information will help I think.

---

### Post by Quintilian on 2009-04-05
I know a lot of HPs have a recovery partition. If you didn't overwrite it when you installed ubuntu then you could boot into that and recover windows that way. Otherwise you'd pretty much just have to burn an ISO of vista or xp and install it that way.

---

### Post by baiserabies on 2009-04-05
I don't have any duel boot,
just ubuntu.
And Im pretty sure that the recovery partition is gone too.
:|

---

### Post by |Mitch| on 2009-04-05
I'm assuming you don't have the Windows installation disk from HP?

You should be able to call HP customer support and give them the serial number of your computer and for the cost of shipping will send you a set of Windows boot disks. They will send you whatever version was installed on your comp. to begin with and it will have all the preloaded software that HP puts on their systems to begin with.

Just explain to them that the system restore feature has been corrupted and that you need to do a clean format/reinstall.

---

### Post by Elfy on 2009-04-05
IF you have no recovery partition, then you need ot boot with an install cd and install it.

But run this

```
sudo fdisk -l
```

Let us have a look at the result - check your partitions.

When you installed did you tell it to overwrite the disk?

---

### Post by baiserabies on 2009-04-05
i get 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85eb85eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18705   150247881   83  Linux
/dev/sda2           18706       19457     6040440    5  Extended
/dev/sda5           18706       19457     6040408+  82  Linux swap / Solaris

when i ran
sudo fdisk -l

---

### Post by Elfy on 2009-04-05
Well if you don't have the discs, then do as Mitch said.

---

### Post by baiserabies on 2009-04-05
so if i pop in a bootable version of vista i should  be able to install it?

---

### Post by lisati on 2009-04-05
> **baiserabies said:**
> so if i pop in a bootable version of vista i should  be able to install it?

If it's an installation disk or a recovery disk, then the answer is "yes"

You might want to chalk this one up to experience: it's always a good idea to make sure you have the means to recover important data, including recovery partitions.

I remember being a little nervous the first time I installed Ubuntu on a machine which had a recovery partition, and being greatly relieved when the choices I'd made didn't wipe out the recovery partition.

EDIT: Just remembered: my newer laptop (from Toshiba) came with a recovery partition and a tool to make a CD or DVD version of it. Once you've got things up and running how you like it you might want to check if your machine has a similar option for making recovery disks.

---

### Post by therockindonkey on 2009-04-05
> **forestpixie said:**
> Well if you don't have the discs, then do as Mitch said.

Yes, this is the most reasonable solution.  The disks probably won't even cost that much.  I recently had to call Toshiba to get replacement disks as I had misplaced the originals.  They only charged me $20 and the disks arrived about a week later.

Here's some HP Contact information that might be helpful (i had to do some poking around on their website to find it).
[I]
HP and Compaq products for Home & Home Office use 800-HP invent or 800-474-6836 24 hours a day, 7 days a week for most products U.S.: English and Spanish for most products. 

HP and Compaq products for business use 800-334-5144 24 hours a day, 7 days a week for most products U.S.: English 

HP TouchSmart PC products HP HDX Notebook PC products 866-408-5408 24 hours a day, 7 days a week U.S.: 

English and Spanish Customers using TTY 877-656-7058 6:00 a.m. - 3:00 p.m. PT
Mon. &#8211; Fri. excluding holidays[/I]

---

### Post by baiserabies on 2009-04-05
is a recovery disc the same as bootable copy of vista?

---

### Post by |Mitch| on 2009-04-05
A recovery disk will get your computer the way it came from HP. Reinstall XP or Vista(whichever was original) + all the added HP trialware, etc...

If your computer came with XP, the only option to get Vista would be to buy a copy of the upgrade disk.

---

### Post by -kg- on 2009-04-05
> **|Mitch| said:**
> A recovery disk will get your computer the way it came from HP. Reinstall XP or Vista(whichever was original) + all the added HP trialware, etc...

If your computer came with XP, the only option to get Vista would be to buy a copy of the upgrade disk.

Or a full-install disk, in which case you could do a clean install without all the HP crap, etc...

Of course, if you want Vista, you'd better check and make sure the computer has sufficient resources to run it.  Vista is quite the resource hog (that is, unless you go for Vista Basic, and even then...).

<edit> I just looked up your [computer's specs]("http://www.pcmech.com/article/hp-pavilion-dv6000-notebook-review/") and according to them, Vista Premium comes with the computer.  You should be good to go with a Recovery Disk, which will put VHP back on your computer.

---

### Post by rhcm123 on 2009-04-05
> **baiserabies said:**
> Hi, I just need some help on how to get back windows on my laptop (HP Pavillion dv6000) preferably vista.
What's the easiest way to do so?

Thanks for your help!
just outta curiosity, why are you trying to put vista back on?

---

### Post by anewguy on 2009-04-05
One other thing to consider if you are going to get rid of Ubuntu and put Windows back:

Be sure to use a LiveCD and run parted or gparted and remove the Ubuntu partitions so the whole disk is unallocated.

Dave ;)

---

### Post by baiserabies on 2009-04-05
the main reason that im going back to windows is mainly cause of the ease of syncing with my iphone.
im prolle going to put windows back on then have a dual boot for ubuntu.

---

### Post by rhcm123 on 2009-04-05
> **baiserabies said:**
> the main reason that im going back to windows is mainly cause of the ease of syncing with my iphone.
im prolle going to put windows back on then have a dual boot for ubuntu.

No offense, but buy a real smart phone (e.g blackberry), or somthing with cross-compatibility.

---

### Post by baiserabies on 2009-04-06
> **rhcm123 said:**
> No offense, but buy a real smart phone (e.g blackberry), or somthing with cross-compatibility.

none taken,
its just that i dont really NEED a 'real'  smart phone,
i just have a iphone cause of the games/music/and i like the virtual keyboard.
im a teen, i dont need a business phone

---

### Post by juancarlospaco on 2009-04-06
Isntall " *Floola* " this programs Sync Iphone perfectly.

---

### Post by Mark Phelps on 2009-04-06
> **baiserabies said:**
> so if i pop in a bootable version of vista i should  be able to install it?

Well ... probably ...

Realize that booting from a generic Vista DVD will not install any of the software that came preloaded from HP (probably not a great loss!) and may struggle with the drivers at first.

Give Windows Update a few reboots and/or a couple of days to discover and load driver updates for Vista.

You would be better prepared if you went to the HP Website, searched for your PC model, and downloaded any driver and application SW they provide.  That way, you can apply any drivers and add any software you want.

Also, since this is an OEM installation, it most probably will activate Vista without asking any questions, but just in case, locate your produce key (probably on a sticker on the case) and have it handy.

And, be sure to install the SAME VERSION as was on there originally -- the activation is specific to the version.  In other words, if you had Home Premium, don't install Ultimate because it most probably won't activate.

---

### Post by baiserabies on 2009-04-06
will it sync my contacts/app/movies/music all?

---

### Post by stchman on 2009-04-06
> **baiserabies said:**
> I don't have any duel boot,
just ubuntu.
And Im pretty sure that the recovery partition is gone too.
:|

Did you make backup discs of the recovery partition?  If no you have 2 options:

1.  Call HP and purchase the recovery DVD, I think they are around $20.

2.  Buy Vista OEM DVD off ebay new.  Approx $125.

Option 2 is a better option as a clean install will give you no cr@p ware.

Why are you getting rid of Ubuntu.

---

### Post by mlentink on 2009-04-06
> **baiserabies said:**
> will it sync my contacts/app/movies/music all?

No.

Go to start, pay, do not get, a large sum of money.

...

Then again, stick around. read, ask questions, and you might learn how you can do what you want, without having to pay Microsoft.

welcome to the free world

---

### Post by rhcm123 on 2009-04-06
> **baiserabies said:**
> none taken,
its just that i dont really NEED a 'real'  smart phone,
i just have a iphone cause of the games/music/and i like the virtual keyboard.
im a teen, i dont need a business phone

i'm almost 16 and i'm on my second smartphone. and i get paid to build servers for a company down the road - i can ride my bike to work in the summer.

EDIT: I forgot to mention how awesome that is :)

---

### Post by baiserabies on 2009-04-07
ok,
so i got a copy of vista and when i tried to boot  from it,
it just automatically boots to ubuntu.. any suggestions

---

### Post by rhcm123 on 2009-04-07
> **baiserabies said:**
> ok,
so i got a copy of vista and when i tried to boot  from it,
it just automatically boots to ubuntu.. any suggestions

you have to modify your bios. hit f8, f12, f2, f10 on startup (it could be a bunch, see your manual or the boot splash screen), and change the boot load order so that CDROM is above HDD

---

### Post by baiserabies on 2009-04-07
i tried that, then i manually tried to option to boot from the dvd drive and it still just booted to ubuntu...

---

### Post by blackgr on 2009-04-07
> **baiserabies said:**
> i tried that, then i manually tried to option to boot from the dvd drive and it still just booted to ubuntu...

This is called.... FATE. Stick with ubuntu!

---

### Post by jerome1232 on 2009-04-07
> **blackgr said:**
> This is called.... FATE. Stick with ubuntu!

That was helpful....

If the computer will boot an Ubuntu live cd but not the vista dvd you have, my vote goes to a bad dvd disc.

---

### Post by |Mitch| on 2009-04-07
[This is assuming you have the DVD Drive set first in the boot order]

Does your computer even recognize the DVD drive and bypass it? Or does it not even recognize?

You did save the settings when you exited out of the Bios? There is two different options: save & exit or cancel & exit. 

You do have a DVD and not trying to run the Vista DVD with just a cd drive?

---

### Post by baiserabies on 2009-04-07
the disc if fine,
i tried it on another computer

---

### Post by helpimtrappedinaserverfar on 2009-04-07
PEOPLE! This thread showcases a major problem with the linux community, namely that a large portion of it hates microsoft. We are not competing with microsoft. While I would love to see microsoft die, this man wants windows, so stop trying to convince him that ubuntu is perfect, ubuntu is for everyone etc. Ubuntu means "Humanity to others," try to stick with that philosophy.

---

### Post by blackgr on 2009-04-08
Usually DVD drives are the reason for not booting some disks. I had same issue. TRy to find an external DVD drive or something like that to boot vista CD.

---

### Post by baiserabies on 2009-04-09
i was looking for a way to boot vista/7 from a usb drive all the ways that showed you to do it was if your are running windows already,
does anyone know a way to create a bootable usb drive of windows from linux????

---

