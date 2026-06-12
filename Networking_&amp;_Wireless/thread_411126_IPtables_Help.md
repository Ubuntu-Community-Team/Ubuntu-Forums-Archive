---
title: "IPtables Help"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by The_night on 2007-04-16
I have been trying to wrap my head around IPtables for a while now, and I am having a difficult time.  Basically I want to create a script that blocks ALL ip addresses Except for a range of ip addresses, and any other ip addresses I might need to enable along the way.  Can anyone help me with this?!:confused:

---

### Post by andguent on 2007-04-16
Most people when starting into firewalling go with a helper package to get started. Basically any firewalling package just runs iptables, so you end up with the same result.

Firestarter is a popular GUI tool for getting firewalling configured the way you want. Read more here: [http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

sudo apt-get install firestarter


If you are going command line and prefer it that way, I highly recommend learning shorewall. It has numerous config files, but if you can learn 4-5 of them, you are set. I find it extremely easy to understand how a network is configured if reading through shorewall configs. If you go that route I can definitely help you out. Shorewall.net is the primary documentation, but I rarely found it easy to read myself.

sudo apt-get install shorewall

---

