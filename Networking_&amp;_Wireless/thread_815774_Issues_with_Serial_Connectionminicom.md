---
title: "Issues with Serial Connection/minicom"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by creedog on 2008-06-01
Not sure if this is the correct place to even post this but I am desperate and frustrated.


I am trying to use minicom to connect to a brocade silkworm 3850 San switch. The connection is 1152000 none/8/none/1 via null modem cable (using null connector to Ethernet to serial) this is direct from the manual. I am just getting jibberish. Anyone know of a better way then to troubleshoot serial connections other than just trying every combo of every adapter that I have.There is nothing on the internet regarding troubleshooting silkworm consoles.

Also, I am able to connect to my Cisco Catalyst 1900 with serial to roll-over, but the thing's internal battery must have died as it says there is no firmware installed. Anyone know where I can get firmware from this thing that I do not have to pay $300 for?

Thanks.

---

### Post by gradedcheese on 2008-06-02
If you're getting jibberish, your baud rate is wrong but otherwise you're probably very close to having it work.  Just try all the baud rates available one by one until it works?  

Control+a, then o then select 'serial port setup', then use option 'e' to set a new baud rate.  Perhaps 115.2k isn't actually what the device is using.

---

