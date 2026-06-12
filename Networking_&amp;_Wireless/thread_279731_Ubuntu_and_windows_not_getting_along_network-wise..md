---
title: "Ubuntu and windows not getting along network-wise."
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by curgoth on 2006-10-18
I'm running Ubuntu server 6.06 LTS, and having weird issues with the windows machines having thier connections to the Ubuntu server periodically.

I have four machines in the back room.

Velvet, the old linux server (debian).
Phoenix, the new linux server (Ubuntu server 6.06 LTS).
Gir, my windows desktop.
Shiny, a windows laptop.

Gir and Shiny can talk to each other with no trouble. Velvet and Phoenix can talk to each other with no trouble. Phoenix can connect to Gir with no trouble. But when Gir or Shiny connect to Phoenix, they are fine for a little while, but if we do anything intensive like playing mp3s off of samba shares on Phoenix, or tranferring large files, Phoenix cuts them off. 

Completely. 

Not just samba shares - all TCP/IP connections (ssh, etc.) are cut off, and Phoenix won't talk to those boxes for a minute or so after they get cut off. No idea why. I tried upgrading to a new gigabit switch (phoenix and gir have gigabit cards), and I don't think it's network cabling, since the window -> velvet connections and the velvet <-> phoenix connections are solid (stay connected for weeks, etc.)

I've checked the process monitor on Gir, and I'm not seeing a huge spike in CPU usage or network usage before the cut offs. I played around with Samba settings to make sure Phoenix, not one of the windows machines, is the master browser for the workgroup.  I checked Phoenix for weird iptables entries, and there were no rules set up, which is what I had expected.

I'm running out of ideas, here. Anyone have any idea what could be causing this?

---

