---
title: "Compatibility."
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Paul Hurley on 2009-03-06
Hi everyone

I'm not yet a ubuntu user - but but very close to jumping aboard.
But before I make the leap, I've got a couple of questions (hope this is the right place to do it).
I've got an Acer Aspire 5930G laptop. tried to get the live CD going but it wouldn't install. I checked on the internet and read some blogs that said the live CD wasn't compatible with my laptop. So, does that mean I won't be able to install the full ubuntu programme? Or is it just the live CD that is incompatible?

Also, I've heard of problems with wifi. Is this true?

Look forward to hearing from you.

paul

---

### Post by binbash on 2009-03-06
You may have sound problems but it is fixable, i do not know wifi part.

---

### Post by 67GTA on 2009-03-06
You can use the alternate (text based) CD to install if you have problems getting the live CD to work. You will have the same as the graphical install. What wifi card do you have?

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Your laptop here: [https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5930G](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5930G)

---

### Post by DGortze380 on 2009-03-06
> **Paul Hurley said:**
> 
the full ubuntu programme?

Ubuntu isn't a program, it's full Operating System.

(wubi and virutal machiens aside...) If you're under the impress that it will install and be turned on and off like any other 'windows' program, you really should do more research first to avoid big issues.

---

### Post by Paul Hurley on 2009-03-07
Thanks for the above info.

When I try to run the live CD I get:busybox v1.1.3 inittramfs revalidation failed erno 5/comrest failed
It runs fine on the desktop - so it's not the CD.

My wifi is 802.11 a/b/g/Draft N-WLAN

Apologies for the lazy language - I know ubuntu is an OS, not a programme. I shall choose my words with care fom now on.

---

### Post by 67GTA on 2009-03-07
What version are you trying to run(8.10, 8.04)?Sounds like the kernel is having trouble with some of your hardware. You might try booting with different boot parameters. Try these one at a time to see if any of them make a difference. At the boot menu, hit F6, and then add to the end of boot text that appears at the bottom of the screen. Also try the second line down from the top(recovery mode). If none of these work, then try the alternate CD.

all_generic_ide
acpi=off
acpi_osi="Linux"
nolapic[FONT=monospace]
[/FONT]noacpi 
noapic
pci=noacpi[FONT=monospace]
[/FONT]irqpoll

---

### Post by Paul Hurley on 2009-03-08
Thanks 67GTA - I'll get onto it asap.

---

