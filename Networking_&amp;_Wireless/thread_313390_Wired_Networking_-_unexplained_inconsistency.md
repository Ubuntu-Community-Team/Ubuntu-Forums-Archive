---
title: "Wired Networking - unexplained inconsistency"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by Ububurns on 2006-12-05
I have one computer that dials up to the internet.
It shares the internet using Firestarter to a client (eth0).
The client computer recieves its IP using DHCP, from the first.

ie:

MODEM
  |
Computer1
  |
Client(a or b)


However:

If I plug that end into client a, it can reach the internet.
If I plug that end into client b, the internet doesn't work.  Yet it can still ping the computer that dials up to the internet, and recieves its IP address from it.

Both computers have working network cards, and run U6.10.

---

### Post by DaveBorealis on 2006-12-06
> **Ububurns said:**
> 
If I plug that end into client a, it can reach the internet.
If I plug that end into client b, the internet doesn't work.  Yet it can still ping the computer that dials up to the internet, and recieves its IP address from it.

Hello,

Just a couple questions:
Does client a always work, but client b never works?
And have you tried pinging someplace on the internet using only an IP address? ```
ping -c1 72.14.207.99
``` (Which is for google.com)

Dave

---

