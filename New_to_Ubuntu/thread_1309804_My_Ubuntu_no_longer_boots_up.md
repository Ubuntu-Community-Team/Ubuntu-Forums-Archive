---
title: "My Ubuntu no longer boots up"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Whitewind6177 on 2009-11-01
Hey, I just started using Ubuntu today, and I was trying to get a feel for it when something went horribly wrong. What I did while on today was get my nVidia driver working right, and activated the desktop effects. Then I installed some programs, VLC media player, DC++, KTorrent(it's possible I restarted before allowing this one to finish downloading). 

After installing VLC player, I looked in my harddrive where Windows is installed on my computer and pulled a .avi file out of it to test VLC, and it worked fine. it mounted the filesystem in the process, this may have caused the error, I don't know really.

What caused me to restart before my downloads were finished was the firefox kept telling me to restart firefox, constantly.  did so repeatedly, and the message kept popping up at the top anyway every couple of seconds. I eventually just restarted my machine to see if that would help. After restarting, I found that Ubuntu no longer boots up. After going to Grub and selecting it, it will say that it failed to load the filesystem, and a command prompt will come up. Is there any way to fix this? I'd post a picture of the error if you want, but I don't really know how, so you may have to walk me through that part.

Also, I just thought I'd also point out that Windows works completely fine, no problems at all.

---

### Post by happyhamster on 2009-11-01
I'm not sure if I can be of any help, but could you try booting into ubuntu, write down the error message you get (as much as possible), and show it here?

---

### Post by cariboo on 2009-11-01
You probably have some corrupted files on your hard drive. Boot from the Live CD, once at the desktop open an Applications-->Accessories-->Terminal and type:

```
sudo fsck -a /dev/sda1
```

Substitute you linux partition for the one in the above command. Once done reboot, and things will almost be back to normal. You may be asked to run dpkg --reconfigure -a when you try to continue installing the interrupted packages.

---

### Post by Whitewind6177 on 2009-11-01
The above suggestion didn't work, nothing changed about the error message. But taking a closer look at it, I saw this.

/dev/sda3: UNEXPECTED INCONSISTENCY; run fsck MANUALLY
(i.e. without -a or -p)

Thats what it said near the beginning. Does this clear anything up?

---

### Post by happyhamster on 2009-11-01
> **Whitewind6177 said:**
> The above suggestion didn't work, nothing changed about the error message. But taking a closer look at it, I saw this.

/dev/sda3: UNEXPECTED INCONSISTENCY; run fsck MANUALLY
(i.e. without -a or -p)

Thats what it said near the beginning. Does this clear anything up?

- It means you have to follow cariboo907's method, but run:

sudo fsck /dev/sda3

Good luck.

---

### Post by Whitewind6177 on 2009-11-01
> **happyhamster said:**
> - It means you have to follow cariboo907's method, but run:

sudo fsck /dev/sda3

Good luck.

Yeah that's what I figured it meant, but I was just wanting to make sure. I'm gonna try running that in a minute, and I'll tell you how it goes.

---

