---
title: "Wubi messed up MBR?"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by Cephiro on 2010-03-24
Hello there. I'm sorry that my first post here is a plea for help, but I'm an absolute beginner and the solutions I found out on the internet don't apply exactly to my case.

Here's the thing. I'm a long time Windows user, but I thought I'd give Linux a (serious) try this time. As I don't know if I'll be able to use it full time, I thought that installing it through Wubi in my Windows 7 partition would be the most hassle-free way to go.

So I installed it through Wubi, it booted fine and dandy. Before I started messing with specifics configs for my PC I thought I'd let Ubuntu update itself, in order to ensure compatibility with my hardware. It updated everything, and asked me to reboot.

After I rebooted... it couldn't boot into Ubuntu anymore. The Win 7 boot works ok, but any attempt to boot into Ubuntu drops me into GRUB4DOS.

I've checked some solutions for fixing the MBR, but it seems that it is ok. The MBR points the boot to /ubuntu/winboot/wubildr, and there are copies (?) of the files in here also in the root of the system. (C:)

Is it a known bug, or should I assume I did something stupid that I should not? Is there a way to fix this, or should I start over?

Thank you very much for the attention.:p

---

### Post by ubu newb on 2010-03-24
Same exact thing happened to me.  I tried fixes from live cd and I then lost the ability to boot into windows 7.   Wish I would have seen this link before installing into its own partition.  Not sure if it works.  [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Let me know it it works.  If not then boot into windows and un-install and either re-install wubi or its it own partition.

Good luck

---

### Post by Cephiro on 2010-03-24
Wow thanks, that worked as a charm. :D

This should be made more public, I guess lots of people would have this problem...;)

---

### Post by undecim on 2010-03-24
Yeah, Wubi has this kind of thing happen a lot. It's really best to test out a livecd and then do a normal install if the livecd works.

---

### Post by ubu newb on 2010-03-24
> **Cephiro said:**
> Wow thanks, that worked as a charm. :D

This should be made more public, I guess lots of people would have this problem...;)


Glad it worked.  Could one of the admins sticky the fix above since there are a quite a few instances of wubi failing to boot?

---

