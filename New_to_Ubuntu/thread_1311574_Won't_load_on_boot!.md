---
title: "Won't load on boot!"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by jezebel on 2009-11-02
Hi
I got a brand new netbook - Acer Asppire One D250 with Win7. I love my new netbook, and wanted to dual boot with Ubuntu. I found Netbook Remix, and installed via usb, alloting 45 gb for 'Ubuntu. 

I rebooted, Grub loaded great, but when I chose Ubuntu, it didn't load - I just got a black screen with a little flashing line, like an underscore.

So (yes, I'm an idiot) I tried to install again, alloting only 10 gigs, as a trial (so, I knew I'd have two Ubuntus, but I just wanted to see what would happen) The new 10gb instal worked great.

Then (Did I mention I was an idiot?) I used Acronis Disk D\irector in Win7 to delete the partition with the big Ubuntu. Of course, after that my pc wouldn't even boot because it couldn't find Grub.

So, I installed again using the same 45 give space, and grub now comes up, but still no Ubuntu exactly. I say Exactly because, when I run memtest, then escape after it's 29% done, I can get into Ubuntu.

What's going on? Anyone??

---

### Post by kansasnoob on 2009-11-02
Well grub 2 seems to be a bit buggy still.

While booted into Ubuntu run the command:

```
sudo update-grub
```

---

### Post by jezebel on 2009-11-02
Thanks Kansasnoob! I did what you suggested, and upon reboot, it seemed fine.. I'll reboot several more times over the next few hours as I customize my new toy and will report back any probs or no probs.

---

