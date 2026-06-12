---
title: "Angry about broadcom 4318 on lenovo 3000 c100"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by Gargamella on 2006-10-20
before i reinstalled Dapper, i was able to use wifi card by bcm43xx-fwcutter... now i reinstalled Dapper but i cant make it work

i did 

sudo bcm43xx-fwcutter -w Desktop/bcmwl5.sys
(original drivers)
but also bcm43xx-fwcutter -w Desktop/wl_apsta.o
(this worked last time before formatting)

but now i can't turn on the wifi chipset light on... don't know why... i am quite sure to have done all the necessary ...

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Gargamella on 2006-10-21
no ideas?

---

### Post by LinLenLap on 2006-10-31
I've got the same laptop, and I found that it works even better under Edgy than under Dapper.

From a clean install, I followed the instructions on this forum:

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom)

I used the recommended above all other drivers. Also copied to firmware and kernel. Also made sure my router is set to G only.

Best,

LLL.

---

