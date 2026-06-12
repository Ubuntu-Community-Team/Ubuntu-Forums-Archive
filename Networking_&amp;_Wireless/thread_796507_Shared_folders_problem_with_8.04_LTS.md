---
title: "Shared folders problem with 8.04 LTS"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by calif99x on 2008-05-16
Hi:

I upgraded to 8.04 from 7.10 and am not happy with the way shared folders are working, or actually not working.

I have several folders for picture and video sharing to a Windows box, and find that the options for creating the shared folder have changed from 7.10.  In addition, I have finding that even when I create the shared folder, I get errors from Windows that the folder is not accessible.

I have 5 shared folders, and 4 of them give the error.  The disk formats are ntfs for 2 drives and ext for the other 2 drives.

This is really starting to annoy me, any help or guidance on getting things working again would be appreciated.

---

### Post by closeyourwindows on 2008-05-16
did you upgrade from an earlier version or is this a fresh install?

---

### Post by calif99x on 2008-05-16
Hi:

I was on 7.10; which was an update from 7.04.  The installation  was stable for quite some time.  Then a set of patches that get pushed through the update manager started the system in a reboot every few minutes.  I saw that the update manager (Synaptic) listed an upgrade to 8.04 and decided to accept the upgrade.

The options for shared folders under 8.04 have changed; 7.10 had options for a couple of different type of shares, that is not there any more.  The help pages are not helpful in understanding how things have changed and how to get things to work as they did under 7.10.

I have several drives and this system has a good size root partition, so I am hoping that a fresh install is not what I need.

Thanks

---

### Post by stoneybroke on 2008-06-24
Hi calif99x

I know that you asked this a while ago but here is what you need to do as shared-folders is NOT available from SYSTEM>ADMINISTRATION.

Go to File-System/usr/bin and double click on Shares-Admin and it will work ok.

---

