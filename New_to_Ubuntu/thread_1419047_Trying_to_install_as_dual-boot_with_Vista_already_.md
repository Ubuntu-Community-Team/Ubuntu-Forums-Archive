---
title: "Trying to install as dual-boot with Vista already installed"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by lindsaybits on 2010-03-01
First things first: i am NOT well-versed in Linux. A while back, i tinkered with Hardy Heron on an older computer, and generally liked it, but ultimately didn't stick with it. I can't recall the exact reasons, but i vaguely remember it having something to do with the system being really slow.

Fast forward to present day. I have a newer computer - AMD 64 dual core processor, 3 GB of RAM, and am currently running Vista. It's an XFX motherboard, with mostly nVidia bits on it. I suppose it should also be stated that i am NOT a hardware geek; i can troubleshoot software like whoa, but once hardware gets involved, i make my husband fix it. :p

So a few days ago i got the idea of setting up a dual-boot Vista/Ubuntu, using the Vista install i already have running (since my Vista disc is AWOL). I found a great walk-through on acpmag.com, downloaded the ISO for 9.10, and started trying to install Ubuntu on a separate partition on my HD.

To say it didn't work is a bit of an understatement. I spent no less than eight hours trying to get it working, and it just was not happening.

At first, it would start the install, give me the logo, and then sit on a blank screen for as long as i let it - up to 15 minutes. 

When i would reboot it, i would catch a brief glimpse of an error message before the system restarted. The first error messages were about being unable to find the ISO. I googled this and found that it could be a problem with the disc, so i tried the "check disc for defects" option. It just gave me the same blank screen and error message. So i created a new disc using InfraRecorder (using the slowest write speed), and tried that. Still no go. I found something through google that indicated it might be an issue with my HD, so i ran **chkdsk /r /f** - no bad sectors, everything came back just fine. Took almost three hours, but those episodes of DS9 weren't going to watch themselves, so that was okay.

At that point, i started trying other types of installs. The "safe graphic mode" led to the ever-present blank screen.

This is about when i figured out that instead of holding the power button to hard boot it, if i hit the power button and released it, it would drop me into a shell, complete with error messages.

I tried it with the ACPI workaround install method, and that actually installed! Holy snap! I let it finish the install, rebooted when it asked me to do so, and tried to boot into Ubuntu, only to see the following: [INDENT]Gave up waiting for boot device. Common problems:
- Boot args (cat /proc/cmdline)
- check rootdelay = (did the system wait long enough?)
- check root = (did the system wait for the right device?)
- missing modules (cat /proc/modules ; ls /dev)
ALERT! /dev/sda1 does not exist. Dropping to a shell!
[/INDENT]I figured i'd borked the install somehow, so i went back into Vista, undid my blank partition (i had also tried it as "unallocated space", same problems), and tried to install it with Wubi. Same error message that i quoted above.

This is where i got my husband involved. He did some research and found a bunch of articles talking about how some people just could not get 9.10 installed for love nor money. I decided that 9.10 just didn't like my computer, so i'd give 9.04 a whirl. I downloaded the ISO for that release, and snagged Ubuntu Studio 9.04 while i was at it. Burned both to discs, and tried each of them separately - not through Wubi this time. I didn't want to add any extra factors to the mix.

Ubuntu Studio told me it couldn't find my CD-ROM, which i found rather odd, given that i was installing it with a disc. I didn't spend too much time on that one, but at that point i was already well into hour seven of this process. Moved onto Ubuntu 9.04 - and got a completely different error message this time:[INDENT]Your BIOS does not provide ACPI_PSS objects in a way that Linux understands.
[/INDENT]I googled it, found a bunch of things telling me i needed to flash my BIOS (including trying to downgrade it, eep!), and i was just DONE. Stick a fork in me, done.

So, for all of you wonderfully helpful linux geeks who want to help a girl get started on becoming a linux geek... from what i've told you, do you think it's even possible to get Ubuntu running on my computer? If so, how? Help!

---

### Post by MelDJ on 2010-03-01
i would try another distro.
just to make sure that linux can be run

---

### Post by gnometorule on 2010-03-01
If you're not married to doing a clean grub based install, you could give WUBI a try:

[http://wubi-installer.org/](http://wubi-installer.org/).

What that does is to simply install ubuntu under Vista using the Windows add/remove program facilities; so it's really easy. Using the ISO, I couldn't get Ubuntu to install on this (old) computer of mine either; WUBI went fine. It starts with a dual boot option as grub does, it's just not grub (not that I know grub as I could not cleanly install it). Other than having a different boot up, I believe the two systems are 100% compatible (the differences are under the hood, and likely not important for you).

---

