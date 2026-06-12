---
title: "Howto: Shutting Down a Windows Box from Ubuntu"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by lp.descamps on 2008-10-05
I've been looking for an easy answer but couldn't find any.
Here is what I'm doing:

I'm using telnet.
So start the service on the windows box.
run services.msc->telnet
set telnet to auto and start the service.

here is the script I've done
#################################
#!/bin/sh
(echo 
sleep 2
echo "**username**\r"
sleep 2
echo "**password**\r"
sleep 2
echo "shutdown -s -f -t 0\r"
sleep 2
echo exit) | telnet **windowsbox**
#################################

i know nothing secure, nothing clever but easy

I hope this might help some of you

---

