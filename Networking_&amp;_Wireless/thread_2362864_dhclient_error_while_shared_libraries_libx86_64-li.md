---
title: "dhclient error while shared libraries: /lib/x86_64-linux-gnu/libisc-export.so.160"
date: 2017-06-02
forum: Networking &amp; Wireless
---

### Post by Raymond Day on 2017-06-02
I got a UP2 board and Installed **ubuntu-16.04.2-server-amd64.iso** it works very good. Updated it and installed "apt install lamp-server^" Then Webmin. Webmin works super fast on it and it said for the updates have to reboot. I did and then can't get on it's Ethernet any more.

So now I can only use the keyboard on it's screen.

The error I get is this:

**dhclient error while shared libraries: /lib/x86_64-linux-gnu/libisc-export.so.160: invalid ELF header**

After I do a **dhclient emp2s0**

Just don't know that fix for this. Any one know. I can't do any apt install because can't get on line.

-Raymond Day

---

### Post by Raymond Day on 2017-06-03
Got it fixed by copying that /lib/x86_64-linux-gnu/libisc-export.so.160 file to a SD card from another Ubuntu server and put it in the same place as this server.

It gets a IP again now.

Not sure why this new install with updates deleted that file?

-Raymond Day

---

