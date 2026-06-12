---
title: "help -- network disabled?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by carrarin on 2010-10-07
Hello everyone, 

For some reason I can't access the internet from my netbook. I am using ubuntu 10.04. I've been using 10.04 for a while now and havent had problems with the internet so far. 

When I click on the network indicator applet it says "network disabeled" 

also, 

```
ifoncig
```

only shows the loopback addr

Also, I am duel booting, and I am able to access the internet from my windows partition.

Help me, PLEASE!

---

### Post by sikander3786 on 2010-10-07
Right click the Network Indicator Applet, go to Edit Connections and Add a new connection. Does that solve the problem?

---

### Post by cap10Ibraim on 2010-10-07
right click the network applet is the "Enable Networking" checked ?

---

### Post by xircon on 2010-10-07
Run:

```
cat /var/lib/NetworkManager/NetworkManager.state
```

If any of the lines say false:

```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```

Change to true.  Save then reboot.

---

### Post by missingperson on 2010-10-21
i just had the same problem today. i'm using an intel imac, dual boot into mac os x 10.6,  and after weeks of tinkering finally had ubuntu running perfectly. i have the broadcomm proprietary drivers installed and up until today they had been working fine, connecting to the router no problem on startup. last night i installed the flash add ons for firefox and added a new user. used the computer for several hours before sleep, no problems.

when i woke up this morning, i got the "networking disabled" message. there doesn't seem to be a remedy for right clicking in this environment (f11 and f12 are sound keys), so i ran the terminal commands that xircon recommended and they worked fine. now my networking is enabled.

new problem: the wifi card just searches and searches for a connection. every 60 seconds or so i get prompted for the password (which is already a part of the setup) i hit confirm, and the card keeps searching for about three minutes, then it just gives up. 

sum it up: old situation, wifi connection would be waiting and ready on startup. new situation: networking seems to be enabled, but i cant get the wifi to connect to my router. additional info: modem and router work fine for all other computers in the house running os x, so it's definitely a linux problem. please help.

edit: nevermind, the problem seems to have resolved itself without any real action on my part.

---

