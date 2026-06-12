---
title: "VPN Relakks on IBEX"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by andy17 on 2008-11-02
Hi guys,

I've been trying to get RELAKKS VPN working on the new Network Manager GUI but couldn't...

anyway it worked on Hardy!

any suggestions???

---

### Post by Takano on 2008-11-06
I have similar problem, any solution?

---

### Post by Ledger on 2008-11-12
Exactly the same problem here. Had it working in Hardy, but won't work in Intrepid. A solution would be hugely appreciated :)

---

### Post by AlbertVeli on 2008-11-15
Hi!

I had the same problem but managed to solve it after some googling on the error messages from /var/log/daemon.log.

I added the following line to */etc/apt/sources.list*

**deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main**

And ran *apt-get update* followed by *apt-get upgrade*.

Actually id didn't work on the first try, but on the second try. Don't give up if it doesn't work the first time and check daemon.log. You can run *tail -f /var/log/daemon.log* to follow what is happening.

---

### Post by Ledger on 2008-11-19
Now it's working :)

What i did:
added


deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main #network-manger

To the end of /etc/apt/sources.list

Then:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install network-manager-pptp

Then I connection to the vpn in the connection manager. I did also disable all authentication methods except of MSCHAPv2..

---

### Post by Ledger on 2008-12-03
Anyone now how to automaticaly reconnect? Relakks disconnects sometimes, and i want it to reconnect and never use the connection without VPN.

---

### Post by Martje_001 on 2008-12-04
Could you share your configuration, please?

---

### Post by BeastlyKings on 2009-02-11
I would also like to know how to set up Network manager to automatically reconnect the VPN, and only allow traffic when the VPN is active.
I don't know what you'd need to know about my configuration. I'm running 8.10 with Relakks as my VPN, if that helps.
Any ideas anyone?

---

