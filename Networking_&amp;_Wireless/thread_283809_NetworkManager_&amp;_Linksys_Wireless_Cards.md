---
title: "NetworkManager &amp; Linksys Wireless Cards"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by NetworkGuy on 2006-10-24
Hi All,

Has anyone ever gotten NetworkManager to work with an ACX111 chipset wireless card?

I had to follow the how-tos in the forums and make sure the kernel loads the 1.2.1.34 firmware else the card doesn't work right.

My card is working fine when manually setup through /etc/network/interfaces however when I try to install and use NetworkManager, multiple wireless networks are displayed but I can not connect to any of them, including mine.

I remarked out everything in /etc/network/interfaces except the lo adapter. 

Thinking it was a WEP issue, I've turned that off on the router, but I still can not make a wireless connection to my network.

I really want to get this to work, but I'm frustrated trying to figure out why it isn't.

I'm attaching the messages from /var/log/messages that I got while trying to attach to my network.

Any ideas anyone?

---

### Post by Guierrmo on 2006-10-24
I have a linksys wpc54g v2 which uses the acx111 chipset.

Check out [http://www.xeno-genesis.com/~jpierre/network-manager-0.6.3/](http://www.xeno-genesis.com/~jpierre/network-manager-0.6.3/)

I downloaded network manager 6.3 from there.  You need to download a couple other packages to satisfy the deppendices(ap?), which are available at the same site.

Check out the bug at [https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/42504](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/42504)

it seems like a silly bug, but to my knowledge they haven't release a fix yet.

oh yea, I forgot to mention, I downloaded the latest version of ndiswrapper.  Not sure if it matters.

---

### Post by NetworkGuy on 2006-10-25
I will take a look into this.

One question for you..  Are you using ndiswrapper in your install.   I would rather keep the machine pure linux and not introduce Windows drivers if I don't have to.

---

### Post by Guierrmo on 2006-10-25
Unfortunately the current acx111 linux driver doesn't work with wpa(not sure about wep), so i'm forced to use ndiswrapper.

---

### Post by NetworkGuy on 2006-10-25
Ok,  I've haven't tackled WPA yet, but I did see where NetworkManager does have trouble connecting to unencrypted networks too.   

Hmmm. May need to look into putting WEP back on and trying this again..

---

