---
title: "Easy internet sharing needed"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by lunarcloud on 2007-11-28
What we need is for network-manager to have an integrated internet sharing configuration using iptables (possibly aided by firestarter), wide-dhcpv6-relay and dhcp3-relay in order to share 

a. from wireless to wired
b. wireless to wireless (two cards, yes)
c. wired to wireless

The wireless card should be set up in master mode first, and upon failure should switch to ad-hoc mode.

It took me hours to set this thing up wired to wireless using an ndiswrapper supported card. Why must we be a step behind apple on this one?

Anyone like this idea?

---

### Post by lunarcloud on 2007-11-29
****... fyi, it is now NOT working for some reason...

---

### Post by dmizer on 2007-11-29
given the proliferation of cheap and preferable alternatives, i really feel that integrating network manager with iptables is neither necessary nor wise.

connection sharing is a throwback to the days where you had a dedicated phone line for dial up internet access but all computers were networked with patch cables (or later, ethernet) for better/faster communication to the mainframe/server.  in those cases, higher speed internal network hardware could not communicate directly with the internet connection unless a server acted as a relay.

this is not to say that connection sharing isn't needed anymore, but home applications (where a gui interface would be desirable) should be few and far between.

i also think that it would be extremely unsafe to have network manager integrated with firewall settings.  so, while i marked "not important" what i really would have liked to mark would be "dangerous" or "fool hardy"

this is my opinion, but for the most part, i think people reach to connection sharing to resolve a network architecture problem simply because they know about it and not because it's the best (or even cheapest) solution.

here's a fairly simple howto using cli: [https://help.ubuntu.com/community/InternetConnectionSharing?](https://help.ubuntu.com/community/InternetConnectionSharing?)

a fairly simple gui alternative is firestarter

---

