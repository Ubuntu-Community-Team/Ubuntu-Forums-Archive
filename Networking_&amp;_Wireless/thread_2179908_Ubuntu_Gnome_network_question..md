---
title: "Ubuntu Gnome network question."
date: 2013-10-10
forum: Networking &amp; Wireless
---

### Post by Tenck on 2013-10-10
As of this moment I'm writing this post from the demo version of Ubuntu Gnome. My question is about internet connection when I do the complete install of Gnome. 

Whenever I do the full install of Gnome, my internet will work during the installation process. So while everything is being downloaded and installed, I can go ahead and connect to the internet (the slide show during the process of installation ends on a slide with a link to Linux wiki. Clicking that opens up FireFox and I can navigate any website). After the installation is done I reboot, boot up into Gnome, and log into my account. That's when my internet has problems. I've gone into Network settings and changed it to wired, and even turned off Airplane mode just to be sure. I'll hit "On" and it'll try to connect, but it can never get an IP address or DNS address. For Windows whenever I had problems I'd just download the newest version of a network drivers. For Gnome I have no idea how I'd even do that. If anyone could help me I'd appreciate that.

---

### Post by varunendra on 2013-10-13
Welcome to the forums Tenck!

Let us see which card you have and which driver it is using, plus a few other obvious things. Please open a terminal (Ctrl-Alt-T) and enter the following commands in it (one-by-one, you may copy-paste from here) -
```
lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
rfkill list all
nm-tool
```

Post back the entire output here. While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

