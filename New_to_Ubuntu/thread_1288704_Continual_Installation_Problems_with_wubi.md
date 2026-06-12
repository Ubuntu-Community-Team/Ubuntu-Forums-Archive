---
title: "Continual Installation Problems with wubi"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-10-11
Until a few days ago, I had xubuntu 8.10 installed on my second laptop - an old Toshiba Satellite Pro 4600 - via wubi.

I hadn't used it for a few months, so when I fired it up obviously there were a number of updates needed. I think it was about 250, but after it did the first 30 or so, I got error messages and the update aborted.

So, there also being an option to upgrade to 9.04, I took that. But that didn't install properly either, and when it rebooted, it hung at a point of doing something with the swapfile(s).

It was all going horribly wrong, so I popped back to Windows 2000 and uninstalled xubuntu from the Control Panel.

Then, I downloaded a fresh .iso of xubuntu 9.04 and put it onto my USB stick, defragged my C drive, rebooted Windows and then ran the wubi I had extracted from the new .iso.

At the start, it went OK, but the install hung at the point it said it was creating the virtual partitions.

So, I cancelled the install, and rebooted. I was surprised to find a xubuntu option on the splash screen (as well as one for Windows 2000), so thinking it would just go nowhere, I selected it and was pleasantly surprised to see xubuntu seemingly loading as normal.

Then it went to various installation screens, but gave me the following error message:
> Some of the partitions you created are too small. Please make the following partitions at least this large (in bytes):
```
/ 1812730880
```
If you do not go back to the partitions and increase the size of these partitions, the installation may fail.
**_Go Back_ _Continue_**
If I press 'Go Back', it just goes back to the previous automated screen and returns exactly the same error message. If I press 'Continue', the installation just hangs. The problem is that the wubi installation is completely automatic - there is no option for me to influence the size of any partitions!

Does anyone here have any ideas as to what I should do next?

BTW, please don't tell me to install from CD, as the CD on the PC is broken and it's so old that the BIOS doesn't have an option to boot from USB.

---

### Post by mprince on 2009-10-11
> The problem is that the wubi installation is completely automatic - there is no option for me to influence the size of any partitions!

Are you sure about this? I thought wubi lets you choose the installation size you want on the installer?

---

### Post by Roger Allott on 2009-10-11
> **mprince said:**
> Are you sure about this? I thought wubi lets you choose the installation size you want on the installer?

At outset, it certainly gives you the options from a select list based upon the minimum being what it needs and the maximum being the amount of free disk space on the PC. For me, it was suggesting a total partition size of 10 Gb, but I elected to assign it 12 Gb.

I certainly didn't have any say in what size each of the partitions is to be (i.e. home, root & swap) - that decision is left to the installer.

---

### Post by Roger Allott on 2009-10-20
Does anyone else have any input to this, as I've still got the same problem.

The situation baffles me, to be honest, because I would have thought that 12Gb would be more than adequate for xubuntu 9.04. I'd need about 3Gb for root, 1Gb for swap, and the rest for home.

So why on earth would wubi allocate less space for the root partition than it knows (or damn well **should** know) it needs???

---

