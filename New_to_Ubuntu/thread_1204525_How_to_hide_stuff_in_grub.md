---
title: "How to hide stuff in grub"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by The Jinx on 2009-07-04
Hi,

I just reinstalled a image of 9.04 to my Dell Vostro a90 and I'm getting some text before it loads into the Ubuntu splash screen. I was just wondering is there anyway to hide whatever text that shows up before the Ubuntu splash screen.

Thanks,
Jinx

---

### Post by earthpigg on 2009-07-04
you could try changing things using the StartUp-Manager package

---

### Post by theozzlives on 2009-07-04
> **The Jinx said:**
> Hi,

I just reinstalled a image of 9.04 to my Dell Vostro a90 and I'm getting some text before it loads into the Ubuntu splash screen. I was just wondering is there anyway to hide whatever text that shows up before the Ubuntu splash screen.

Thanks,
Jinx

What kinda text you getting? You're gonna get a little.

---

### Post by The Jinx on 2009-07-04
ummm. just like the Grub loading countdown and when it tells you it is loading Ubuntu 9.04

something like: 

" GRUB loading stage1.5 "

---

### Post by llazarte on 2009-07-10
> **The Jinx said:**
> ummm. just like the Grub loading countdown and when it tells you it is loading Ubuntu 9.04

something like: 

" GRUB loading stage1.5 "


Yeah, I was trying to get rid of this as well. Unfortunately, with no luck until now :-(

**hiddenmenu** is not enough...

---

### Post by kandieyman on 2009-07-10
That is not something that you will be able to hide. Also, do not expect that to change, when Ubuntu switches to Grub 2, the message will change, but it will still be there.

---

### Post by LewRockwell on 2009-07-10
if you don't need to dual-boot then you don't need grub

eliminating is better than hiding

.

---

### Post by egalvan on 2009-07-11
Changing the "timeout" value to zero will make it flash by much faster,
but it is still visible.

---

### Post by QIII on 2009-07-11
Changing the timeout value to 0 also keeps you from being able to select another OS in a dual boot configuration.

If you have, say Vista, before your Ubuntu entries, you'll catch h*ll trying to boot to Ubuntu.

I'd just go with about 3 seconds.  I've heard complaints that people get it defaulted to 0 on install with Jaunty, but I can't confirm.

---

### Post by egalvan on 2009-07-11
> **QIII said:**
> Changing the timeout value to 0 also keeps you from being able to select another OS in a dual boot configuration.


I'd just go with about 3 seconds.  I've heard complaints that people get it defaulted to 0 on install with Jaunty, but I can't confirm.

Yeah, your're right, but the OP sounded as if he were single booting.

As for Jaunty default, I've set it up on three different machines...
all three defaulted to ten seconds...
same as my old Hardy...

(immediately changed to 60 seconds, but that's just me)

---

### Post by The Jinx on 2009-07-13
no I am single booting, its just that it shows that

---

