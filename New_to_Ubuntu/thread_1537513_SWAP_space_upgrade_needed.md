---
title: "SWAP space upgrade needed?"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by JP121 on 2010-07-23
Hi.
 
I just have recieved 2 gigs of RAM I am installing in my system.  My understanding is that because I will now have more ram, I also need more SWAP space.  My current amount is whatever the default is when installing (I originally had 512 mb if that changes anything).
 
Do I need to change the SWAP partition, and if I need to, is it safe to do this via the Live CD?

---

### Post by JKyleOKC on 2010-07-23
If you use the "suspend" or "hibernate" options, then yes, you need to increase the size of the swap partition to at least the amount of RAM you have. The reason is because when you hibernate, the system copies all of the RAM into the swap partition so that it can power down, and then restores it when you power back up.

If you never use these capabilities, then you should be in good shape with your existing swap size. With 2 GB of RAM there should be very little actual swapping taking place during normal operation.

It should be possible to do the resizing from the live CD, but someone who's more expert in this area than I am will have to say for sure. I understand that any existing swap space is used, even by the live CD, and this could lead to difficulties. However you should be able to turn swap off long enough to do the resizing, if need be...

---

### Post by linux18 on 2010-07-23
-boot to a live cd
-open gparted
-click on the swap space and click "swapoff"
-delete the swap partition
-resize the ubuntu partition down 1536MB
-apply 
-click on the 2GB of free space and format it as linux swap

but if you don't hibernate you don't need any swap

---

### Post by JP121 on 2010-07-23
Thank.  I will do that tonight.

---

### Post by QIII on 2010-07-23
Swap should not be needed during suspend.

Suspend shuts down the machine with the exception of enough power to maintain the RAM.

Hibernate (or "suspend to disk") writes RAM state to swap and then powers down everything including the RAM.

I have zero swap (lots of memory, no need, don't hibernate because boot times are so fast now), but I can suspend just fine.

Hibernate has the advantage in that the RAM state is recoverable after a power failure.  In suspend, power goes off to the RAM, and the state is lost.  You are basically just starting the machine over.

---

