---
title: "Server questions (Minecraft, Cyberpanel, Matrix)"
date: 2022-04-17
forum: Networking &amp; Wireless
---

### Post by sacredtoast on 2022-04-17
Hello everyone! I have some experience with Minecraft servers. I have an HP Proliant 1U running Ubuntu 20.04 server. If I use Ubuntu desktop I can host my Minecraft server fine. If I use Ubuntu server everything starts fine according to output, but  I can't even connect locally. No route to host? This isn't a port forwarding issue because I just care about a lan server for now. I have an exception in ufw but maybe something else ufw related? The only other software on this server is Cyberpanel. Anyone with Cyberpanel experience understand if this could cause some kind of interference? Another off question, I've been obsessed with the idea of hosting my own matrix server for me and the buds. Everyone uses droplets and that's where I get lost. I have my own hardware, my own domain name the bones are there. Anyone have a decent guide for getting it going like such? If these programs interfere should I set them up in docker??

---

### Post by Tadaen_Sylvermane on 2022-04-20
[https://www.digitalocean.com/products/droplets](https://www.digitalocean.com/products/droplets)

Running your own Minecraft should be easy as pie on your own iron. I prefer to run mine in Docker personally but to each their own. I'm not sure what configuration you've done. For myself on both Debian and Ubuntu I can start the docker and just connect, assuming I have the proper ports targeted. I've never done anything exposed to the internet though.

This is the Docker I built for myself. Is configured to fairly easily run multiple servers at the same time.
[https://gitlab.com/jmgibson1981/homescripts/-/tree/master/docker/minecraftserver](https://gitlab.com/jmgibson1981/homescripts/-/tree/master/docker/minecraftserver)

---

### Post by sacredtoast on 2022-04-21
Thanks for all that! I will check it out when I'm done traveling this week!

---

### Post by sacredtoast on 2022-04-24
I just decided to set it up on a different machine and got it working the first time. Not sure what the issue was with the old machine.

---

