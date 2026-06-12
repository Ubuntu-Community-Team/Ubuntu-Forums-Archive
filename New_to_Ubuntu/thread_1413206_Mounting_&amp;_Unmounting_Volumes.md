---
title: "Mounting &amp; Unmounting Volumes"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by Linux BASHer on 2010-02-22
In the terminal I know I can mount a volume by using the mount command somewhat like this:

mount /media/disk

And likewise unmount using the umount command like this:

umount /media/disk

However, though unmounting appears successful, I notice in the GUI, the icon of the drive merely becomes grayed-out in Thunar. Clicking on the icon re-activates the mounts the volume. This is not what I have come to expect, nor the behavior I prefer. Funny thing is, it does this for encrypted volumes too, which concerns and puzzles me as I do not have Ubuntu save my password for security purposes.

So my questions are:

How do I definitively unmount a volume so that it no longer shows up in the GUI  and needs to be properly mounted anew if one wishes to work with it again?

And, is the process of mounting an encrypted volume any different from that of mounting a regular volume (with the exception of course, of needing to provide one's password)? Ubuntu usually auto-mounts so I've never had the opportunity to do so.

---

### Post by mikeyphi on 2010-02-22
AFAIK volumes are always detected by the OS, can be automounted or left for the user to mount. Mount/Unmount can be done via mouse right click. Different systems use different indicators to show when a volume is mounted.

---

### Post by Linux BASHer on 2010-02-22
> **mikeyphi said:**
> AFAIK volumes are always detected by the OS, can be automounted or left for the user to mount. Mount/Unmount can be done via mouse right click. Different systems use different indicators to show when a volume is mounted.

Accepted. However, how is it mounting an encrypted drive without asking me for my password? I hope it is not remembering my password, as I told it not to.

And my other question remains... Is there any difference in the process to mount an encrypted drive (via CLI)?

---

