---
title: "IM monitoring tools"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by daveloh on 2008-05-12
is thr any IM tracking or monitoring tools i can use to track network users IM chat log and wat IM tool they use???

thr is serious misuse of IM in my office.....management ask to collect evidence~~~~

---

### Post by lemming465 on 2008-05-19
First, what kind of acceptable use policy did the users sign, if any, and what are the wiretapping laws in your jurisdiction?  You may want the mandate from management in writing.  (The first step in any network investigation is not breaking any laws, and the "get out of jail free" card for the the investigator :-)

Next question, how much control do you have over the PC's and the network?  You need one or the other.  If you have control of the PC's, you can install logging software on them.  Otherwise you have to be able to capture the network traffic.  If you are on a switched network, which is typical, you either need something like a [Fluke hardware network tap]("http://www.flukenetworks.com/fnet/en-us/products/Tap+and+Switch+Solutions/MOA.htm?categorycode=LANH") to replicate the uplink traffic to your ISP, or if the switches are smart enough, your equivalent of the Cisco *monitor session* command to replicate port traffic to your network analyzer.  A quick and dirty analyzer is any Linux box running wireshark.  If you can pick out an IM session, the Analyze option to "follow TCP stream" is your friend.

A lot is going to depend on what protocols are being used for IM.  E.g. many Jabber servers will use encryption, which would make monitoring a lot harder unless you have access to the hosts.

If it's looking like too much work to snoop on the traffic, maybe you could just tighten up the egress filtering on the firewall and force all outbound traffic through a proxy server.

---

### Post by tamoneya on 2008-05-19
im going to second the wireshark recommendation.  Unless your office is very large wireshark should be able to solve this problem easily.

---

