---
title: "Time Synchronise among network computers"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by Guruprasad on 2011-04-29
I have 4 computers on network. 

Is it possible to synchronize the time over network using any software?

---

### Post by HermanAB on 2011-04-29
Well, the 'correct' way is to use the Network Time Protocol.  You can either set up your own NTP server or let all machines sync against a global time server.

Otherwise, you could go the DIY way and make a script that runs the date command over SSH for example.

---

