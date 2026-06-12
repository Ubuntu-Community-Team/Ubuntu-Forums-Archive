---
title: "smb sharing &amp; android devices?"
date: 2014-03-13
forum: Networking &amp; Wireless
---

### Post by kurja on 2014-03-13
Does anyone know of a samba compatible server package for android that doesn't require rooting the android device? I'd like to share directories on the sd card in my android tablet to my ubuntu desktop computer, but as far as I can tell after reading around the web about this, samba wants to use ports that are not available unless root. Is there a straightforward solution to this..?

---

### Post by lukeiamyourfather on 2014-03-13
The server could be setup on the desktop machine and then connect to it from the Android device (FTP, SMB, whatever). Or just grab a USB cable and transfer what you need, that's probably the easiest.

---

### Post by SeijiSensei on 2014-03-13
It is not even possible to mount a remote NFS or Samba share onto an Android phone as a client without rooting the device, never mind having the device run a server of its own.

Using a USB cable is the obvious solution, but it only works well with versions of Ubuntu starting with 13.04.  Before that support for the now-required MTP protocol was poor.

Another option is to [transfer files via wifi]("https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransferpro&hl=en").  Follow the link in my signature to see more options for file transfers between Android and Ubuntu.

---

### Post by kurja on 2014-03-13
FTP works, transferring via sd card or usb cable works too, but setting up an smb server on the tablet would by far be the most convenient way... with ftp or usb I need to prepare the files on the pc then doodle with the tablet to transfer them, with smb I could just drag and drop the files and be done with it.

It's utterly infuriating that we have all this technology, and then the technology is intentionally restricted so we can't do some of the most obvious, fundamental things :evil:

Looking at rooting now... Unless anyone can point out a more convenient method?

---

### Post by kurja on 2014-03-13
> **SeijiSensei said:**
> It is not even possible to mount a remote NFS or Samba share onto an Android phone as a client without rooting the device, never mind having the device run a server of its own.

Using a USB cable is the obvious solution, but it only works well with versions of Ubuntu starting with 13.04.  Before that support for the now-required MTP protocol was poor.

Another option is to [transfer files via wifi]("https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransferpro&hl=en").  Follow the link in my signature to see more options for file transfers between Android and Ubuntu.

thanks, looking at that link now.

---

### Post by kurja on 2014-03-13
Tried AirDroid, the app seems to do what I want (well, almost), it's maybe a little "bloaty" solution for this but hey. I'll consider this solved for now, thanks all.

---

### Post by lukeiamyourfather on 2014-03-14
> **SeijiSensei said:**
> It is not even possible to mount a remote NFS or Samba share onto an Android phone as a client without rooting the device, never mind having the device run a server of its own.

Not true, there are dozens of apps in the Google Play Store for accessing SMB shares. I couldn't find any for NFS but there might be some out there (didn't look that hard).

---

### Post by kurja on 2014-03-15
> **lukeiamyourfather said:**
> Not true, there are dozens of apps in the Google Play Store for accessing SMB shares. I couldn't find any for NFS but there might be some out there (didn't look that hard).

That's right, I already had an smb client on the tablet and 'it just works' without rooting or anything. It's just the smb server that won't work without root access.

---

### Post by SeijiSensei on 2014-03-15
> **lukeiamyourfather said:**
> Not true, there are dozens of apps in the Google Play Store for accessing SMB shares. I couldn't find any for NFS but there might be some out there (didn't look that hard).

Of course there are applications that can access an SMB share like AndSMB.  That's not what I was referring to.  I'm talking about *mounting* the share into the Android file system the [way you can with CIFS]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") on Linux.  Without a rooted phone, you cannot mount a remote file system.  You can only use client software that can communicate with an SMB (or NFS) server, but not create a full-time mount

---

### Post by bab1 on 2014-03-15
> **SeijiSensei said:**
> Of course there are applications that can access an SMB share like AndSMB.  That's not what I was referring to.  I'm talking about *mounting* the share into the Android file system the [way you can with CIFS]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") on Linux.  Without a rooted phone, you cannot mount a remote file system.  You can only use client software that can communicate with an SMB (or NFS) server, but not create a full-time mount
Any client software that can access a CIFS share has to mount the shared directory to the local hosts file system.  Maybe it is better said that you can't mount the share via fstab unless the device is rooted.  So, an accessed share is a mounted share.  ;-)

---

### Post by SeijiSensei on 2014-03-16
The SMB clients I've used work more like an FTP client than anything else.  I may be wrong, but I don't think they mount anything into the file system.  They just stream bits.

---

### Post by lukeiamyourfather on 2014-03-17
> **SeijiSensei said:**
> The SMB clients I've used work more like an FTP client than anything else.  I may be wrong, but I don't think they mount anything into the file system.  They just stream bits.

It's semantics, but I get your point. The original poster was able to transfer their data and that's all I cared about. =d>

---

### Post by kurja on 2014-03-22
> **SeijiSensei said:**
> It is not even possible to mount a remote NFS or Samba share onto an Android phone as a client without rooting the device, never mind having the device run a server of its own.

Using a USB cable is the obvious solution, but it only works well with versions of Ubuntu starting with 13.04.  Before that support for the now-required MTP protocol was poor.

Another option is to [transfer files via wifi]("https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransferpro&hl=en").  Follow the link in my signature to see more options for file transfers between Android and Ubuntu.

Update on this:

I tried an app called "SSHDroid", and it is able to set up ssh server on my tablet with no root access; so now I can see the tablet's memory and sdcard right in my desktop's nautilus over wlan, and transfer files to and fro in a convenient manner. So much goodness! =D
[ATTACH=CONFIG]251380[/ATTACH]
As far as I can tell, it's now mounted - and the nautilus bookmark takes me right to where I want. Works! Happy! =D

---

