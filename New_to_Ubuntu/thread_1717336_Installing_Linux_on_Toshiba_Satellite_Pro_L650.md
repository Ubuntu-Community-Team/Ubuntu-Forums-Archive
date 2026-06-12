---
title: "Installing Linux on Toshiba Satellite Pro L650"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by cytochrome on 2011-03-29
Hi there.

I recently purchased a computer of the aforementioned make/model with preinstalled Windows 7 Professional but want to install a Linux distribution.

I considered Ubuntu 10.10, reportedly to work but with some headphone and Internet connectivity issues, and having Google searched and searched Linux and Ubuntu Forums, I don't exactly know what to do. Some posts on the WWW suggest that installation does not work due to a BIOS thing or some other hundred computer things that I, with a low level of MS ancient Windows till Windows XP-using knowledge, don't understand.

I would very much appreciate help regarding successful dual-booting installation of a "good" distribution (thus far, I am to understand that Ubuntu, openSUSE, and Fedora or something else starting with an F; I've also downloaded the .iso's but I don't know what to do and I'm fearful of accidentally destroying my computer) without too much fuss or stress. Furthermore, a suggestion as to how I might divvy my HDD (~650 GB) would be appreciated; lots of irreplaceable software is Windows-only so I would probably need to keep that partition moderately large.

As both Windows 7 is novel for me (its navigation being overhauled from Windows XP) and Linux is virtually wholly foreign, I may need steps, as in step-to-step instructions.

This might seem terribly lazy or stupid; but, I genuinely don't have too much of a clue about Linux and am trying to acquaint myself better (still, I don't know where I should have started in my acquainting or where I'm supposed to be going). Cheers!

---

### Post by kitsuneclem on 2011-03-29
> **cytochrome said:**
> Hi there.

I recently purchased a computer of the aforementioned make/model with preinstalled Windows 7 Professional but want to install a Linux distribution.

I considered Ubuntu 10.10, reportedly to work but with some headphone and Internet connectivity issues, and having Google searched and searched Linux and Ubuntu Forums, I don't exactly know what to do. Some posts on the WWW suggest that installation does not work due to a BIOS thing or some other hundred computer things that I, with a low level of MS Windows-using knowledge

I would very much appreciate help regarding successful dual-booting installation of a "good" distribution (thus far, I am to understand that Ubuntu, openSUSE, and Fedora or something else starting with an F; I've also downloaded the .iso's but I don't know what to do and I'm fearful of accidentally destroying my computer) without too much fuss or stress. Furthermore, a suggestion as to how I might divvy my HDD (~650 GB) would be appreciated; lots of irreplaceable software is Windows-only so I would probably need to keep that partition moderately large.

As both Windows 7 is novel for me (its navigation being overhauled from Windows XP) and Linux is virtually wholly foreign, I may need steps, as in step-to-step instructions.

This might seem terribly lazy or stupid; but, I genuinely don't have too much of a clue about Linux and am trying to acquaint myself better. Cheers!
install as Wubi while in the windows mode place the Live disk into the comp and instlall the Wubi This is a great way to try Ubuntu with out even a single chance of wrecking the windows partisan

---

### Post by bcbc on 2011-03-30
I believe you'll need the following kernel boot option: acpi=copy_dsdt (see [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/647358](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/647358))

Also, if you have BIOS version 1.40 there's probably a 1.60 update you can install. That's based on a couple of support threads I've come across, not personal experience.

So, how do you install with these boot workarounds... see this thread: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
If you happen to use Wubi, then there is a post #8 in this thread which discusses the Wubi install.

Finally... I recommend creating an Ubuntu CD or USB and booting in 'live cd/usb' mode i.e. boot from it and select "Try it" (try without installing). You can play around with the boot override options, and make sure everything is good before installing.

---

### Post by Andavane on 2011-03-30
Indeed.
If you burn your *.iso to a CD, you can boot from that, and see for yourself what issues you will/won't get with Ubuntu.
Just remember that when you do that, it will take longer to boot up cos your CD is acting like a hard drive.

This method won't touch anything on your existing installation, neither will using wubi.

---

### Post by cytochrome on 2011-03-31
Hi there.

Would any of you know as to why my system became a 32-bit system despite my choosing to run 64-bit Windows 7 (pre-installed OS that has not yet been booted) at the initial boot-up? It's very bizarre.
> **bcbc said:**
> I believe you'll need the following kernel boot option: acpi=copy_dsdt (see [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/647358](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/647358))Okay... haha, now I have to understand these boot options.
> Also, if you have BIOS version 1.40 there's probably a 1.60 update you can install. That's based on a couple of support threads I've come across, not personal experience.Oh, okay. Thanks.

I ran sysinfo32 and discovered that my BIOS is INSYDE 1.80, 1/09/2010. I don't understand what any of that means though and what the implications of that are.
> So, how do you install with these boot workarounds... see this thread: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
If you happen to use Wubi, then there is a post #8 in this thread which discusses the Wubi install.

Finally... I recommend creating an Ubuntu CD or USB and booting in 'live cd/usb' mode i.e. boot from it and select "Try it" (try without installing). You can play around with the boot override options, and make sure everything is good before installing.Okay, that's great. Thanks!

If any of you could list a couple of software that are made available by Ubuntu or link to a list, that would be greatly appreciated. I think I may need to convince myself to use Ubuntu (or some Linux distro.), if but partially/with MS Windows.

---

