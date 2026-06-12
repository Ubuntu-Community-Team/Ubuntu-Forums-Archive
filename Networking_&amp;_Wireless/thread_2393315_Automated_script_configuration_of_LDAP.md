---
title: "Automated script configuration of LDAP"
date: 2018-06-01
forum: Networking &amp; Wireless
---

### Post by leslie4 on 2018-06-01
I've found several references for installing and configuring LDAP under Ubuntu 16.04 LTS, but they all consist of running

```
sudo apt-get -y install libnss-ldap libpam-ldap ldap-utils nscd
```

and then answering the interactive prompts. (One example is [https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/configure-ldap-client-on-ubuntu-16-04-debian-8.html](https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/configure-ldap-client-on-ubuntu-16-04-debian-8.html))

I would like to come up with a shell script that would automate the process.  Are there no command-line parameters that can be specified during the apt-get install?  If not, could I create the LDAP configuration files ahead of time, and have the apt-get install use them instead of prompting me for the values?  Thanks in advance for all who respond.

---

### Post by TheFu on 2018-06-01
I would use **ansible**, but there are 50 other methods, including making a script.  Ansible's APT package tells the installer it isn't interactive, so their won't be any prompts. 

APT is for installing and removing packages.  The packages themselves have the pre-install and post-install scripting, so APT can't pass anything through.  I think there is an option for one of the apt tools not to run the post-install config script. You can place any config files into the correct locations if you like.  They should be seen and used.  Any config mistakes will break the subsystem for the program, but no worse than normal breakage from a bad config file.

Anyway, hope these are ideas you find useful.

---

### Post by leslie4 on 2018-06-04
Thanks for the suggestion.  After doing some further research, I think I am going to experiment with **debconf-get-selections** and **debconf-set-selections**, based on this link: [https://stackoverflow.com/questions/702248/how-can-i-automate-dpkg-apt-get](https://stackoverflow.com/questions/702248/how-can-i-automate-dpkg-apt-get)

---

