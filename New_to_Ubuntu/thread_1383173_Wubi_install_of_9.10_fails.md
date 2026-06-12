---
title: "Wubi install of 9.10 fails"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by LokiP on 2010-01-16
Installed wubi November 2009, it worked.
Updates last Thursday (Jan 2010) broke it.
Uninstalled wubi.
Installed wubi, still broken! Same error.
"Cannot find GRLDR."

Setup: HP 5101 netbook, 80Gb SDD, one partition, unencrypted, no CD drive. I installed Wubi from the internet within Windows. I don't have an ISO file.

What's changed since last November which now breaks it? Can I point the wubi installer at an old version from November to avoid whatever updates broke things?

Help me Wubi-ones, you're my only hope.

---

### Post by warfacegod on 2010-01-16
This may or may not help. It helped allot of others fix their fragged Wubi installs, of course that was before they uninstalled.

[http://ubuntuforums.org/showpost.php?p=8639887&postcount=14]("http://ubuntuforums.org/showpost.php?p=8639887&postcount=14")

---

### Post by LokiP on 2010-01-17
Hi, thanks for the link. Unfortunately, it still doesn't work, even after installing the modified wubildr file over c:\wubildr

The error is still this:

Try (hd0,0): NTFS5: 2
Try (hd0,1): invalid or null
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null
Cannot find GRLDR.

Press space to hold this screen, any other key to use previous MBR.

I'm just wondering what the actual bug is? Because it used to work. I'm guessing that GRUB was changed during the update. But now I'm wondering why it was changed. If so, might a solution be if someone with old working wubildr* files who has not yet updated to the new GRUB could post them as attachments?

I think what you're saying is there's a known problem which will prevent clean installs, and if only I had my old installation, the new patched wubildr might work...? If so, I do have a backup of the old root.disk, I'll try substituting that in and see (with the patched wubildr). Otherwise, anyone have those old wubildr files anywhere? I basically wouldn't mind going back to whatever I had installed last Novemeber.

If only there was some kind of "version control" when updating GRUB, so all your old boot files would still be there as a safety measure in case something breaks as a result of the update...

---

### Post by warfacegod on 2010-01-17
Any particular reason you don't use a dual boot? Far fewer issues that way.

---

### Post by LokiP on 2010-01-17
So, I shouldn't use Wubi? I don't know how to resize the Windows partition safely to create a new partition for Ubuntu. I don't have a CD drive, either, which complicates installations. Wubi was handy for the "try before you fully install" option it offered.

Anyway, I tried the old root.disk, but no luck.

I should actually explain the full problem, since there was an intermediate step that may be significant.

First, I installed Wubi last November. It worked. gobi-loader didn't, but I got it to work by copying some firmware from the Windows host.

Last Thursday, an automatic Ubuntu software update process killed GRUB.

It was dumping me into a GRUB shell whenever I tried to boot into Ubuntu. SoI booted into Windows to research the problem online, and also made a backup of root.disk for good measure. I could work around this, using instructions here: [http://www.omaregan.com/?p=583](http://www.omaregan.com/?p=583)

Strangely, I had to boot kernel version 2.6.31-16-generic, not 2.6.31-17-generic (which would just reboot the computer instead of actually booting into Ubuntu). So I figured something might be wrong with the version -17 kernel.

So, after backing stuff up to the Windows host, I used Synaptic to reinstall grub-pc and kernel version 2.6.31-17-generic.

After rebooting, I now had a "GRLDR not found" problem. I can't tell if this error message is informing me of a missing file within Windows, or a missing file within the root.disk. I experimented with reverting to the backup of the old root.disk, but no luck, same "cannot find GRLDR" problem. So I assumed it was something missing within Windows, not on the root.disk. (Anyone enlighten me on this?)

Then I uninstalled Wubi.

Then I reinstalled Wubi.

The GRLDR problem remains.

I'm left with two possibilities:

One possibility is that uninstalling Wubi doesn't cleanly uninstall. I.e. something got screwed up within Windows, and stayed screwed up despite the uninstall. I know uninstalling Wubi doesn't remove the boot option from boot.ini, so there's at least on piece of cruft left after the uninstall. What else might be lying around stuffing things up for the reinstall? What files/other bits of Windows does Wubi actually touch?

Another possibility is that the upstream Wubi distribution is currently broken. This would imply that the grub shell bug was an intermediate form of the full bug, that I was lucky enough to get stuck in (until I "fixed" it by reinstalling grub-pc and kernel -17 from Synaptic). The grub shell bug was preferable to the "missing GRLDR" bug because I could at least boot into Ubuntu from the grub shell (even if it did require typing four lines). A solution here is to revert to an older form of Wubi. (But how to revert?)

If it's something screwed up within the Ubuntu file system, then I can't understand why the old root.disk won't work. It's a complete copy of the EXT2 file system after the GRUB shell bug exhibited itself but before the GRLDR bug exhibited itself. I've confirmed that replacing the root.disk produced by the reinstalled Wubi with this old copy of root.disk still exhibits the second bug, "missing GRLDR". This implies to me that something is different in the Windows side of things (otherwise it would have reverted to the grub shell bug).

Maybe something else is happening, like the root.disk is fragmented and I need to defrag the Windows drive, but if that's the case then why does the Wubi FAQ say you can backup root.disk by copying the file?

Confused and disheartened.

---

### Post by warfacegod on 2010-01-17
When ubuntu release their last set of updates it did this to allot of wubi installs. So its really ubuntu's fault not wubi's or Windows (for once). Your earlier kernel working doesn't surprise me, it didn't have the updates applied to it. Ubuntu behaved as though you had never updated at all.

If there is no specific need to use a Wubi install, then I suggest creating a dual boot. I assume you are on Windows 7 if so it comes shipped with the ability to resize its own partition.

If you decide to create a dual boot there is a good chance that Windows won't like it. This is the simplest way I can find to fix that.

[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by LokiP on 2010-01-18
Hi, thanks for the suggestion. I'll try it if I can.
Unfortunately, it's not Win7, it's XP SP3. So I'm not sure how to resize that partition, but I'll investigate.
Also unfortunately, that tutorial assumes I have a CD drive...

---

### Post by warfacegod on 2010-01-18
Window XP usually doesn't mind being resized by Gparted or by the Ubuntu installer. I've done it several times with no issues. That doesn't mean something won't go wrong so use caution.

If you don't have CD drive, how did you get Linux onto your machine?

---

### Post by LokiP on 2010-01-19
Wubi, via the network, is how I got Linux onto the machine. That was a major reason for using Wubi. No partitioning, low risk. And XP was on the machine when I bought it.

---

