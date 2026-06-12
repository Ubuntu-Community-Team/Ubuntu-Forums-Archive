---
title: "How do you install Ubuntu in an Android Superpad???"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by joseph2221 on 2011-01-17
The Super Pad i got from China looks great, but I HATE Android. You would think since Droid is Linux too it would boot from the usb-- it doesn't. 

-Joseph

Here's a Youtube  link to the model.

[http://www.youtube.com/watch?v=zE2J9leO3EE](http://www.youtube.com/watch?v=zE2J9leO3EE)

Heres the manual:

[http://www.onderka.com/wp-content/Manual-ZH10X2.pdf](http://www.onderka.com/wp-content/Manual-ZH10X2.pdf)

---

### Post by fabricator4 on 2011-01-17
> **joseph2221 said:**
> The Super Pad i got from China looks great, but I HATE Android. You would think since Droid is Linux too it would boot from the usb-- it doesn't. 

Hi, USB booting is a function of the hardware and the BIOS, nothing to do with the OS.  There is no OS until the machine has booted...

The technical information given in the "manual" is useless.  I had to look elsewhere to even find out that it's running an ARM 11 CPU though I'd guessed it would be.

There's no findable (Google) information on hacking the ZH10X2-PAD which is generally the case for off-brand products from China unless they gain a great deal of popularity, like the BeBook Ereader for example, which occurred to a large degree because the source code is freely available.

Your pad appears to have 2GB internal storage available for the OS which would be enough for a light Linux install, however you might lose functionality if proprietary or unusual hardware is not supported.  My guess would be that the internal memory would be flashed from a card inserted into TF1: logical but not necessarily the case.

A starting point for the OS would be the  [*Ubuntu ARM wiki*]("https://wiki.ubuntu.com/ARM").  Unless you can find someone who's already done it you might be in for a great deal of frustration however, or even a pad that doesn't work anymore.

Why not just enjoy your pad for what it is, rather than what it isn't?

Chris.

---

### Post by ncmoody on 2012-03-22
I am in the same boat as Hoseph2221

I have a superpad and also diskile Android, as a long time Linux user I would love to convert.

The details of my pad are :-

ibex flytouch 3
tim 6
disco10
2.2-20110803
Kernel 2.6.32.9
zjd@dtlinuxserver #36
Build FRF85B-tim6a

uname -a give armv61

Label on back = infoTMIC android 2.2 DDR II 512M Hard disk 16GB


Now I understand that the Tim 6 upgrade was installed by booting from a MicroSD card and the new frimware was copide / flashed over.

So it seems to me there is a mechanism to boot thios device from the microSD card.
But having searched the internet and posted questions on fora for bithe the pad and Android I have bot found any details.

Does anyone know the boot mechanism is it similar to Grub or Lilo 

Is there a ready made solution to run any Linux ( preferably a ubuntu variant) on the superpad directly from the microSD without touching the android firmware.

I knopw this is a big ask but any pointers would help.

Regards

---

### Post by Dharkheart on 2012-05-12
I have a ViMicro Flytouch 6 vortex 10 tablet with 512mb ram, 8gb onboards and 32gb microsd. I am running Android 2.3 Gingerbread and I would like to install Ubuntu onto this tablet as I would greatly prefer it to the Android OS.
 
[LIST]
[*]I have gained root access via gingerbreak but aside from that I am uncertain as to how I should go about installing Ubuntu. Which version do I select and how do I get it onto my tablet? Haven't guessed I'm virtually a noob at this? Shame on you! LOL!
[*]Seriously I would appreciate an answer as I have searched the web and I can't find one. Thanks.
[/LIST]

---

### Post by holycow131415 on 2012-05-13
[http://androlinux.com/](http://androlinux.com/)

Though i dont think that is truely running off the device alone without being connected via computer.

Also, [http://www.ubuntu.com/devices/android](http://www.ubuntu.com/devices/android) is coming soon.

---

