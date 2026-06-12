---
title: "How to set up fstab for usb disk ACLs"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by Ralph L on 2010-04-13
I want to use Access Control Lists (ACLs) on a removable usb hard drive.  I don't know how to set up /etc/fstab for usb drives.  Every time I try to make an fstab entry for the usb drive I get an error, when I plug in the usb drive and the system tries to automatically mount it.  The drive isn't mounted.  If I delete the fstab entry for the usb drive, the drive automatically mounts with no problem.  However, ACLs are not enabled, because no fstab entry exists to enable ACLs.  

The error message states that "only root can mount the drive".  However, as far as I can tell, automatic usb mounting is being done by root.  When I plug in the drive (with no fstab entry) and it automatically mounts, Nautilus Properties shows the drive is owned by root and has permissions of rwxr-xrwx.

Any help is much appreciated.  Note:  I am running Karmic on a Dell Latitude D610 laptop.

Ralph

---

### Post by Doctor Mike on 2010-04-14
> **Ralph L said:**
> I want to use Access Control Lists (ACLs) on a removable usb hard drive.  I don't know how to set up /etc/fstab for usb drives.  Every time I try to make an fstab entry for the usb drive I get an error, when I plug in the usb drive and the system tries to automatically mount it.  The drive isn't mounted.  If I delete the fstab entry for the usb drive, the drive automatically mounts with no problem.  However, ACLs are not enabled, because no fstab entry exists to enable ACLs.  

The error message states that "only root can mount the drive".  However, as far as I can tell, automatic usb mounting is being done by root.  When I plug in the drive (with no fstab entry) and it automatically mounts, Nautilus Properties shows the drive is owned by root and has permissions of rwxr-xrwx.

Any help is much appreciated.  Note:  I am running Karmic on a Dell Latitude D610 laptop.

RalphAre you editing the fstab file using sudo?

---

### Post by Ralph L on 2010-04-15
Dr. Mike

Yes I am using sudo to edit fstab.  The changes get into fstab ok.  The problem is that fstab is not used during USB mounting.  And I don't know what is.  I have been searching high and low on the Internet and haven't found anything describing how to automount usb drives with the ACL parameter set.  I am sure that somebody must be using usb removable drives with ACLs, but I haven't found it.  I think the title of this thread is somewhat misleading, but I posted it when I thought the problem was with fstab.

Thank you for responding.  Any help appreciated.

Ralph

---

### Post by Ralph L on 2010-05-06
For anybody who may be interested in resolution of this problem see [http://ubuntuforums.org/showthread.php?t=1451667](http://ubuntuforums.org/showthread.php?t=1451667)

Ralph

---

