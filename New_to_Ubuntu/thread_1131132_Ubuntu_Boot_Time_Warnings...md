---
title: "Ubuntu Boot Time Warnings.."
date: 2009-04-20
forum: New to Ubuntu
---

### Post by scrypt on 2009-04-20
HI

When I Boot up my Ubuntu Laptop.
I can see there a four warning Messages. But they disappear to quickly for me to read what the warnings are.

There are also five different warning messages when I close down Ubuntu.

I get a bit more time to read the five warning messages at shutdown and they are:-

HAPM WARNING   "= It shows this line five times."

I am hoping The Warnings that flash up at boot time are the same as the warnings that show at Shutdown.

Is there a way to check what these warning messages are from inside Ubuntu once I have Started up?

Also What does "HAPM Warning" Mean?

Is it anything I should be worried about??

Thank-you in advance

---

### Post by Cypher on 2009-04-20
Open up a terminal (Applications->Accessories->Terminal) and type "dmesg" this will get you all of the log messages since booting up thus far.

Depending on when you run this command after bootup, you should see the "Loading Linux Kernel" line which is the first one. You can also look at /var/log/messages for a log of ALL messages across all boots..

---

### Post by scrypt on 2009-04-20
Thank's for your quick reply.

What is the best way to view the /var/log/messages?

How do I do this?

---

### Post by Rinzwind on 2009-04-20
=> system / admin / log file viewer
is the easiest way.

---

