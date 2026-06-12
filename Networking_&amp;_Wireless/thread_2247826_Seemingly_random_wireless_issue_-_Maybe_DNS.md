---
title: "Seemingly random wireless issue - Maybe DNS?"
date: 2014-10-10
forum: Networking &amp; Wireless
---

### Post by mark-lamorey on 2014-10-10
Hi all,
I have a new 14.04 install on a new Lenovo M73T.
Everything works fine until it does not - sometimes after 10-15 minutes of use other times only after a hibernate.
The problem is that I lose my internet - I connect through wireless and initially it still shows me as connected but I cannot ping anything (google, yahoo, etc...).
I have ran the wireless script right after a reboot and once after the problem starts.
I see the differences (TKDIFF), but I have not used linux in many years and never got that proficient - any thoughts / advice appreciated.
[ATTACH]257112[/ATTACH]  
[ATTACH]257113[/ATTACH]
The ...good.txt.gz file has good connectivity.

There are two major differences - in the bad file I have the line :     no-auto-default=<MAC 'eth0' [IF]>,
and I have no channel occupancy data in the 'iwlist''

Do I just need to find the secret restart command order to get this going again - I have tried the commands in the next post

Appreciate any direction

---

### Post by mark-lamorey on 2014-10-10
One other thing - I remain connected to my wireless node, but have no internet access. 
If I use the below:
sudo service network-manager restart
... or ...
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up

I lose my connection (obviously), but then I cannot reconnect to my wireless

---

### Post by mark-lamorey on 2014-10-12
How do I set this thread to solved ?
 - while I still have the problem it is very clearly not a wireless issue. Looks more like DNS , DHCP, and or my router or modem.
Need to debug, but would start new thread.

---

### Post by jeremy31 on 2014-10-12
> **mark-lamorey said:**
> How do I set this thread to solved ?
 - while I still have the problem it is very clearly not a wireless issue. Looks more like DNS , DHCP, and or my router or modem.
Need to debug, but would start new thread.

Just above your first post on the right side it says "thread tools" and you can use that to mark as solved

Maybe you can find clues to the issue with ```
cat /var/log/syslog | grep -i dhcp
``` after you lose internet connectivity

---

