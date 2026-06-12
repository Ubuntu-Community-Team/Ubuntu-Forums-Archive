---
title: "Installing/Root"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by psychtor on 2009-01-09
After trying many times to get Ubuntu 7.04 to install (only copy I have) it finally installed last night after I removed the  NVIDIA MMX440 video card. The monitor was still plugged into the card at install so should have been in the mobo port.

I did not write all the text down except:

First I was told to run FSCK so I did.

My username/desktop is listed but there is no root. When i installed I used "guided use the whole disk" and just let it go.

Can I create the "root" after install? If so, how? If not, where can I copy instructions to do it on reinstall?

Also, it's not safer not have a username/password for "root" right? I think that advice was on the screen when I installed.

Which file names has all those instructions anyway?

I would also like to find a way to stop the motherboard from reserving 128 MB RAM out of the 512 that I have. There is no option to alter that in the CMOS or the BIOS That option shows an unchangeable 64 MB RAM (probably for the onboard Intel video)but every time I remove or disable that from the device mansger in Windows it just insists on doing it again at reboot even though I use the video card.

So I guess that's it for now.

---

### Post by taurus on 2009-01-09
The root account is locked as a default.  If you need to have root privilege, use sudo/gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by psychtor on 2009-01-09
> **taurus said:**
> The root account is locked as a default.  If you need to have root privilege, use sudo/gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

So using the whole disk and no root superuser account is satisfactory? In other words I didn't mess it up and everything is fine?

---

### Post by Captain_tux on 2009-01-09
Yes, that's correct... the **sudo** (administrator) password is the password of the user you created during installation.

Nice, isn't it?! Welcome and enjoy the finest operating system known to man!

---

### Post by ugm6hr on 2009-01-09
I know you say you only have 7.04, but I would strongly advise downloading a current version: 8.04.1 is a good choice (or 8.10).

7.04 is not supported, so is a security risk (potentially).

---

### Post by psychtor on 2009-01-09
> **Captain_tux said:**
> Yes, that's correct... the **sudo** (administrator) password is the password of the user you created during installation.

Nice, isn't it?! Welcome and enjoy the finest operating system known to man!


Ok, great.Thanks.  Now I'm gonna try to get that thing online but first I gotta get some info on iptables since I certainly don't want to get hacked.

---

### Post by psychtor on 2009-01-09
Can I upgrade that to 8.04 without much of a problem or do I just install 8.04 over top of the old?

---

### Post by ugm6hr on 2009-01-09
> **psychtor said:**
> Can I upgrade that to 8.04 without much of a problem or do I just install 8.04 over top of the old?

I'd go with the latter. Upgrading will take more bandwidth, and be difficult, since 7.04 repositories are now hidden.

---

