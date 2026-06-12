---
title: "WPA problems"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by Trident167 on 2008-09-24
I have managed to install the original driver for BelkinF5D7010 with ndiswrapper. The card is recognized and is able to find the network. Only problem is it won't accept the pass. It keeps asking over and over. Wondering if it's a problem with the driver install. Any ideas - keep in mind I'm sort of a newb to Linux.
Currently there are 2 drivers installed with ndiswrapper - "blkwgnv7" and "net8185". The "blkwgnv7" is the original cd driver which accepts the reads the card and is the one that is active. Could I remove the other one without diturbing things? How?

Thanks,

Tony

---

### Post by Trident167 on 2008-09-25
So far I have managed to get the card working with what help I was able to find on here. 
Now to my other problem. I have two identical laptops (thinkpad 600x) with identical wireless cards installed (Belkin F5D7010). As you would have it, they both have different chipsets so one was working with the Atheros drivers and the second I had trouble with adding my windows drivers and ndiswrapper - problem stated in earlier post. 
Now second works like a charm and the original Atheros based one picks up the network and shows it's connected but won't connect. It worked fine on the initial install. Am i missing something?
I'm sort of a noob so if I need to post something let me know. 

Thanks,

Tony

---

### Post by willca on 2008-09-26
post this for the card that wont work.

lspci | grep Ethernet

---

### Post by Trident167 on 2008-10-03
Sorry about the delay, it's been a busy week.
I managed to get it working with one of the stickies.
Thanks!

---

