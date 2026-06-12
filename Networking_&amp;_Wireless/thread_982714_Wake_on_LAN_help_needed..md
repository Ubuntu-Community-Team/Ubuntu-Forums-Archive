---
title: "Wake on LAN help needed."
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by Suilenroc on 2008-11-15
Hey there, Suilenroc here.

So I've been working on making a home server, detailed in my thread in the server platform forums here. I'm trying to get it to Wake on LAN, but I've been unsucessful, mostly because the best tutorials are all from ubuntu 6.06 or 5.XX. I know that WOL works, as it worked when I shut down from windows. Something in the Ubuntu shutdown process is not letting the network adapter stay alive.

Speaking of which, I have to shutdown with either "sudo init 0" or "sudo shutdown -h now." For some reason, the shut down option is missing from the context menu in the upper right.

---

### Post by buccaneere on 2008-11-15
Are the shutdown options missing also from System / Quit ?

---

### Post by Suilenroc on 2008-11-15
No, they aren't. Hadn't noticed that before. 

But that's not my main concern, I can live with making an executable script for shutdown, or going system->shutdown. What I want is the WOL, but I have no idea how to get it going. I've used ethtool, made a /etc/init.d/wakeonlanconfig file with this in it:

```
 
ethtool -s eth0 wol g

```

---

### Post by buccaneere on 2008-11-15
Your script is beyond me there... But the instability of networking is beyond us all I think...

Cool username there:

---

### Post by Suilenroc on 2008-11-15
Eheh, thanks. It's my middle name, actually, just backwards. I use it for most iternet aliases. 

So, anyone else have any idea? I'm pretty sure that there's just one option that I'm not finding, that, once switched, will stop the total shutdown of the computer's networking. I just don't know where to look...

---

