---
title: "Grub2 confusion...how do I make an older kernel boot by default??"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Kapitän Rotbart on 2009-11-24
Hey,

See, 2.6.31-14-generic works for me on my t91, but 2.6.31-15-generic does not.

I would like someone to tell me either how I can get ...-15 to work, or how I can boot ...-14 by default. I also find it really tricky to access the grub menu, I have so little time to hit Esc before it starts booting the default kernel. Any help? It's really annoying to have to make several attempts just to access grub, just to boot an old kernel in order to get an Ubuntu session.

I considered switching to Mandriva, but I couldn't figure out how to get the touch screen to work :P So I'm pretty desperate at this point :(

---

### Post by drs305 on 2009-11-24
Edit /etc/default/grub and change the DEFAULT= line. Here is a link for all the details:
[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

---

