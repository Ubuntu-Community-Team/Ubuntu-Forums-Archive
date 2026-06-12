---
title: "I can't install any operating systems thanks to Grub."
date: 2010-09-23
forum: New to Ubuntu
---

### Post by BobPOW on 2010-09-23
I used to have Ubuntu 10.04.1 on my computer.  Last night I got tired of  the operating system, and decided to replace it with ReactOS.

So  I burned the latest version of ReactOS on a CD, erased my only  partition, and installed ReactOS.  When the computer rebooted, I get a  message:

error: file not found.
grub rescue>

I ask  around on the ReactOS forums, and the members inform me that I still  have Grub on my hard drive.  They told me to come here for advice on  removing Grub, because they don't know much about Linux.

So community, how do I remove this Grub?  I'd really love to get my computer back to working status.

---

### Post by uRock on 2010-09-23
ReactOS should have installed its own boot loader. Grub does not prevent other OSes from writing over it.

---

### Post by Calash on 2010-09-23
Grub is the bootloader.  You can easily erase it with several methods but the real question is what does ReactOS need for a bootloader.

I do not know off the top of my head, but their website would be the first place to look.


Edit: looks like it uses something called FreeLoader.  Check this link for some info.

[http://www.reactos.org/wiki/FreeLoader](http://www.reactos.org/wiki/FreeLoader)

---

### Post by eriktheblu on 2010-09-23
That looks more like your MBR is pointing to Grub, but Grub is not there.

What you probably need to do is fix the MBR to indicate the ReactOS boot loader, but I don't know how to do that.

How many internal hard drives do you have? If you have more than one, it could be as simple as changing your boot order in the BIOS.

---

### Post by uRock on 2010-09-23
ReactOS uses [FreeLoader]("http://www.reactos.org/wiki/FreeLoader").

---

### Post by drs305 on 2010-09-23
Grub is still installed on the MBR. You will have to ask the ReactOS users how to install it's bootloader, or wait for someone here who knows how to do it. 

You can wipe Grub off the MBR with TestDisk, but unless you replace it with another bootloader it won't help you.

---

### Post by BobPOW on 2010-09-23
> **uRock said:**
> ReactOS should have installed its own boot loader.  Grub does not prevent other OSes from writing over it.
  
  After ReactOS has installed, it asks me if I want to install the boot  loader.  I've tried installing it both with the boot loader, and without  the boot loader.  Neither works.
 
 > **eriktheblu said:**
> That looks more like your MBR is pointing to Grub, but Grub is not there.

What you probably need to do is fix the MBR to indicate the ReactOS boot loader, but I don't know how to do that.

How many internal hard drives do you have? If you have more than one, it  could be as simple as changing your boot order in the BIOS.

I have one internal hard drive.

> **uRock said:**
> ReactOS uses [FreeLoader]("http://www.reactos.org/wiki/FreeLoader").

Cool.  How do I use this FreeLoader?

---

### Post by scrooge_74 on 2010-09-23
Funny how you install another OS, it breaks and you blame it on Linux. Then you keep asking how to install the other OS in the wrong place is there a ReactOS you could go and ask the proper questions there?

---

### Post by BobPOW on 2010-09-23
> **scrooge_74 said:**
> Funny how you install another OS, it breaks and you blame it on Linux. Then you keep asking how to install the other OS in the wrong place is there a ReactOS you could go and ask the proper questions there?

It helps if you read the original post before mouthing off like a fanboy.  I said that I went to the ReactOS forums first, and they directed me here.

If you can help me, that's great.  If not, then leave the community alone.  We are busy having a mature conversation.

---

### Post by uRock on 2010-09-23
> **BobPOW said:**
> Cool.  How do I use this FreeLoader?
The link provides instructions on how to manually install FreeLoader.

---

### Post by scrooge_74 on 2010-09-23
> **BobPOW said:**
> It helps if you read the original post before mouthing off like a fanboy.  I said that I went to the ReactOS forums first, and they directed me here.

If you can help me, that's great.  If not, then leave the community alone.  We are busy having a mature conversation.

Again if you break it you get to keep all the parts.

They sent you here cause they had no clue. 

I have helped along a quite a good number of people so if you are upset cause you dont understand a system is not me/community fault.

That statement of yours when you said you got tired of the OS sounds more like you never got the hang of it and want a drop in Windows replacement.

---

### Post by QLee on 2010-09-23
[QUOTE=BobPOW]...
 I said that I went to the ReactOS forums first, and they directed me here.[/QUOTE]
Gee, I wonder why they would do that, they should be the experts in installing their bootloader in the MBR.

As you have been told, we could help you remove GRUB but that would not give you a booting system.

[QUOTE=BobPOW]..  We are busy having a mature conversation.[/QUOTE]
To me it appears as if only parts of the conversation are mature and respectful.

Sorry we didn't get a chance to welcome you to the forums before you finished with Ubuntu. I hope you have good luck with that alpha software OS.

---

