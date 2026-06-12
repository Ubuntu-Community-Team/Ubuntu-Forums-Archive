---
title: "asymetric ping behaviour"
date: 2019-12-29
forum: Networking &amp; Wireless
---

### Post by ulrichmuc2 on 2019-12-29
There are two hosts in my network, A and B. If I ping A from B, I get "Destination Host Unreachable".
Ping from A to B succeeds.
After the successful ping from A to B,  ping from B to A succeeds too, but only as long as B does not loose the connection (by going to sleep) and reactivates the connection after resume.
Host A is a Raspberry Pi running raspian, host B a PC running ubuntu 18.04
This behaviour is new, since I installed alsamixer on the Pi, but I doubt that there is a connection.
When the ping doesn't work, also A is not seen by Angry IP Scanner running on B, after the successful reverse ping it IS seen.
Any ideas what causes this weird behaviour and how to fix it?

---

### Post by TheFu on 2019-12-30
What is the network topology?  If same subnet, then only ethernet and ARP tables are being used.
Ping by IP or hostname?  
Is /etc/hosts setup on both systems so they know about each other?
Any wifi involved?
Is IPv6 enabled or not?

---

### Post by ulrichmuc2 on 2020-01-02
> **TheFu said:**
> What is the network topology?  If same subnet, then only ethernet and ARP tables are being used.
Ping by IP or hostname?  
Is /etc/hosts setup on both systems so they know about each other?
Any wifi involved?
Is IPv6 enabled or not?

Both computers are in the same subnet:   192.168.2.*
/etc/hosts entries are correct, ping by IP and by hostname makes no difference.
Connections are via wlan.
IPv6 enabled? How do I check?

It seems, the behaviour described appeared after using rdesktop for connecting once. Rebooting fixed it - should I have tried earlier.

---

### Post by ulrichmuc on 2020-01-14
I now see that rdesktop was NOT the cause and rebooting fixes the problem only temporarily.
After a while (maybe some days) host A can again not be accessed from host B, though both are connected to the network.
Pinging B from A fixes the problem.
Interestingly, the first ping-reply takes about 2 seconds, the following ones about 6 milliseconds.
Any ideas?

---

