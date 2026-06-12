---
title: "ltsp - black screen after login"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by yemu on 2008-02-12
hi,
i have a problem on my ltsp server running gutsy. 
sometimes after logging in i get only black screen with a cursor, no background, no wallpaper, no gnome-panel.
also sometimes thin-clients just freeze :-(
y

---

### Post by vuul on 2008-03-27
I had this same problem. It turned out to be an xserver issue.
I was able to diagnose my client's xserver issue with LTSP by doing the following:

On the LTSP server machine:
```
sudo chroot /opt/ltsp/i386
```

Give your root of your clients a password with:
```
passwd
```

You have to then rebuild the LTSP image with:
```
sudo ltsp-update-image
```

(wait for image to build...)

Then restart your client

Now when you reach the blinking cursor, use CRLT+ALT+F1 to get a terminal login prompt. Then login as root with your new password

Then navigate to /var/log
```
cd /var/log
```

Then view your xorg logfile:
```
less Xorg.6.log
```

I hope you will find the fault in the last lines of this logfile.

My specific error was because my thin client had a widescreen display and Xorg couldn't find an acceptable resolution.

I switched to a non-widescreen display and the client booted properly.

However, the no-resolution for the widescreen could probably be resolved with some xorg.conf tweaking...

---

