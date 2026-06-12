---
title: "DWL-650 not working (anymore)"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by NarsilAnduril on 2007-02-14
Hi folks,

I'm sticky on a stupid thing ...

On my laptop (Compaq IVO N160) under Edgy, my WIFI card DWL-650 used to work perfectly until the latest update from today feb 14th (i don't look what's to update anymore - i know it's bad - so i can't say what). The update needed a reboot.

Since the reboot, no more WIFI ! Caramba, i'm bad ...

i can see the device in the "device manager" and the card's LED is blinkling, but nothing in the network tools (no eth0 shown).

Any suggestion ?

Thanks

Diego

---

### Post by sumgi on 2007-02-14
Have you tried to disable and enable your wireless connection? Or disable it and then restart ubuntu and when it comes back up restart it.

---

### Post by NarsilAnduril on 2007-02-15
What do you mean by disabling / enabling ? In the network manager ?

If yes, the wireless connection is not listed there anymore, that's my problem !

Diego

---

### Post by gradedcheese on 2007-02-15
the new kernel breaks ndiswrapper as I understand it.  You can reboot with the older kernel and see if that helps, select the second-to-latest kernel listed from the grub menu.

---

### Post by NarsilAnduril on 2007-02-15
I'll try this. I reach the GRUB menu pressing ESC during boot, right ?

If it works, what's next ? Keeping old kernel as default wouldn't be secure ?

---

### Post by gradedcheese on 2007-02-15
yes, ESC at boot.  The old kernel will be fine, I don't think there were any security issues resolved in the update, there's nothing wrong with using that kernel until the driver issue is resolved.  You can set the default kernel by editing /boot/grub/menu.lst (let me know if you need help with that)

---

### Post by NarsilAnduril on 2007-02-15
Thanks, i'll try this this evening : i'm at work right now, on my win machine :((

Diego

---

### Post by NarsilAnduril on 2007-02-15
Thanks gradedcheese, it's solved.

I've set default to "2" in menu.lst (kernel 2.6.17-10-386) and everything's back.

So,  kernel 2.6.17-11-386 is messing with ndiswrapper ? Should i post that somewhere ?

Diego

---

### Post by wej1971 on 2007-02-15
Ah, that explains my network dying *just* after I got it working ;)

Bugger!

---

### Post by gradedcheese on 2007-02-16
> **NarsilAnduril said:**
> Thanks gradedcheese, it's solved.

I've set default to "2" in menu.lst (kernel 2.6.17-10-386) and everything's back.

So,  kernel 2.6.17-11-386 is messing with ndiswrapper ? Should i post that somewhere ?

Diego

good job!  Yeah, it's a known problem but I don't think enough people know about it.  I saw a lot of questions about it right when the update happened.  ndiswrapper is a very unsupported hack, so you should **not** expect it to smoothly survive kernel upgrades.  You might want to see if there's an official thread explaining this, but if not I would post and tell people about it, maybe tell them how to use grub to try their older kernel.

---

