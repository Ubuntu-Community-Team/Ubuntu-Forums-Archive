---
title: "how to delete grub entries?"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by CmdGabriel on 2011-08-20
Hi,
after several system updates I have lots of  "old" grub entries to boot. How can I delete some of this entries?
I tried startup-manager. But i can use it only to select the default grub entry.
regards
gabriel

---

### Post by papibe on 2011-08-20
There are brave people who can go into the deepest hardcore files of grub and do almost anything.

For the rest of us the easy way: remove packages on synaptic. Check this useful [article]("http://www.omgubuntu.co.uk/2011/07/kernel-entries-gone/").

Regards.

---

### Post by -kg- on 2011-08-20
Yes, you can delve into GRUB and remove the entries, but that does little good for hard drive space.  Even though you remove those entries in your GRUB menu, the old kernels remain and take up hard drive space.

I don't know about what the video in papibe's link says (didn't watch it), but what I do is either reboot the computer and freeze it at the menu.  I then copy down the kernel number of every older kernel (except the newest two...I like leaving at least one working older kernel just in case), OR...

Launch Nautilus and navigate to "File System/boot" where you can find the same numbers.  Copy the oldest ones down, and then launch Synaptic.  It might be easier to copy them down at boot time, though, since they're listed from newest to oldest...just copy down the ones lowest on the list.

Once in Synaptic, enter the numbers one by one, then uninstall the associated kernel images, etc.  Once you have all those files uninstalled, you'll need to launch a terminal and run "sudo update-grub"  This will update your GRUB menu, and all those older kernels will not only be gone from your GRUB menu, but off of your hard drive, as well.

---

### Post by papibe on 2011-08-20
> **-kg- said:**
> (didn't watch it)
It is basically that in a 2min video.

Well, actually there are a few improvements:
[LIST]
[*]It is not necessary to stop at GRUB.
[*]In order to get the actual kernel you use 'uname -r'
[*]You can sort packages on synaptic by name, making it very easy to delete the old ones, and keep, let's say, the last two.
[*]The host is very nice ;)
[/LIST]
Kind Regards :P

---

