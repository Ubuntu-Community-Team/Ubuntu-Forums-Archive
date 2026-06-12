---
title: "new cable/dsl router now i cannot connect to the web"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by feelthejoe on 2007-09-30
i had been connecting to the internet fine with a direct connection. i just bought a linksys cable/dsl router and installed it on my laptop with XP and XP connected to the web fine. i then connected the cable to the 2nd router port the back of my ubuntu box. i now cannot connect to the internet unless i go into terminal and type..

sudo poff dsl-provider
sudo pon dsl-provider

once i do that it will work how do i fix this? thanks.

---

### Post by feelthejoe on 2007-09-30
i have fixed the problem for now i edited rc.local with the following lines..

poff dsl-provider
pon dsl-provider

and i can connect to the internet fine once it boots up.. can anyone help me with why i must do this? thanks

---

### Post by noob12 on 2007-09-30
Your new router will handle the PPPOE now for you on its WAN port.  The ethernet ports it offers for the internal net provide nice straight IP over ethernet.

What this means is that you need to take out any commands that start PPP on your box at boot time (like "pon").

After that just set your wired connection up for regular Automatic DHCP configuration using the  **System | Administration | Network** menu.

---

### Post by feelthejoe on 2007-09-30
i've done this and it does not fix the problem. the only way i can get the internet to work is..

sudo poff dsl-provider
sudo pon dsl-provider

why is this and i had been running those lines in rc.local but now it wont work either i have to keep opening up terminal and typing it in

---

### Post by noob12 on 2007-09-30
Well rc.local runs after networking so it is happening too late to help.  Maybe you can find where your ppp setup is getting triggered to begin with.

A pretty common place for starting it is in the file /etc/init.d/network/interfaces in pre-up lines for ppp0.  Can you post the output of these commands?

```

ifconfig -a

cat /etc/network/interfaces

grep -n "pon" /etc/init.d/* | grep -v swapon

```

---

