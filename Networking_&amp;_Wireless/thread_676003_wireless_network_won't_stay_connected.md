---
title: "wireless network won't stay connected"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by Kevin Fischer on 2008-01-23
I'm running Gutsy on my laptop with a broadcom wireless card.

I have the constant problem that, after being connected to a wireless network for more than a few minutes, I lose my connection. The network still shows up as being connected, and if I disconnect and reconnect everything is fine for another minute.

This is different from the other similar thread b/c there the connection actually was shown to be lost and no networks showed up in the network manager.

Any ideas? I'll happily provide any information.

---

### Post by bettyhills on 2008-01-23
I know _nothing_, but was researching a similar problem recently and found a suggestion to **turn off SNMP authentication** as unnecessary _if_ you have set up security on your wireless router using a key.  It said SNMP authentification sends out a query every few minutes that can interrupt the wireless connection.  

I do not know how to turn SNMP authentification off under Ubuntu.

---

### Post by Kevin Fischer on 2008-01-23
This is a campus network, so no wireless security, unfortunately.

Thanks for the help, though.

Any other thoughts?

---

### Post by bettyhills on 2008-01-23
The other thing to look at is power saving features.  Try turning all of them off.  Look at Power Schemes, Display adapter, Screen saver, Hard drive, and more...

Make sure nothing is "going to sleep" or on standby after a period of inactivity.

Can you find out if SNMP authentification is required on the campus network?  If not, try turning it off.

I hope that someone knowledgeable jumps in...

---

