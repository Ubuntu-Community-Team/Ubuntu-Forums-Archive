---
title: "measuring traffic volume for individual router users"
date: 2017-07-04
forum: Networking &amp; Wireless
---

### Post by ktat on 2017-07-04
Hi,

I have been trying to find a program that measures data transferred and received over the course of a month.  vnstat does this well, however it only measures the data going through my laptops wifi.

I would like to measure the traffic going through my router (NetCom Wireless, Product Class: 	NF10W, Software Version: 	NF10W.NC.AU-R5B016.EN) and be able to break that down to specific devices.

I am using Ubuntu 17.04 on Dell inspiron 15.

Thank you.

---

### Post by TheFu on 2017-07-04
[snmp]("https://en.wikipedia.org/wiki/Simple_Network_Management_Protocol") on the router. If the router doesn't support it, get a better router.
There must be 50 sets of monitoring software that support SNMP, but I don't think any are for non-admin types.  OpenNMS is one.

Some routers have bandwidth use graphs built into their interface. I've only seen them for a subnet or VLAN, not on a device-by-device basis.

---

