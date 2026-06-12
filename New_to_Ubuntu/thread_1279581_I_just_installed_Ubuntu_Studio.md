---
title: "I just installed Ubuntu Studio"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by bruce leroy on 2009-10-01
I just installed Ubuntu Studio.  System rebooted after installation.  I'm getting a message "Alert! ?DEV/MAPPER/ORBITAL-ROOT DOES NOT EXIST.DROPPINT TO A SHELL".. then "C:COULDN'T FIND AN INPUT INTERRUPT ENDPOINT".  I'm a beginner in all of these and don't know what could be the problem.  I looked like everything was ok when i loaded it.
Please help!

---

### Post by egalvan on 2009-10-01
> **bruce leroy said:**
>  . then "C:COULDN'T FIND AN INPUT INTERRUPT ENDPOINT".

I don't use Studio, I use regular Ubuntu/Kubunt/Xubuntu.


I have two machines connected via a KVM (Keyboard Video Mouse)
interface,
and when I switch away during the boot cycle, I get that

C:COULDN'T FIND AN INPUT INTERRUPT ENDPOINT

error...

it may not be related, but it's a start.

---

### Post by ErikEhlert on 2009-10-01
Hm, well it seems like its a problem with your Hard Drive itself, what did you use to install UStudio? if you used a disc did you burn to a clean CD? Where exactly did it start showing this message? Was this after you went into the Live CD and put in all you settings or when you booted off the CD for the first time?

---

### Post by bruce leroy on 2009-10-01
I got the install CD from Linux Format magazine.  I get this message after I've selected all my settings.  It seemed like the install went well.  I had no errors.  I type in reboot after the message and I still get it after.

---

### Post by bruce leroy on 2009-10-01
The KVM switch was causing the C:COULDN'T FIND AN INPUT INTERRUPT ENDPOINT issue.  But, I still can't pass the text messages from booting.  The other message is MISSING MODULES (CAT/PROC/MODULES;LS/DEV).  I'm new to Ubuntu and I have no idea what this means and how to fix it.

---

### Post by starcannon on 2009-10-01
NM I don't know.

---

### Post by bruce leroy on 2009-10-03
I just entered EXIT and got the system to boot up.  Can't believe I figured this out by myself.  Ubuntu Studio running but really slow.  Download speedt at around 40 kb/s, it's ridiculous.  What could be the problem?

---

### Post by starcannon on 2009-10-03
> **bruce leroy said:**
> I just entered EXIT and got the system to boot up.  Can't believe I figured this out by myself.  Ubuntu Studio running but really slow.  Download speedt at around 40 kb/s, it's ridiculous.  What could be the problem?
Ubuntu Studio uses a special Low Latency Kernel(which has given me headaches in the recent past); I started to post about it earlier, but was unsure if that was your issue, so removed my post.

My advice, for what it is worth, is to download a regular Ubuntu ISO, install that, then add the Ubuntu Studio packages and then boot from the Generic Kernel on start up.

You can get the "regular" Ubuntu ISO [here]("http://www.ubuntu.com/getubuntu/download"), I recommend the 8.04 LTS(Long Term Support) version(in general stick with LTS versions). Reinstall, then, once you have Ubuntu up and running, come on back, P.M. me to get my attention, and I'll steer you towards the Ubuntu Studio packages.

GL and HF

P.S.
Please attach a copy of 
```
lshw > ~/Desktop/hardware.doc
```
just to help determine whether or not it may be a hardware problem.

---

