---
title: "how to set gufw/ufw firewall rules ?"
date: 2024-10-14
forum: Networking &amp; Wireless
---

### Post by Xpdin on 2024-10-14
I want to set up through gufw or through ufw directly from the terminal, the next settings from the first print screen


The second print screen is the one from gufw, if in that gufw window, I must set up these rules.

---

### Post by Xpdin on 2024-10-14
[COLOR=#141414][FONT=&amp]&#8203;It is a must to add these rules in order for an app to work properly.[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]It seems that for the first rules the command is:[/FONT][/COLOR]
```
[COLOR=#141414][FONT=&amp]sudo ufw allow from 141.0.145.180/32 to any port 64297 proto tcp[/FONT][/COLOR]
```
[COLOR=#141414][FONT=&amp]Unfortunately, for the second rule, it should be something like that, but it doesn't work:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]
[/FONT][/COLOR]
```
[COLOR=#141414][FONT=&amp]sudo ufw allow 0:64000/tc[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]ERROR: Bad Port._&#8203;_[/FONT][/COLOR]
```
[COLOR=#141414][FONT=&amp]Any ideas, please?[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]Thank you.[/FONT][/COLOR]

---

### Post by TheFu on 2024-10-14
If you are going to allow everything in and out, just disable ufw.  If you did that in my company, you'd be fired.

---

