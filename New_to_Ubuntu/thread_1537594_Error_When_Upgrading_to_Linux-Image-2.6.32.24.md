---
title: "Error When Upgrading to Linux-Image-2.6.32.24"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by Excedio on 2010-07-23
Hey guys...getting this error when upgrading to the latest linux kernel available to me. Same thing happened with linux-image-2.6.32-23-generic & linux-image-2.6.32-22-generic. My computer is running normal, but these are getting annoying. Can someone provide me a little guidance please?

[QUOTE=Update Manager]E: linux-image-2.6.32-24-generic: subprocess installed post-installation script returned error exit status 2
E: grub-pc: subprocess installed post-installation script returned error exit status 2[/QUOTE]

---

### Post by Excedio on 2010-07-23
Ok guys. Having a bit more of an issue than I was expecting. I restarted and now i'm getting this error:
 
```

error: file not found
error: you need to load the kernel first
 
     Failed to boot both default and fallback entries.
 
Press any key to continue...

```
 
Pressing any key does nothing but repeat the message.

---

### Post by Excedio on 2010-07-23
Well...I've gotten past this point by using [this post]("http://ubuntuforums.org/showpost.php?p=9487046&postcount=22") in another thread. I get to the ubuntu splash screen and then get a blank screen with a flashing underscore.
 
When I reboot and press Esc during the splash screen I get this:
```
(process:227): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
                                              fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 218008/3514368 files, 2126657/14041344 blocks (check after next mount)
```
 
 
EDIT: I got to this point by removing Linux-Image-2.6.32.24 and installing back to Linux-Image-2.6.32.22. This was the image I had before.

---

### Post by overdrank on 2010-07-24
Moved to Absolute Beginner Talk

---

### Post by Excedio on 2010-07-24
Is it possible that this is happening if I used the wrong image? By "wrong image" I mean 32bit vs 64bit.
 
Lappy is 32bit.

---

### Post by munky99999 on 2010-07-24
I got some probs from today's patch.

My particular error is error 13: invalid executable format

---

### Post by Excedio on 2010-07-25
Bump

---

