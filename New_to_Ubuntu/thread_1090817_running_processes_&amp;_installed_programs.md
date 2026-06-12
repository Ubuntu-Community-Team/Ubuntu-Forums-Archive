---
title: "running processes &amp; installed programs"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by serros88 on 2009-03-08
Hi,

I just checked whether Clamav (anti-virus) et Firestarter (firewall) are running on my system 8.10. I opened Monitor System but cannot see these programs running!!!??? 
Can you explain where to check the running programs.

Another question on programs:
In Synaptics I can see I have 1335 programs installed. Well, where can I see the list of installed programs and how to execute (coming from Windows world, have to change my habits and skills).

Txs,
serros

---

### Post by markjensen on 2009-03-08
Check any particular service's status:
**chkconfig | grep clamav** (as an example)

List all installed packages:
**dpkg --list**

What do you mean "how to execute"?  Are you having problems running an app you installed?   If you have a daemon (service) that you want running, you can do it from your services manager app, or even directly from the command line, like:
**sudo service boinc-client start**

---

### Post by blueridgedog on 2009-03-08
Running programs:

```
ps ax
```

---

### Post by snova on 2009-03-08
Firestarter is not a firewall, but merely a tool to configure it. The firewall is not something you can remove or disable, and it does not run as a process.

Regarding ClamAV, besides the fact that it's probably not going to be of much use, I don't know.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

