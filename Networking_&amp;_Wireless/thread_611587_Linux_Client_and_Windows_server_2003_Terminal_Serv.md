---
title: "Linux Client and Windows server 2003 Terminal Services License Issue"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by Tom Haskell on 2007-11-13
Hi there,
I have been searching for almost a week to figure out where the Terminal Services Licensing information is saved or located if i were to use Linux based client and ofcourse windows server 2003.
Since Linux does not deal with registries which is the case of windows client, I wonder where Linux client will save the above info(terminal services license info, TSCALs)of the users?
I have spent an enormous amount of time trying to figure out this thing in the internet, so far I have not gotten any specific answer for this.
Tom

---

### Post by Fire_Chief on 2007-11-13
The clients do not save info about the TSCALs they use on the server. The server is solely responsible for tracking and allocating the CALs.

---

