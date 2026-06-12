---
title: "Recognising USB device in VirtualBox"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by OllieGab on 2009-09-01
I've got VirtualBox running on my Ubuntu 9.04, XP running in the VirtualBox and most things working okey. I've got the version which makes it possible to enable and disable the the USB...and still it just doesn't recognise any USB device I connect!
Why? I installed VB in order not to have to reboot in XP the few times I actually need Windows...and I don't feel very confident with writing "loads of stuff" on the command line. The odd command, yes, but some help pages I have seen contain enormous amount of extra tweaking and configurating.
It shouldn't really be that complicated, should it?

Thankful for any advice...preferably "simple" ones!

Cheers Ollie

---

### Post by earthpigg on 2009-09-01
are you using VirtualBox OSE (open source edition), or the more fully-featured proprietary version from virtualbox.org?

have you installed guest additions?

---

### Post by pedro3005 on 2009-09-01
> 
I've got the version which makes it possible to enable and disable the the USB

Probably means he's got the full version.

---

### Post by moster on 2009-09-01
Earthpigg correct me if I am wrong but he must put checkbox in here to his USBs start working. Of course, in case you installed official VirtualBox. Not Virtualbox OSE who even do not have USB support.

menu system/administration/users and groups -> unlock. Then select your username and click properties. Then click to tab "user privileges" and put check in checbox "Use virtualBox"

That is all :D

---

### Post by OllieGab on 2009-09-01
Yes, I've got the "full" version. I tried first with the OSE but that greyed out the USB function/configuration ability.

Yes, I have also got the guest additions.

---

### Post by OllieGab on 2009-09-01
That is also done!

---

### Post by moster on 2009-09-01
Then you must restart computer :) It must work if you have additions installed and put checkbox where I tell you.

---

### Post by OllieGab on 2009-09-01
I seem to have got something now...though I haven't changed any settings as they already were OK.
I connected a camera, which came up in the directory tree (XP's) with its name. A USB stick came up under Entire Network, Virtual Shared Folders, VBOXSVR\media....does that make sense?

---

### Post by earthpigg on 2009-09-01
> **OllieGab said:**
> I seem to have got something now...though I haven't changed any settings as they already were OK.
I connected a camera, which came up in the directory tree (XP's) with its name. A USB stick came up under Entire Network, Virtual Shared Folders, VBOXSVR\media....does that make sense?

yeah, its possible restarting your computer (or virtual computer) fixed things up.

vbox requires kernel modules for both the host and guest... kernel modules normally are only loaded when the computer starts.

---

