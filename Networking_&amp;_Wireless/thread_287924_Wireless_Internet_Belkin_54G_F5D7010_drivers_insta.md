---
title: "Wireless Internet Belkin 54G F5D7010 drivers installed, hardware not recognized"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by seidleroni on 2006-10-29
Hi everyone,

I have installed Ubuntu on my old win98 laptop.  I'm really really new to Linux and although i'm fairly knowledgeable when it comes to computers, this whole linux thing is new to me.

I installed Ubuntu and I have the belkin wireless card noted in the title.  At first, the wireless option showed up when I went to administrator->network.  However, I followed the directions here:

[http://ubuntuforums.org/showthread.php?t=187004](http://ubuntuforums.org/showthread.php?t=187004)

I put the files in /home/windows_drivers (is this OK?).  After I followed the directions,  I entered:

sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5a         driver present

(Note, I get 'driver present' and not 'hardware present').  After I follow the directions, the wireless option does not present itself anymore under the network area.  I then installed "Network Manager" as someone else suggested, however, after installing, I cannot find it under the 'programs' area.  

Oh, by the way, the light for the belkin isnt on.  When I"m in windows, it works well, but in Ubuntu, the belkin power light doesnt come on.

Is Network Manager gonna get me up and running? if so, how do I start it?  Is there anything else I can do?  If the drivers are 'present', then how do I get it to recognize that the hardware is present?

Thanks!

Seidleroni

---

### Post by Village on 2006-10-29
I'm having the same problem. Before I upgraded to 6.10 it had just started to work in 6.06 after weeks of trying, I guess it was thinking "I've made him suffer for long enough".

I'll let you know what happens...

---

