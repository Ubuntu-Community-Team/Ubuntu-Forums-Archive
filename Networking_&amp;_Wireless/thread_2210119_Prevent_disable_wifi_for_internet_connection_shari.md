---
title: "Prevent disable wifi for internet connection sharing"
date: 2014-03-09
forum: Networking &amp; Wireless
---

### Post by dikdirk on 2014-03-09
I am running Lubuntu 13.10 on my laptop and am trying to set up internet connection sharing with my desktop which also runs on Lubuntu 13.10. I want my laptop to be connected to wifi and then share its internet connection with my desktop. 

For this I followed the following manual: [http://forum.lxde.org/viewtopic.php?f=6&t=31326](http://forum.lxde.org/viewtopic.php?f=6&t=31326).

However, when I plug in a network cable into my laptop the wifi is automatically disabled and my laptop is no longer connected to the internet! Does anyone know how to prevent this behaviour?

---

### Post by varunendra on 2014-03-11
By default Network Manager prefers wired connection, but I don't think it disables the wireless. I haven't tested this personally, so maybe wrong though.

However, if the wireless is 'Physically' turned off (i.e., "rfkill list" command shows "hard blocked"), then it is most certainly a BIOS feature that some models have (notably HP Pavillion Dv4). So if it is physically disabled, check your BIOS and disable this behaviour from there.

---

### Post by dikdirk on 2014-03-12
I have a HP nx63200 and it indeed turned out to be a BIOS option. This solved my problem thnx!

---

### Post by varunendra on 2014-03-12
Good shot! Please mark the thread as [SOLVED] to make it more useful for others. :) The option is in the "Thread Tools" link above the top post (when you are logged in).

---

