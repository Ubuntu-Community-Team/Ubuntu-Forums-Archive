---
title: "Interruptions in wireless, how do I debug it?"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by Necreia on 2007-07-01
Hello, a small description of the problem if this is something one has solved before:  Between every 4-6 minutes I get about a 3-5 second 'interruption' which causes data to halt for a bit.  Causes problems in online games.

Anyhow, I'm new to Linux.  What are some of the tools/methods that I can use to try to track down what's causing this?

---

### Post by Sendervictorius on 2007-07-01
One way to track down the problem is to use packet sniffing see what your network is doing. Load Ethereal (Wireshark) onto your computer from synaptic and run it. (Downside of this method is you might find you need to learn a bit about ethernet packets). You will easily be able to see if you are getting periods where packets are incomplete. Could be noise, or problems with your cabling (or wireless if that is how you are connecting)

What might help is if you can post details of your setup to the forum: e.g. your ethernet or wireless card (lspci command gives info)

---

### Post by Necreia on 2007-07-01
Thanks, that tool will be perfect.  I've learned a bit about ethernet packets so let's see what it says.

My card is:
05:01.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

---

### Post by Necreia on 2007-07-02
So far I see no patterns about the delays.  Further to note is that I get this behavior with Windows Vista, but NOT Windows XP.

Also, I have moved in the meantime and have changed ISP's.

Very strange, but I'm going to lean towards drivers at the moment.

---

