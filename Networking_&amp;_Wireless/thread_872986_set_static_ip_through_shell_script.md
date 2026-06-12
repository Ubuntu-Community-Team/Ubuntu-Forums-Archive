---
title: "set static ip through shell script"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by brdtt12 on 2008-07-28
I work for a company that has multiple offsite computers that check into a server at our local office. They check in and update content using shell scripts that run at pre-specified times throughout the day.
One of these computers is currently not checking in. This means it is unable to connect to the internet. There has been no change with the network it is on, the only cause for this problem is when it was loaded before shipment it must have been set with the incorrect network settings.
Each computer is setup with a static ip and is not accessible from outside the network.
What I am looking for is a script I can use to log into the network setting(password required) and set a new static ip, subnet mask, gateway address, and dns numbers.
I have found various scripts that use 'expect' and 'send' but have not had any luck getting anything to work. Any help or direction would be greatly appreciated. Also if it matters I have Ubuntu 7.04 installed.
Thanks in advance.

---

### Post by argail1980 on 2008-07-28
but how do you plan to connect to that computer, if it has the network misconfigured? does it only have the wrong IP?

The only possibility to set up the internet connection is from that computer, not from outside.

To execute any script on that computer, you could write a bash script on that machine (as root), chmod to make it executable by anyone and set the suid bit (the script can then be run with root privileges by ohter users). Then you can SSH to the machine and run the script. ```
ssh user@host /path/to/that/script
```

But again, this only works if the machine has an internet connection

---

