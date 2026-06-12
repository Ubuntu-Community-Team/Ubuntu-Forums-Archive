---
title: "Strange DNS issue with feisty upgrade."
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by dave_the_moon_man on 2007-04-25
Have searched already but can't find the reason for this.

After upgrading to feisty, i managed to get my PC Card Wireless adapter recognised and working by editing /etc/network/interfaces.

However, every time i connect to the network, my DNS settings are overwritten meaning i have to enter them manually in the GUI.

Also, although i can browse the internet fine, I can't ping my router. I says 'destination unreachable' even though i can get to its config pages fine in the browser.

Can anyone help me out?

Dave.

---

### Post by Buffalo Soldier on 2007-04-25
[LIST=1]
[*]Run: ```
sudo gedit /etc/dhcp3/dhclient.conf
```

[*] Uncomment and edit the prepend line (line 18 for me) to include the IP of the DNS servers that you want to use (example 208.67.222.222 and 208.67.220.220):

> #prepend domain-name-servers 127.0.0.1;
prepend domain-name-servers 208.67.222.222, 208.67.220.220;

[*]Run: ```
sudo /etc/init.d/networking restart

```[/LIST]

---

