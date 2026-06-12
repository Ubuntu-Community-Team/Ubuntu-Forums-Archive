---
title: "Where is NetworkManager log"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by Endymion Zhang on 2008-06-29
Can anyone tell me where is NetworkManager log file?
(I haven't found it in /var/log/ directory.)

Thanks a lot!

---

### Post by Endymion Zhang on 2008-06-29
Sorry, I've found it just now, it's daemon.log.

---

### Post by atrus on 2009-11-18
daemon.log also has a lot of other information... is there a way to get just network-manager logs?

---

### Post by dirakx on 2009-12-28
you can do something like cat /var/log/daemon.log | grep NetworkManager,

hth

---

### Post by another_sam on 2011-12-04
great daemon.log does not exist anymore. (i am trying to found why I can't connect to a mobile broadband connection.)

you know when you search for linux knowledge on the web and you get results but they don't work. why this pain.

---

### Post by matt_symes on 2011-12-04
Hi

> **another_sam said:**
> great daemon.log does not exist anymore. (i am trying to found why I can't connect to a mobile broadband connection.)

you know when you search for linux knowledge on the web and you get results but they don't work. why this pain.

This is an old, old thread. You *really* should start a new thread.

I expect this thread to be closed very soon :)

In the meantime, take a look in /var/log/syslog

```
grep -i networkmanager /var/log/syslog
``````
matthew@matthew-Aspire-7540:~$ grep -i networkmanager /var/log/syslog | tail -n2
Dec  4 15:23:20 matthew-Aspire-7540 NetworkManager[1126]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Dec  4 15:23:20 matthew-Aspire-7540 NetworkManager[1126]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
matthew@matthew-Aspire-7540:~$ 
```Kind regards

---

