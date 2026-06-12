---
title: "Ubuntu Server able to Boot from USB stick?"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by vitae_drinker on 2009-08-26
Hey, I've been following Ubuntu for quite a while, and recently converted my old laptop to Jaunty after it continually acted up under Win XP and was getting to the point of being unusable. My (new) desktop is still Win Vista 64 (mainly for gaming). Both are wirelessly connected to my router.

What I want to do is build a (headless, I believe the term is) file server (mostly music and PDFs for use in tabletop RPG/Mini gaming) using an all-in-one mini-ITX mobo and case using a 1 TB drive, DVD burner, and an ethernet connection to my router but booting Ubuntu Server from a USB stick.

The reason I want to do it this way is so that I can keep the (limited) SATA connections for future HD expansion. Plus, as an option in the future, possibly take this box and turn it into a Nettop, and keep the Server set up on the USB and just transfer it to another box with a minimum of fuss.

Is it possible to get a relatively small (2 gb - 4 gb) USB stick to install Jaunty Server on to, and use that as the boot drive, leaving the HD as storage only? IE: Similar to the Live USB?

I'll probably keep the USB Stick on the inside of the case as well (to help protect it).

Is it possible? Will it work? Will it consistently boot if I have to reboot the server without outside intervention (IE: hooking up a monitor/keyboard)? Will it read the USB stick as just a HD at install, or do I have to do something special? I know (if it is possible to us the stick as the boot drive do) that I would have to set the BIOS to boot USB primary.

Would it be better to use just a Live USB of Desktop Ubuntu?

Will I be able to install Samba & SSH to it? What about Mediatomb if I want to do media sharing?

I searched on the forums and found a few threads that made it seem possible, but wanted to know if someone had successfully done so.

Thanks in advance for your help!

(If this is not the appropriate forum, please don't hesitate to move it elsewhere!)

---

### Post by DGortze380 on 2009-08-26
Possible ... but

Booting from a USB Stick has nothing to do with Ubuntu. It's only possible if your motherboard supports booting USB. 

You *may* be able to create a bootable CD that will subsequently boot the USB. I tried this once, but didn't end up needing it and never tested it.

---

### Post by vitae_drinker on 2009-08-26
> **DGortze380 said:**
> Possible ... but

Booting from a USB Stick has nothing to do with Ubuntu. It's only possible if your motherboard supports booting USB. 

You *may* be able to create a bootable CD that will subsequently boot the USB. I tried this once, but didn't end up needing it and never tested it.


Roger that, I understand the Mobo needs to be able to boot from the USB. So let us assume that is a given.

Can you boot Ubuntu Server edition from a USB stick?

---

### Post by DGortze380 on 2009-08-26
> **vitae_drinker said:**
> Roger that, I understand the Mobo needs to be able to boot from the USB. So let us assume that is a given.

Can you boot Ubuntu Server edition from a USB stick?

I just said... booting has nothing to do with Ubuntu.

Install it on the stick. If the mobo supports it, it will boot. If not it won't...

---

### Post by marshmallow1304 on 2009-08-26
[https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html)
is extremely helpful for setting up a server.

---

### Post by vitae_drinker on 2009-08-26
> **DGortze380 said:**
> I just said... booting has nothing to do with Ubuntu.

Install it on the stick. If the mobo supports it, it will boot. If not it won't...

So the short answers to some of my questions are "Yes, you can install the server edition to a USB stick" and "Yes, you can boot from it."

Now, do have to do anything different to do so? If so, what?

---

### Post by bodhi.zazen on 2009-08-26
As has been indicated on this thread, assuming your BIOS supports booting from a USB, there is nothing you need to do that is any different from installing on a USB then a Hard drive, server or desktop. The installation is the same.

I suggest you go ahead and install and post if you have problems rather then asking if it possible =)

---

### Post by vitae_drinker on 2009-08-26
> **bodhi.zazen said:**
> As has been indicated on this thread, assuming your BIOS supports booting from a USB, there is nothing you need to do that is any different from installing on a USB then a Hard drive, server or desktop. The installation is the same.

I suggest you go ahead and install and post if you have problems rather then asking if it possible =)

Hehe. Good point. Once I get the parts to build the server (it should be by Friday), I will do just that and come back with any issues I had.

Thanks for everyone's quick help! :guitar:

---

