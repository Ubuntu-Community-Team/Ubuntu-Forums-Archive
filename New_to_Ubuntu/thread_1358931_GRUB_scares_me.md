---
title: "GRUB scares me"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by manny43 on 2009-12-19
I'm thinking of installing a second operating system like SimplyMepis but i've been told that
once Mepis is installed Ubuntu will not automatically add the new operating system to GRUB
what's keeping me from installing new os is the fact that i have no idea how to add another
operating system to GRUB.iF you guys could show me the steps on how to do it whenever
you have the time.Thank you

---

### Post by Elfy on 2009-12-19
With grub legacy it was fairly easy and there are many threads on the forums about that, grub2 is not quite so simple but there is this [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by cenzorrll on 2009-12-19
I highly recommend reading the link above, there's lots of good entries in there.

an issue that will most likely come up when installing mepis is that it will probably not be using grub2, which probably won't even be an issue.  however it does mean that it will install grub legacy to the MBR, again not likely an issue, as it SHOULD find your ubuntu boot information and add that autmatically.

what i would suggest, if possible, is to install mepis except for the boot loader (i know it's possible when doing a advanced/expert install). then boot into ubuntu and type: ```
sudo update-grub
``` this should search your drive(s) for other operating systems and add them to the list.  if that doesn't work, you can always do it manually by adding an entry to /etc/grub.d/40_custom

again, i suggest reading the grub2 info above before deciding on what you want to do.

---

### Post by audiomick on 2009-12-19
+1 cenzorll

I have always avoided changing things in grub too, as it makes me nervous, but it isn't that hard actually, from what I have read.

It is certainly the case that grub is designed to deal with multiple boot situations, so you can assume that it will deal with what you want to do.

If you find yourself dealing with legacy grub rather than grub 2, read about it here:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by madmax.santana on 2009-12-19
I got hard-beaten by GRUB (technically, GRUB Legacy) but now I guess I am enough qualified to give you some "inside" information... :P
I used to dread GRUB too, but yeh know what? It's "THE" best... (Well that's my opinion)...

About adding another OS to your system, I guess it will be way easy if you have grub legacy. [COLOR=Red]Even if it doesn't automatically read your boot information[/COLOR], you can add the particular OS to your

> /boot/grub/menu.lst

Just open it and go to "GRUB Automagic Options" (It's nothing but an autmatically generated list of OSystems on your system. If GRUB got it, it is already in the list. If it didn't you can add this... )

Enter

> title Whatever
root (hdA,B)
makeactive
chainloader +1
boot

[COLOR=Red]Don't forget to replace (hdA,B) with the particular path of drive you have installed your new OS on... (Like for me it's (hd0,5))[/COLOR]

This thing is mostly used in cases you don't have a kernel image already in your grub directory. See, whenever it reads a new kernel it automatically copies a boot image of the particular kernel in grub directory. But if it doesn't you can manually force it to find the boot-sectors every time it boots.

I guess it would be simple. But I am still an amateur. So pardon errors if any. :) Have tried my best to explain but forgive wordiness and any of too much technical jargon. Hope grub won't be a mystery for you for long. Happy Ubuntuing.

---

### Post by cfirpo99 on 2009-12-19
Hello

Im trying to go back to 8.04 from 9.10 because I may be in over my head. So I boot up with the new ISO I burned for 8.04 LTS and it boots straight into GRUB shell (is that by design on the CD?). Ive read that the GRUB shell wont boot the ISO from the CD, and im assuming GRUB gets called because it sees the current install from 9.10 on the HD.

Bios is set to boot CD 1st.  If i boot with the 9.10 CD it works just fine as a test. For some reason the GRUB shell (1.97 beta) loads every time I use the 8.04 LTS CD, then im stuck.  It sees the previous install because GRUB is asking me to choose and OS from the menu or go to prompt.  I know there are a bunch of commands in the shell but dont know if that will help me or how to.

How can I just do a clean install to 8.04?  The HD is still loading into 9.10 without a problem, but i have no idea how to format the drive or run the install (iso) from within Linux if at all possible.


Thanks in advance

---

### Post by Gone fishing on 2009-12-19
I run a multiple boot system Karmic,Windows 7, and Haiku. I recommend GAG very easy to setup and I then install grub on the root partition. I did have a problem with Karmic I assume because of ext4, however this was easily resolved by making a small ext3 boot partition.

It is posible that the latest GAG works with ext4.

---

### Post by Elfy on 2009-12-20
> Just open it and go to "GRUB Automagic Options" (It's nothing but an autmatically generated list of OSystems on your system. If GRUB got it, it is already in the list. If it didn't you can add this... )If you are adding OS's to the list then make sure they are outside of the Automagic part of the list or you will lose them.

---

### Post by ranch hand on 2009-12-20
Grub2 does NOT kill kittens and is much more flexible than grub-legacy.

There is a learning curve as it is not at all the same.  Keep in mind, hard as it is to believe, grub-legacy was popular as a turd in the punch bowl when released.

If you read the link in my sig you will know a lot more about grub2.  The second link in my post is written by the guy who wrote most of the info in the above link.  The advantage of his post here in the How to section is that  his sig has links to his other How To's that are equally great.

Mempis will not pick up your Ubuntu either because (unless they have updated since I last looked) their version of grub-legacy does not support ext4.

You will have to use this guide to restore your grub2.  Remember that you need a Live CD for 9.10 or above (I am in 10.04-testing where we use 1.97 instead of 1.97beta4 as in 9.10).  here is the link;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

drs305 is one of us that have fooled with grub2 since 9.10testingAlpha2 when it was released on us.  It was a rough, but FUN, ride for a while.

I highly recommend the use of a custom menu (see sig) with the "symbolic" menuentry for all your Debian based OS'.  They never need to be updated for kernels and you can then disable all scripts above 10_linux (including that one if you want).  Makes things very neat and fast.

Mepis will be picked up by os-prober.  The generated entry will not, probably be correct although it may be editable.  The entry example I give (see sig) for mandriva will probably work just fine for Mepis in a custom menu.

---

### Post by ikt on 2009-12-20
> **manny43 said:**
> I'm thinking of installing a second operating system like SimplyMepis

If you're thinking of just mucking around I would suggest using virtualbox instead as this makes the issues of installing, configuring and removing the other operating systems much easier.

---

