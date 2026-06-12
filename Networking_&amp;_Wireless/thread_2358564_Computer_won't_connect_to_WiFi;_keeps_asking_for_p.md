---
title: "Computer won't connect to WiFi; keeps asking for password"
date: 2017-04-14
forum: Networking &amp; Wireless
---

### Post by jsc12345 on 2017-04-14
Today I upgraded to Ububntu 17.04. When I booted for the first time since the update, my computer asked me for the password to my home WiFi network. Well, I thought, the thing's just updated the OS, prehaps it's forgotten the network. So I input the password and waited for it to connect. The box came up again. After restarting the router and computer, quadruple-checking the password and forgetting the network, I have been forced to turn to the Greater Internet for help. What's causing this problem? Is it a problem with the new kernel/OS? What can I do about this?

---

### Post by Autodave on 2017-04-14
Couple of things come to mind.  I have several laptops, but one in  particular gives me fits anytime I try to enter a wireless password: it  will take me 20-40 times before it actually accepts it. Why? No idea.

Another is this: on any laptop, when something that used to work  suddenly quits working for no apparent reason, try this.....and don't  laugh.....I have "fixed" many laptops this way: shut down, disconnect AC  power, remove battery. Wait 10 minutes, reinstall battery and power up.  See if wireless works now.

---

### Post by kurt18947 on 2017-04-15
I've had this happen though not recently. I found that removing the connection then redoing it fixed the problem. I use this app accessed via alt-F2 :
```
nm-connection-editor
```
Remove the problem connection then recreate it. I'm using Ubuntu-Gnome but I assume this app is available in all 'flavors' of Ubuntu.

---

### Post by wildmanne39 on 2017-04-15
*Thread moved to **Networking & Wireless**.*

---

