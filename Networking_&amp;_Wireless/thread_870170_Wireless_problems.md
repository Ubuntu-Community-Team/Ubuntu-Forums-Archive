---
title: "Wireless problems"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by romangradel on 2008-07-25
Hi,
I just got my dell m13330 and even though I get a signal, I can't connect to the internet. I am new to Ubuntu and have the 8.04 installed. Could someone please help me connect?

---

### Post by PinkFloyd102489 on 2008-07-25
Open a terminal, input these commands, and post the output here.


```
lspci
```
```
lshw -C Network
```

---

### Post by romangradel on 2008-07-25
thank you for your help, but it did not work could you give me a more detailed explanation?

thanks

---

### Post by northern lights on 2008-07-25
That was not meant to fix your issue right away, rather give more detailed info on your specs & current state of network devices.

Run ```
sudo lshw -C network
``` again. Now mark the text below that command, i.e.
```
user@host:~$sudo lshw -C network
[sudo] password for user
.
.
.
user@host:~$
```what is represented by the dots. When marked, press "Ctrl+Shift+C", switch to this forum and in a new reply to this thread press "Ctrl+V". Post.

---

