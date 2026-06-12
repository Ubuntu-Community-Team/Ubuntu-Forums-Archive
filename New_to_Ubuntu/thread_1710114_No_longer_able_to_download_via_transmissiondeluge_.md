---
title: "No longer able to download via transmission/deluge and no longer able to send email.."
date: 2011-03-19
forum: New to Ubuntu
---

### Post by daggerdawg on 2011-03-19
Hi,

Yesterday I decided to upgrade to ubuntu 10.10 and encounter all kinds of problems...after several hours of trying I decided to restore my system back to 10.04.  During both the upgrade and now on fresh install of 10.10 I am unable to download via deluge and transmission.  I am also unable to send email via thunderbird and evolution.  I have install ufw and unstalled and then reinstalled it and opened the ports for deluge.  I have tried almost all topics on getting thunderbird and evolution working.  I am still unable to do so.  Any help or information would be great!!

---

### Post by quirks on 2011-03-19
- Is your Internet connection working in general? E.g., can you browse websites or access other stuff on the Internet other than e-mail via Thunderbird/Evolution or file sharing via Transmission?
- If nothing works on your Ubuntu machine, have you tried accessing the Internet from a different PC?
- Since you mention that you changed your firewall configuration, can you show me the output of this command (prints the firewall config):
```
sudo iptables -nvL
```

---

