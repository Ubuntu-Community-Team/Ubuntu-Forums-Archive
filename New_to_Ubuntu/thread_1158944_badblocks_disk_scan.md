---
title: "badblocks disk scan"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by bongoceroblue on 2009-05-14
I'am running a 9.04 Server and used the badblocks -vsn command to scan a usb external h.d. but the scan takes to long and i don't know how to stop it.What command can i use, help anyone?

---

### Post by Pjukern on 2009-05-24
in the same terminal press ctrl+c.

or if you are in another terminal, use ps aux | grep badblocks to get the pid. 
then stop it with the "kill" command.

---

