---
title: "snort - Invalid CIDR block for IP"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by midcocc on 2008-12-05
I installed snort and fat fingered the intial ip range during the setup/install script of

apt-get install snort-mysql

Now when I go to start I get an error it fails to start snort and there is a message in the daemon.log of
FATAL ERROR: Error  /etc/snort/rules/bad-traffic.rules/(27): Invalid CIDR bloc for IP addr ###.##.###.###/##

and the ###.###.###.###/## is the number I fat fingered during install.  Where is this located so I can edit it?  It's not in the /etc/snort/snort.conf file.

thanks!

---

### Post by bodhi.zazen on 2008-12-05
did you try the file in the error message ?

> FATAL ERROR: Error  **[COLOR=red]/etc/snort/rules/bad-traffic.rules[/COLOR]**/(27): Invalid CIDR bloc for IP addr ###.##.###.###/##

You can also grep 

```
sudo grep -R ###.##.###.###/## /etc/*
```

---

### Post by midcocc on 2008-12-05
cool, thanks! 
/etc/snort/snort.debian.conf

"It's the little things"!

---

