---
title: "Problem starting the Ubuntu Firewall"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by ed89 on 2009-03-15
I have installed this [firewall]("http://rob.pectol.com/content/view/2/1/") in my Ubuntu 8.10, and I modded the config-file to say DISABLED="no", however, it won't start.

```
eivind@ED-linux:~$ sudo ubuntu-firewall start
 * Ubuntu-firewall has been DISABLED in the config file!  Exiting...

```

What to do? Thanks.


*I missed that the config file was to be located in /etc/default.. Got it now! Thanks*

---

### Post by drs305 on 2009-03-15
In the config file it says you have to either reboot or run the following command before the settings will take effect. Have you tried this before starting it again?
```

sudo ubuntu-firewall stop

```

Note the spelling above - I imagine it's a typo in the config file and changed it. The actual config text calls for "sudo ubunti-firewall stop".

---

