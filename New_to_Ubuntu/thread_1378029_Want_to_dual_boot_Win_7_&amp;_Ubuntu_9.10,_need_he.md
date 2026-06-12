---
title: "Want to dual boot Win 7 &amp; Ubuntu 9.10, need help installing Ubuntu"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Lazerfingers on 2010-01-10
So the last time I tried to install Ubuntu beside Windows was about a year ago and it was on an older model Dell laptop running XP sp3. I defragged the HD twice and then ran the Ubuntu CD installer. I was given the option to set up a new Ubuntu partition and it said yes, clicked an appropriate partition size, and then the installer went to work. A few minutes later I get an error saying that there was an error when trying to partiton the HD and I must quit.
I try to reboot and get a blank screen after the BIOS. My original Windows install doesn't show up and obviously neither does Ubuntu. Thus I am forced to install Ubuntu on the entire drive and my love for Linux was born. :)
Now I find myself with a shiny new laptop with Win 7 64 bit installed on it and I'm severely missing Ubuntu.
How can I get Ubuntu 64bit back on my computer without risking wiping my Windows install, and without doing the BS "inside Windows install" (I forget what it's called) that doesn't allow you to keep your settings and programs when you upgrade to a new version of Ubuntu.

Thanks for any help given. :)

---

### Post by tom.swartz07 on 2010-01-10
> **Lazerfingers said:**
> So the last time I tried to install Ubuntu beside Windows was about a year ago and it was on an older model Dell laptop running XP sp3. I defragged the HD twice and then ran the Ubuntu CD installer. I was given the option to set up a new Ubuntu partition and it said yes, clicked an appropriate partition size, and then the installer went to work. A few minutes later I get an error saying that there was an error when trying to partiton the HD and I must quit.
I try to reboot and get a blank screen after the BIOS. My original Windows install doesn't show up and obviously neither does Ubuntu. Thus I am forced to install Ubuntu on the entire drive and my love for Linux was born. :)
Now I find myself with a shiny new laptop with Win 7 64 bit installed on it and I'm severely missing Ubuntu.
How can I get Ubuntu 64bit back on my computer without risking wiping my Windows install, and without doing the BS "inside Windows install" (I forget what it's called) that doesn't allow you to keep your settings and programs when you upgrade to a new version of Ubuntu.

Thanks for any help given. :)

Okie dokie!
Rather than just cut and paste a link here, Ill talk you through it.

I would suggest, before you begin, Boot into Windows and run a defrag a few times. Delete any junk on the OS that you wont need and defrag one last time. This will assure that all of the data on your drive is as compacted and continuous as possible.

Next. Check for BIOS updates. Most of the time you could skip this step, as there arent too many BIOS updates, but If there is- its imperative that you install it. 99% of the time you just run the file in windows and restart your computer when it tells you to. (I say you update the BIOS because it helps assure that you have the most stable base for your computer when it boots up)


Now, Download and burn Ubuntu to a CD. 9.10 is the current version.

Pop it in your drive and restart. Boot to the cd- you might have to fiddle with it to get it- every computer uses a different key, but its usually F10, F12, or ESC.

Once thats running, you could install side by side. (im going to wimp out here on you and post a link, but trust me- its really worth it)

This guide will show you, step by step, screen by screen how to install dual boot. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

From there, youre all set!

Good luck! Enjoy that shiny new hot rod!

---

### Post by Lazerfingers on 2010-01-11
Wow, this is exactly what I needed.  Thank you for the very thoughtful reply.  

You've made me even more anxious to get back into Linux and become an active member of it's awesomely civilized community.

Cheers!

---

### Post by cloyd on 2010-01-11
I invite further comments from those more experienced than I.  I have successfully installed Ubuntu on a grand total of two machines now, both with dual boot. Both were running Vista.  I read instructions from "Idiots Guide to Linux" over and over until I think I came to understand them, and I did one thing different from what many people seem to do. 

First, I defragged my hard drive (shoulda done it twice, just did it once, but it worked.)

Second, I used utilities in Vista to _shrink_ my C (or D drive in one case).

Third, I installed Ubuntu using the option, "Use largest free space."

What I think I did differently from many of the instructions I see on this forum was to shrink my Vista drive using utilities in Vista (thus creating free space for the Ubuntu partition) before creating the Ubuntu partition.  Vista created the empty space, but Ubuntu actually created the partition for the install in the empty space.

Again, _I invite comments from other, more experienced users_ before saying, "This is the way to go." I may have just been lucky, but so far I have had no problems with losing data.  Both systems successfully dual boot.

---

### Post by audiomick on 2010-01-11
@ cloyd
The only thing that is missing, going by what I have been seeing in the forum over and over again, is to start Windows a couple of times after shrinking to let it have a chance to do file system checks and what have you.

Using Windows tools to shrink Vista and Win7 partitions seems to be the recommended way to do things.

---

