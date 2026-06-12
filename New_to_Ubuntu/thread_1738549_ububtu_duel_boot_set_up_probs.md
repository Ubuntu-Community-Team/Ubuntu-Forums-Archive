---
title: "ububtu duel boot set up probs"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by birdibeach on 2011-04-24
I have successfully managed to set up duel boot with ubuntu 1010 and win 7 with a usb.
No problems and I am very happy with ubuntu. The hardware is a Dell Inspiron. I used the "Install with other OS system" at install start up which made the process very easy for a newbie like me. I have tried to do the same thing with my brothers computer and the "Install with other OS function" is not available requiring manual set up, GParted, mount points and a whole lot of other stuff that is over my head. Is there a simple way to get Install with other OS option on my brothers install?

---

### Post by Dutch70 on 2011-04-24
Hi and welcome to UF

It may be that he already has 4 primary partitions which is the max. Boot to the live cd/usb, open Gparted & take a screenshot. Attach it to your next post with the paper clip in the toolbar.

---

### Post by birdibeach on 2011-04-24
Thanks Dutch I' am really grateful. I did not need to take a screen dump as I figured the problem out using Disk Mgt in Win 7. Apparently to start with there was an old partition with vista on it that I deleted. I then created a new partition resizing the main one that win 7 had which was 400Gig. This was my mistake that did not enable the auto install option (due to too many partitions). When I returned the partition to its original size without the vista partion, I obviously met the limit. I have now successfully installed Ubuntu along side win 7 using the "install with other OS" function. See how we go. Much obliged kind sir.

birdibeach

---

### Post by Dutch70 on 2011-04-25
Nice! You're quite welcome.

Maybe I'm a little too late here, but you do know that if you create an extended partition, you can create just about as many (logical) partitions inside it as you want? Linux, unlike windows is perfectly happy inside a logical partition & you're going to want a prtn for swap, although you can use a swap file. I'd create a prtn.

---

