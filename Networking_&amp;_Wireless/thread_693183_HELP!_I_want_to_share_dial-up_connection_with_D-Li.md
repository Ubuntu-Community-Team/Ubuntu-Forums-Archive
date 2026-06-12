---
title: "HELP! I want to share dial-up connection with D-Link Wired Router!"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by s3a on 2008-02-10
How do I share internet connection with wired router? More specifically, a dial-up one?

Thanks in advance!

---

### Post by dmizer on 2008-02-10
here's what you will need:
1) an ubuntu computer with both a dial up modem and a network card.
2) patience.

here's how to configure your ubuntu computer for internet connection sharing (be sure to read the whole howto before trying to follow it).
[https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28connection%29%7C%28internet%29%7C%28sharing%29](https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28connection%29%7C%28internet%29%7C%28sharing%29)

(note: in the above howto, "ppp interface" = dial up connection)

you will also have to configure your router to cooperate with your setup.  this means that your router will need to be configured as a hub, not a router, and your local network will be static ip unless you configure your ubuntu computer as a dhcp server.

good luck, post here with questions.

---

### Post by s3a on 2008-02-15
Thank you! I almost there...I just do not understand the last step...can you like elaborate on it?

What I don't understand:

#

Add gateways, ask the server maintainer for the DNS and include then on /etc/resolv.conf such as:

<nameserver> <ipaddress>

---

### Post by s3a on 2008-02-15
I get the ip part butr not the nameserver...what's a nameserver? I followed exactly the instructions so would that mean there is no name if thats wat a nameserver is?

---

