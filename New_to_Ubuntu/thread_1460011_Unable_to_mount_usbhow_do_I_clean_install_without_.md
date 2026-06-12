---
title: "Unable to mount usb/how do I clean install without Live CD/USB"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by Mr_Moggy on 2010-04-22
Hi there

Complete newbie to Ubuntu here, so please be gentle :)

I have a bit of a serious problem; On 9.10 (Netbook remix version), I installed "libimobiledevice0" through synaptic (in a attempt to get gtkpod to recognise my ipod touch). The installation caused one major hitch: Not only did it delete rhythmbox from my system, it has also apparently removed the ability for me to mount, and even recognise my USB flash drives/devices (the disk utility says they are "unknown or unused"). They do appear however in my list of drives when doing a check with fdisk.

(sidenote: did a search for "USB" in synaptic and all the major mounting packages seem to be in order)

This has of course put me in a bit of predicament as I am unable to create a start-up disk, and with no alt. computer to make one I am at a loss as to what to do.

Is there a way to do a clean reinstall of ubuntu without a install disk/usb stick? Or a more direct solution?

Cheers :)

---

### Post by phidia on 2010-04-22
If you want to do a reinstall on your netbook ( it does seem that provided your bios allows it that you could still start up from a usb drive-you just have to change the boot order in bios & have usb drives before the HD )
But if for some reason that doesn't work you can do a network install see the network install section of the community docs [here]("https://help.ubuntu.com/community/Installation").

---

### Post by Paddy Landau on 2010-04-22
A couple of perhaps silly questions:

[LIST]
[*]Have you tried mounting your USB disk manually? What is the exact error message that you get?
[/LIST]

[LIST]
[*]Would it help to uninstall (via Synaptic) libimobiledevice0?
[/LIST]

---

### Post by phidia on 2010-04-22
Deleted-mispost sorry

---

### Post by Mr_Moggy on 2010-04-23
Thanks all for your help! It seemed that uninstalling the offending package did the trick :)

---

### Post by Paddy Landau on 2010-04-23
> **Mr_Moggy said:**
> It seemed that uninstalling the offending package did the trick
Excellent. Please mark the thread as Solved.

---

