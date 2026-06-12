---
title: "NIC recieving, but not sending anything."
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by hotstovejer on 2006-10-14
I seem to have a problem with a machine I just built. The nic shows up, and it shows that it is recieving info, but it doesn't send anything. I ping, and get nothing. (Unknown host) I have a straight run to my modem (no router), and the cable that doesn't work on that machine works on this one. I tried putting in the DNS that I have on my machine, and nothing still. Any ideas?

---

### Post by coastdweller on 2006-10-14
> **hotstovejer said:**
> I seem to have a problem with a machine I just built. The nic shows up, and it shows that it is recieving info, but it doesn't send anything. I ping, and get nothing. (Unknown host) I have a straight run to my modem (no router), and the cable that doesn't work on that machine works on this one. I tried putting in the DNS that I have on my machine, and nothing still. Any ideas?

post the contents of your /etc/network/interfaces file

> sudo pico /etc/network/interfaces

Tell us more about the "modem" and what type of connection it is.

---

