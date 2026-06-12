---
title: "Bluetooth on Gutsy: unable to reinstall bluez-apps and obex error in Bloetooth Applet"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by hengie on 2008-01-27
Hi!

I've been trying to get my Apple Wireless Keyboard working on Gutsy more than a week now, still no luck. I've tried various approaches to fix the problem, until i removed all the bluez-* packages (to reinstall them later). 

Before i removed those apps,  Bluetooth Applet recoqnized the keyboard, but gave the* "obex://[xxxx]" is not a valid location.* error. Installing gnome-vfs-obexftp only changed the error to *Couldn't display "obex://[xxx]". Check if the service is available.* I also tried to connect the device from the command line with hcid, but that only gave me a timeout error. 

And now i'm encountering another problem when trying to apt-get install bluez-utils:
```
The following packages have unmet dependencies:
  bluez-utils: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is to be installed
```
There might have been some updates in the meanwhile that cause this conflict but i have no idea how to solve it. 

I've read tons of how-to's and forum posts that have worked for many but not for me. I would like to find a way to install bluetooth-related software from the scratch so that none of my old configuration files or packages could affect this.

This is my first post, so i'm unsure what kind of extra information to post to get most effective feedback.

---

### Post by sjzasada on 2008-03-28
Hi,

I'm having exactly the same problems with an Apple bluetooth keyboard. Did you find a solution to this?

Thanks,

Stef.

---

### Post by hengie on 2008-05-27
Hi,

Still no luck. I think i'll try to get it working on another distro, since i have more time now. I was hoping that this bug would be fixed, but it seems it hasn't been.

I'll let you know, if that helps. And of course, if someone has any advice, PLEASE share it with me!

Cheers,
henGie

---

