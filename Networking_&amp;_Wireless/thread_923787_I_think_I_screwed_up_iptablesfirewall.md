---
title: "I think I screwed up iptables/firewall"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by adlin5000 on 2008-09-18
I had ports forwarded through my router for Deluge and Frostwire, and they were working fine. Then I decided to give amule another try. I followed the instructions here on how to open ports in iptables (both manually and with firestarter):

[http://ubuntuforums.org/showthread.php?t=526975](http://ubuntuforums.org/showthread.php?t=526975)

Well not only did it not work for me, but now all my ports are closed! I removed amule and firestarter and still nothing. If anyone can give me a clue on what I messed up and how to fix it, I would appreciate it.

I'm not sure what info would be helpful on this one, so let me know what info you need and I'll get it to you.

Thanks

---

### Post by adult swim on 2008-09-18
from a terminal, type  in ```
sudo ufw enable
``` and then ```
sudo ufw allow xxxx
``` where xxxx is the port you want to open, example sudo ufw allow 3039 will open port 3039.  to close the port if you want type in ```
sudo ufw delete allow xxxx
```
if your programs are still showing your ports closed, have you opened the ports in the router as well?

---

### Post by adlin5000 on 2008-09-18
Thanks for the help. opening the ports did not do it, but I figured a way. I looked at the help message for ufw, and ran "sudo ufw disable" and that did the trick.

On a side note: I have never used a firewall except the one on my router (WRT54-g running DD-WRT firmware), is that wise? Should I use one?


Again thanks for the help.

---

