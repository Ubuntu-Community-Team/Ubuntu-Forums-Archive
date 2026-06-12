---
title: "why does wireless need to be &quot;reset&quot; ?"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by dhuff on 2005-12-01
I've got an HP DV1000 laptop with the Intel Integrated wireless 2200 chipset, which I dual-boot between WinXP, sp2 and (K)Ubuntu 5.04.

It seems like about 50% of the time I can't get connected to my Linksys WRT54G AP and have to go into the Network config GUI and re-enter all the specs to get it to work. (an analogous procedure to "repairing the network connection" under Windows). This happens both after I've booted into WinXP, or just restarted from a prior Ubuntu session.

Any idea why I have to slap my Intel 2200 chipset around like this ?

---

### Post by WanStiller on 2005-12-22
I have exactly the same laptop and setup, and I'm getting the same issue :( 

I hoipe someone has any ideas how to correct this, everything else is working just cool.

---

### Post by rfmonk on 2005-12-23
I don't have the same laptop (I have a Sony VGNT350P) with 5.04 and am dealing with the same issues, when I run dmesg I get WEP decryption failed and I have entered this stuff manually time and time again. Im only posting to keep this up high on the stack so someone will hopefully address wireless issues or point a link to something we should have read.

However, try iwconfig
                  ifconfig
                  dmesg to get better info on network, I wonder if you can sudo gedit iwconfig to change something that way or is there a prefered method?

---

### Post by WanStiller on 2005-12-28
Well, after several days of poking around with iwp2200, nothing worked. So I decided to reinstall ubuntu from scratch, then get all the updates to the kernel through my wired ethernet connection, and THEN configure my wireless interface. It works perfectly now, "almost" out of the box, you might say. :smile: 

I don't mean to go around recommending to reinstall, it's dirty and no real understanding of  what the real issue was, but I was clean out of ideas, and in the end it seems to be working fine. I'm glad it did too, I really having fun with ubuntu and this was the only thing keeping me from using it more.

---

### Post by WanStiller on 2005-12-28
I just realized this thread is under hoary, and I'm using Breezy....guess this should be in another part of the forum..well, the important thing is it's finally working!

---

