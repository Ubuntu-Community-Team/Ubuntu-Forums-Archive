---
title: "UFW and custom rules"
date: 2017-09-23
forum: Networking &amp; Wireless
---

### Post by Eldon_McGuinness on 2017-09-23
Hi all, I was looking to setup some port redirection, which turns out to be odd with ufw, and was able to find an answer as to how it is accomplished. However, the answer left me instead with a new question:

[FONT=monospace]In the example below, it adds a rule to the nat tables PREROUTING chain:

[/FONT]```
[FONT=monospace][COLOR=#000000]*nat [/COLOR]
:PREROUTING ACCEPT [0:0] 
-A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 32400 
COMMIT
[/FONT]
```[FONT=monospace]

The only thing I do not understand is what does the [0:0] means in this config, I've done a fair bit of reading and googling with no results. Thanks in advance for any help anyone can lend.

[/FONT]

---

