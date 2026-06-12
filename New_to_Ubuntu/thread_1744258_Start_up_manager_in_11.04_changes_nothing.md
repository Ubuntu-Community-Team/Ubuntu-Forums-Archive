---
title: "Start up manager in 11.04 changes nothing"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by wapfu on 2011-04-30
Upgraded to 11.04 and have tried to change the boot order in the grub to start with windows xp. No matter how much I try - start up manager shows xp the grub shows the new release. Dam skippy its annoying. And the time in the top - want it to read 12 hour not 24 - dang thing will not change either.:confused:

---

### Post by j0hnnya on 2011-04-30
Having the same exact problem here.  Usually use the Start Up Manager to repair this issue (every time I install updates on Ubuntu) and it works every time - but not with the Gosh Darn Narwhal.

If and when Win 7 decides it wants to restart the system then the system restarts in Ubuntu.

Looking forward to a solution.

---

### Post by JayKay3OOO on 2011-04-30
The time is really easy to change to 12h:

Click The Clock > Time and Date settings > Clock tab > choose the time type.

Heh,heh - Why have I not used Windows 7 for 6 months? Oh I remember! The annoying auto-restart option. Scratch downloading something when you are sleeping.

---

### Post by wapfu on 2011-05-01
Tried that Jaykay3000 didn't work either. :(
Grub and the clock don't seem to want to play the game.

---

### Post by Hedgehog1 on 2011-05-01
> **wapfu said:**
> Upgraded to 11.04 and have tried to change the boot order in the grub to start with windows xp. No matter how much I try - start up manager shows xp the grub shows the new release. 

Start Up Manager is not yet updated to work with Natty.

However, here is how you can change the Grub menu order to have your Windows installation first in the menu:

```
sudo mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober
```

```
sudo update-grub
```


***The Hedge***

:KS

p.s. Grub has gone through some signification enhancements, and many options are set in new ways.  It will likely take Start Up Manager developers a little while to catch up.

---

### Post by wapfu on 2011-05-02
That worked Hedgehog1 - cheers.:)

---

### Post by mguentz on 2011-05-04
Thanks Hedgehog1! It worked like a charm for me too. \\:D/

---

### Post by Daneel.Olivaw on 2011-05-04
> **Hedgehog1 said:**
> Start Up Manager is not yet updated to work with Natty.

However, here is how you can change the Grub menu order to have your Windows installation first in the menu:

```
sudo mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober
```

```
sudo update-grub
```


***The Hedge***

:KS

p.s. Grub has gone through some signification enhancements, and many options are set in new ways.  It will likely take Start Up Manager developers a little while to catch up.
I had de same problem and this worked like a charm.

Thanks a lot!

---

### Post by windrider42 on 2011-06-30
That worked for me as well Hedgehog1.. Thanks

---

### Post by shuttleworthwannabe on 2011-07-25
Thanks worked like I expected--now how do I reverse the order, i.e. Have Ubuntu boot first then Windows 7?

---

### Post by ruedishe on 2011-08-09
Thank you very much Hedgehog1. This worked perfect for me. I wonder if this has to be repeated after every new kernel update? Could you also explain the code?

---

### Post by ruedishe on 2011-08-09
Thank you very much Hedgehog1. This worked perfect for me. I wonder if this has to be repeated after every new kernel update? Could you please also explain the code?

---

### Post by ruedishe on 2011-08-09
Thank you very much Hedgehog1.  This worked perfect for me. I wonder if this has to be repeated after every new kernel update?  Could you please also explain the code?

---

### Post by windrider42 on 2011-08-14
> **shuttleworthwannabe said:**
> Thanks worked like I expected--now how do I reverse the order, i.e. Have Ubuntu boot first then Windows 7?


I am not sure how to reverse it again, but you could just set it to load Ubuntu now in the Start up Manager

---

### Post by shuttleworthwannabe on 2011-08-17
Yah, it is a bummer--I am in Oneiric, and StartUpManager still not fixed.

---

### Post by Rolyh on 2011-09-12
Thanks hedgehog.
Worked for me too.

---

### Post by airplanesimen on 2011-09-25
I do have a problem! I wrote in ur commands in the terminal. it worked. But the problem is when i restarted my computer, it is the recovery for windows on top. the second choice is windows loader... can i enter the file end fix this manually? i need windows loader on top, not the recovery :P

---

