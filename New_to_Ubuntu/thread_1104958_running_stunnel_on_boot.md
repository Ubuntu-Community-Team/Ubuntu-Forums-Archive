---
title: "running stunnel on boot"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by enboig on 2009-03-24
I have installed ubuntu 8.04 server and added stunnel.
If I run it from console it works perfectly, when trying "/etc/init.d/stunnel4 start" nothing happens.

Any hint? thanks.

---

### Post by finer recliner on 2009-03-24
1) maybe an obvious question, but you're running "/etc/init.d/stunnel4 start" with "sudo" right?


2) after running the command, "sudo /etc/init.d/stunnel4 start", try typing "ps aux | grep stunnel". This command will search for all running processes titled "stunnel". You should get back at least one result to confirm that stunnel is running (if you see a process called "grep stunnel" -- ignore it, its the just the process that was created for your search of stunnel ;))

---

### Post by enboig on 2009-03-24
> **finer recliner said:**
> 1) maybe an obvious question, but you're running "/etc/init.d/stunnel4 start" with "sudo" right?


I made "sudo bash" and "passwd" so I am doing all of this as root.

> **finer recliner said:**
> 2) after running the command, "sudo /etc/init.d/stunnel4 start", try typing "ps aux | grep stunnel". This command will search for all running processes titled "stunnel". You should get back at least one result to confirm that stunnel is running (if you see a process called "grep stunnel" -- ignore it, its the just the process that was created for your search of stunnel ;))

after "stunnel4 start" I run "ps -A | grep stunnel" which should be de same and no process is there.

---

