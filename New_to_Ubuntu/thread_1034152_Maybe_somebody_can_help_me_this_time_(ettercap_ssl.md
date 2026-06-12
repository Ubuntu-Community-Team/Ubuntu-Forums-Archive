---
title: "Maybe somebody can help me this time (ettercap ssl)"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by eaterofbrainz13 on 2009-01-08
Ok so I previously asked why I couldn't pick up hosts in ettercap. I did a little research and found that I have to uncomment the lines in the iptables section of the config file for ettercap. Im pretty new to ubuntu but I searched for the config file using sudo find / -name /etc/ettercap.conf. That didnt' help. So if somebody could tell me first where to find this file and then how would I edit it in ubuntu. Thanks!

---

### Post by gettinoriginal on 2009-01-08
Alt F2 and enter ```
gksudo nautilus
``` this will bring up your file browser in root.  Search for ettercap.conf.    Open with your preferred text editor.

---

### Post by cariboo on 2009-01-08
All the ettercap configuration files are in /usr/share/ettercap.

Jim

---

### Post by eaterofbrainz13 on 2009-01-08
Ok I found it. Its actually in  /etc/etter.conf. I edited it using the command nano /etc/etter.conf . Super easy (8 hrs later lol).

---

### Post by gettinoriginal on 2009-01-08
Glad you got it working :P  Please go to tools and mark this as solved.

---

### Post by zeezam on 2009-01-17
Trying to use ettercap to sniff login on my home network.

```

sudo ettercap -i wlan0 -Tq -d

```

"Starting unified sniffing..."

Try log in on gmail, hotmail etc.
Nothing appears in the terminal...

What do I do wrong? Have tried the GUI also.

---

