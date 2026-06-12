---
title: "Peculiar problem with wireless"
date: 2016-09-25
forum: Networking &amp; Wireless
---

### Post by avrgarc on 2016-09-25
My wireless doesn't work like it should. I just installed Ubuntu  16.04 on a new machine dual boot with Windows 10 (previously I tried  installing other Linux distros, but had the same problem).
  Here's what happens: my laptop is plugged (power), then i turn it on  and what happens is that with every linux distro the Wi-Fi doesn't work  upon the start; i have to unplug and plug it again (always to the power)  for the Wi-Fi to work. After this, it doesn't matter whether it is plugged or unplugged, it still works. Then when i turn it off, the whole thing  repeats.

  Now, here's a couple of information you might want to know:
  
[LIST]
[*]The WiFi works just fine, all the time, with Windows 10.
[*]During the installation of Antergos from Live USB, the WiFi works. After the installation it can happen that the wifi works for a while, even though i  restart it multiple times, but eventually, the wifi starts to do this  strange thing.
[/LIST]

1) Rfkill says the wifi is hard blocked.
2) ```
 cat /sys/class/rfkill/rfkill0/hard 
``` result is: 1 (no i can't seem to be able to unlock it)
3) The power management option is off

I'd really appreciate some help; i have no idea how something like this is even possible!

---

