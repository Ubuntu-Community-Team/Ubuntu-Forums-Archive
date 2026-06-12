---
title: "Will Xubuntu work on my PC?"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by RabbitWho on 2009-08-16
I'm looking for general advice here. And I know nothing so don't be afraid to be patronizing. 

I have a 10 year old IBM Aptiva Intel Pentium 3 - 499 MHz, 192MB RAM, 12 GB hard drive (7GB free)  currently running on XP 

I've already gone through all the usual things to speed up Windows, and while it's working alright now it takes a long time to boot up and Photoshop runs very slowly on it. 

Other than that it's fine, it runs the Internet and can even play music at the same time. 

Would it be possible to dual-boot it with Xubuntu? (I know it's not exactly optimal RAM... or anything other than sheer durability and tenacity (I absolutly adore it)) 
If so what kind of improvements in performance could I expect? 
I don't have a photoshop disk so I won't be able to reinstall it, would I be able to acess photoshop through Xubuntu and run it? That's nonsese isn't it, I suppose I'd have to go to XP every time I wanted to run an XP version of a programe (with the exception of word processors and things I could re-install?) 
Am I risking the whole computer by doing this? Because I can live with it fine as it is, my number one interest with this PC is keeping it alive and able to access the internet for as long as possible, everything else is a bonus. 

I recently took the plunge and ordered a new laptop after 10 long happy years with this computer, so I'll be back here again at some point asking more questions about Ubuntu! For now I'd really appreciate any advice or shared experiances anyone could give me.

---

### Post by snowpine on 2009-08-16
Hi RabbitWho, welcome to the forums! According to the official Xubuntu documentation, your computer falls somewhere between the "absolute bare minimum" and the "recommended minimum" specs: 

> Minimum requirements

    * 333 MHz processor
    * 192 MB of system memory (RAM)
    * At least 1.5 GB of disk space
    * VGA graphics card 

Recommended minimum requirements

    * 800 MHz processor
    * 256 MB of system memory (RAM)
    * 6 GB of disk space
    * Graphics card capable of 800x600 resolution 

In my experience, Xubuntu is about the same speed as Windows XP. I would not expect a big performance gain by switching. There are a lot of other great reasons to switch to Xubuntu, though (free software, no viruses, great community, etc.) so your next step if you're curious is to burn a "Live CD" and test it out with no change to your computer. Try it for a while, and if you like it, you can indeed set up a "dual boot" so you can choose between Xubuntu and Windows each time you start up. (Keep in mind running from the Live CD will be much slower than an hard drive install.)

If your #1 goal is to make your old computer run faster, there are better Linux "distros" for that goal than Xubuntu. Puppy Linux would be a good place to start (fast and user friendly).

---

### Post by LewRockwell on 2009-08-16
Strong vote for Puppy Linux on legacy equipment like that!

I triple-boot a netbook with XP Pro, Ubuntu 9.04, and Puppy Linux

All three run the machine quite nicely, including the wireless

.

---

### Post by HermanAB on 2009-08-16
Hmm, Puppy Linux will likely work on that, but do try to find some more RAM for the poor thing.  Even 256MB will work much better than 192MB.

---

### Post by Jerry N on 2009-08-16
I have tried a lot of different supposedly light Linux distros on that class of machine and I haven't found anything that I consider to be satisfactory.  You could try installing Damn Small Linux but to me DSL is such a kluge that it isn't worth messing with.  Puppy is a lot friendlier.  Old Xubuntu 6.06.1 LTS worked fairly well but I was never able to get it to print on a networked printer.  What works best for me on old machines like that is Windows 2000, which doesn't require activation.  

I noticed that the Aptiva I have has the correct form factor for MicroATX motherboards and I had an ATX power supply, 1 gb of DDR2 RAM, and a spare SATA hard drive so I bought a real cheap Gigabyte mother board and low end Intel dual core processor and built a nice new computer for my workshop.  

Jerry

---

### Post by ashwinhgtx on 2009-08-16
Yes Puppy Linux can be that laptop's saviour. It's very easy to install and configure. Do try it out and let us know about your progress.

---

### Post by halitech on 2009-08-16
> **RabbitWho said:**
> I'm looking for general advice here. And I know nothing so don't be afraid to be patronizing. 

I have a 10 year old IBM Aptiva Intel Pentium 3 - 499 MHz, 192MB RAM, 12 GB hard drive (7GB free)  currently running on XP 

I've already gone through all the usual things to speed up Windows, and while it's working alright now it takes a long time to boot up and Photoshop runs very slowly on it. 

Other than that it's fine, it runs the Internet and can even play music at the same time. [/quote]

very little you are going to do to speed up Win XP on those specs to be honest.

> Would it be possible to dual-boot it with Xubuntu? (I know it's not exactly optimal RAM... or anything other than sheer durability and tenacity (I absolutly adore it)) 

Yes but lack of disk space will eliminate that ability.

> If so what kind of improvements in performance could I expect? 
I don't have a photoshop disk so I won't be able to reinstall it, would I be able to acess photoshop through Xubuntu and run it? That's nonsese isn't it, I suppose I'd have to go to XP every time I wanted to run an XP version of a programe (with the exception of word processors and things I could re-install?) 

again, based on the specs, probably not a lot of improvement. As far as running windows apps, they are windows apps and don't run on linux but there are linux native apps for almost every windows app (and 99% are free) so you should be able to find something for a replacement.

> Am I risking the whole computer by doing this? Because I can live with it fine as it is, my number one interest with this PC is keeping it alive and able to access the internet for as long as possible, everything else is a bonus. 

Only thing at risk would be the windows install itself.

> I recently took the plunge and ordered a new laptop after 10 long happy years with this computer, so I'll be back here again at some point asking more questions about Ubuntu! For now I'd really appreciate any advice or shared experiances anyone could give me.

I would almost go with the instructions here:
[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

and do a Debian minimal install using XFCE or LXDE for the desktop. I've used it on lower specs then yours and worked fine for what they were.

---

### Post by Peterfc on 2009-08-16
Hi Guys

I have an almost identical setup running Openoffice presentation. I run a dispaly in my store and it is never turned of. The monitor is on a timer.I also have Firefox and internet. The internet is only for Updates and firefox for an emergency. Go for it.

I do not use windows on my machines.

---

### Post by RabbitWho on 2009-08-16
Cool! thanks so much everyone! 

I'm reading about Puppy Linux now. 

Some questions:
[I]
"Type of file system used. ([FAT]("http://puppylinux.org/wikka/FAT/edit"), the old [long name]("http://puppylinux.org/wikka/LongFileName/edit") file system used by Microsoft Windows 95 & 98 or [NTFS]("http://puppylinux.org/wikka/NTFS/edit") commonly used by Microsoft [WindowsXP]("http://puppylinux.org/wikka/WindowsXP/edit"))"[/I]
I'm using XP but my computer was originally 98, can I still take it that it's NTFS? 


*"You know that your computer can read and start (i.e. boot) from system CD/DVDs or checked the [BIOS setup]("http://puppylinux.org/wikka/BIOS/edit") of your PC."*

Is it safe to take this as a given? It's just to get into the bios settings I think I have to restart the computer and press F1.. and that might not work, i've never tried it.. and restarting takes ages anyway. 

Other than that I think I'm ready to try it, any other comments or warnings for me?

---

### Post by ashwinhgtx on 2009-08-16
> **RabbitWho said:**
> Cool! thanks so much everyone! 

I'm reading about Puppy Linux now. 

Some questions:
[I]
"Type of file system used. ([FAT]("http://puppylinux.org/wikka/FAT/edit"), the old [long name]("http://puppylinux.org/wikka/LongFileName/edit") file system used by Microsoft Windows 95 & 98 or [NTFS]("http://puppylinux.org/wikka/NTFS/edit") commonly used by Microsoft [WindowsXP]("http://puppylinux.org/wikka/WindowsXP/edit"))"[/I]
I'm using XP but my computer was originally 98, can I still take it that it's NTFS? 


*"You know that your computer can read and start (i.e. boot) from system CD/DVDs or checked the [BIOS setup]("http://puppylinux.org/wikka/BIOS/edit") of your PC."*

Is it safe to take this as a given? It's just to get into the bios settings I think I have to restart the computer and press F1.. and that might not work, i've never tried it.. and restarting takes ages anyway. 

Other than that I think I'm ready to try it, any other comments or warnings for me?

You can check your file system in XP by just right clicking the drive icon in My Computer and clicking Properties. Most probably you are on NTFS.

---

### Post by RabbitWho on 2009-08-16
> **ashwinhgtx said:**
> You can check your file system in XP by just right clicking the drive icon in My Computer and clicking Properties. Most probably you are on NTFS.

Cool beans, thanks, yup, it was NTFS

---

### Post by cariboo on 2009-08-16
I just installed Xubuntu on an iMac Friday, the specs are quite similar to yours 333Mhz ppc cpu 256Mb ram and a 6Gb hard drive. I would suggest replacing Firefox with Opera, though as firefox is a bit of a resource hog.

---

### Post by RabbitWho on 2009-08-16
I went with Puppy Linux in the end, and I am amazed.. I can't believe it, it's like I have a whole new computer, and I'm only using a fraction of the ram. The whole thing is so fast and it has everything I need. I am so happy. I never realized windows was poisoning my computer! I can see it lasting another 10 years now, before every action dived into virtual memory and seemed to cause it actual pain, now it's running faster than my cousins new(ish) mac I'm typing this on! ( because i haven't got the internet running yet, but I'll check the puppy website or go on a puppy forum for that! )

The only problem I had was when I first went to install it I used Nero to burn the disk, just mentioning it as a warning to everyone else! Don't use Nero to burn bootable disks! 


Thanks so much to everyone for your help and advice. I think I'm going to go out and buy a "linux for dummies" book an find out how and why these things are so amazing. 

Ahhh i can't beleive how happy I am, I've brought my beloved old computer back from the dead.. and it's acting like I've been given a brand new computer absolutly free.

---

### Post by Jerry N on 2009-08-16
"*The only problem I had was when I first went to install it I used Nero to burn the disk, just mentioning it as a warning to everyone else! Don't use Nero to burn bootable disks!*"

I don't understand that statement!!  I have burned well over a hundred bootable disks with Nero, both in Windows and with NeroLinux in Ubuntu.  I always burn them at 40X and have had only one or two failures which were caught during Nero's verification and were probably bad media. 

Jerry

---

### Post by JC Cheloven on 2009-08-16
> **RabbitWho said:**
> I went with Puppy Linux in the end, and I am amazed.. I can't believe it, it's like I have a whole new computer, and I'm only using a fraction of the ram. The whole thing is so fast and it has everything I need. I am so happy. I never realized windows was poisoning my computer! I can see it lasting another 10 years now, before every action dived into virtual memory and seemed to cause it actual pain, now it's running faster than my cousins new(ish) mac I'm typing this on! ( because i haven't got the internet running yet, but I'll check the puppy website or go on a puppy forum for that! )

...

Thanks so much to everyone for your help and advice. I think I'm going to go out and buy a "linux for dummies" book an find out how and why these things are so amazing. 

Ahhh i can't beleive how happy I am, I've brought my beloved old computer back from the dead.. and it's acting like I've been given a brand new computer absolutly free.

So, what an excitement! I also like to put these oldies to work again :-D But don't get disapointed when yotube videos chunks. Try to use a lighter browser than firefox (epiphany...), and try to get some more ram: it's incredibly easy to find some compatible 192 or 256 Mb module for these old machines (open your box and note the specs of your ram). Last time I mixed up a 64Mb module with a couple of 128Mb ones (I bougth both for 5€), and they worked fine. It's also incredibly easy to plug them, don't get afraid, It is worth. You'll have better reasons to get amazed.

You probably did a frugal puppy install, which is a good thing. 
In my experience, puppy usually has no problems with network cards of old computers. I hope you'll find your way around.

Finally, the Gimp can do almost everything photoshop does. The learning curve is a bit steeper because the documentation isn't as good, though. 

Best of luck
________________________

---

### Post by R_W322 on 2009-08-17
Sorry if this is already been posted but a second suggestion isn't a bad one. You should consider using or atleast trying DSL (damn small linux) I'll post the minium specs. 

from damnsmalllinux.org: 

[LIST]
[*]Run light enough to power a 486DX with 16MB of Ram
[*]Run fully in RAM with as little as 128MB (you will be amazed at how fast your computer can be!)
[/LIST]
Enough said use. 

RYAN.WDZIECZNY

---

### Post by ashwinhgtx on 2009-08-17
> **RabbitWho said:**
> I went with Puppy Linux in the end, and I am amazed.. I can't believe it, it's like I have a whole new computer, and I'm only using a fraction of the ram. The whole thing is so fast and it has everything I need. I am so happy. I never realized windows was poisoning my computer! I can see it lasting another 10 years now, before every action dived into virtual memory and seemed to cause it actual pain, now it's running faster than my cousins new(ish) mac I'm typing this on! ( because i haven't got the internet running yet, but I'll check the puppy website or go on a puppy forum for that! )

The only problem I had was when I first went to install it I used Nero to burn the disk, just mentioning it as a warning to everyone else! Don't use Nero to burn bootable disks! 


Thanks so much to everyone for your help and advice. I think I'm going to go out and buy a "linux for dummies" book an find out how and why these things are so amazing. 

Ahhh i can't beleive how happy I am, I've brought my beloved old computer back from the dead.. and it's acting like I've been given a brand new computer absolutly free.

Congrats. Enjoy your new pet. 
:guitar:

---

### Post by PhilGil on 2009-08-17
> **RabbitWho said:**
> Ahhh i can't beleive how happy I am, I've brought my beloved old computer back from the dead.. and it's acting like I've been given a brand new computer absolutly free.
I agree, Puppy Linux is a wonder.  I use it on a 10 year old Compaq laptop that used to run Windows 98.

---

### Post by JC Cheloven on 2009-08-17
> **R_W322 said:**
> Sorry if this is already been posted but a second suggestion isn't a bad one. You should consider using or atleast trying DSL (damn small linux) I'll post the minium specs. 

from damnsmalllinux.org: 

[LIST]
[*]Run light enough to power a 486DX with 16MB of Ram
[*]Run fully in RAM with as little as 128MB (you will be amazed at how fast your computer can be!)
[/LIST]
Enough said use. 

RYAN.WDZIECZNY

Damn Small Linux is amazing, and pretty much my favourite for old machines, but I'm unsure whether it is being supported at this time. The project seem to have run into internal problems last year, and no much activity is seen since dec08:

[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=4;t=20537](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=4;t=20537)

Indeed a pity ... but I can't recommend a non supported distro.

---

