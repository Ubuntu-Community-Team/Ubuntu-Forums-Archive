---
title: "mobile broadband compatible with ubuntu?"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by swazi7sista on 2010-01-05
Hi all.  I'm a complete newbie so please give me all answers in layman's terms  :)

I have just received my new Inspiron 10v mini, with Ubuntu 8.04.  I'm in the UK and have no idea which mobile broadband providers, offering pay-as-you-go, are compatible with Ubuntu.  Any suggestions?

Many thanks in advance for your help.

---

### Post by cariboo on 2010-01-05
I'm not in the UK, but an ISP is an ISP, no matter how they deliver the signal. If you already have the phone, plug it in to your computer and check to see if it is detected. Open an Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n10
```

If it is detected, you show see some connection info and a driver being loaded. I haven't got my usb cable with me or I would show you what the output looks like. It should be more of a matter of coverage and price more than anything else when selecting a provider.

---

### Post by =not4prophet= on 2010-01-05
If you want to use mobile broadband with Ubuntu, I would recommend upgrading to a version newer than 8.04.  Starting with version 8.10, there were significant improvements to the handling of mobile broadband connections from within network-manager.

---

### Post by lemmy999 on 2010-01-05
I'm posting this from a hotel room in the UK using my EEEPC  900 running 9.10 using a Vodafone 3g SIM and USB dongle. Install is a cinch, data costs £15 a gig and does not expire (unless you don't log in within 270 days)I have been using the current data package (ie 15 quids worth)for  some months on and off!

Hope that answers all your questions.

---

### Post by DannStarr on 2010-01-05
Yep... Im posting this using ubuntu 9.10 connected via my mobile phone, using O2 PAYG sim. £15 a month gives me unlimited web (fair usage policy) and unlimited txts

---

