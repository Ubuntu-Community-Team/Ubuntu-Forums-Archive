---
title: "Wireless Stopped Working"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by Jerim on 2006-07-21
I started this discussion in another thread, but it seems to have stopeed getting responses:  [http://www.ubuntuforums.org/showthread.php?t=217714&highlight=wireless+stopped+working](http://www.ubuntuforums.org/showthread.php?t=217714&highlight=wireless+stopped+working)

The basics is that my wireless card has been working great for the last few months. I recently moved to another apartment. While I was at the new place, moving some stuff in, I logged on to the free wireless connection that is available for the apartment complex. When I went back to my old apartment to spend the night, it no longer gave me the wireless option on the Network Manager Applet at the top. For some odd reason I could still open a browser at home and it would let me get webpages. It just worked without me having to set anything up. 

However now, it won't work at all. I used the suggestions in the above thread, and it appears the wireless card is recognized by Ubuntu. It just won't stay on. Any help will be greatly appreciated. I did do some updates recently, however there was a gap of a few days between the updates and the wireless issue. It wasn't an immediate effect.

---

### Post by jknotzke on 2006-07-21
I have the same problem.

   I looks like it's the kernel. Using vmlinuz-2.6.15-23-386 it works, but using vmlinuz-2.6.15-26-386 it does not..

   I did find this: [http://folk.uio.no/krisvh/linux/cl56.html](http://folk.uio.no/krisvh/linux/cl56.html) which looks promising..

   The problem appears that the module used to control the internal card, cannot turn the 'radio' on. 

   Justin

---

