---
title: "nmap:- Strange read error"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by brilyant on 2007-08-10
Ubuntu 7.04

eth0 is configured as 10.0.0.7/8, and plugged directly to a D-link printer server

After entering:      nmap -n -sP 10.0.0.0/8      there is a pause, then error messages stream continuously down the screen:

     Strange read error from 10.0.4.x: Transport endpoint is not connected

where x cycles from 0 to 39


Using eth0 configured as 192.168.y..z /16 , nmap successfully scanned  64k IP addresses.


Can anyone explain what the message means?

---

