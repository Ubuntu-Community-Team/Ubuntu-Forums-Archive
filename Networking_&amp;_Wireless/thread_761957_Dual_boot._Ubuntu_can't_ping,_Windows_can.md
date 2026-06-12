---
title: "Dual boot. Ubuntu can't ping, Windows can"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2008-04-21
Hi all,

got a good one for the experts. Dual boot machine on a wireless network. In windows, can happily ping and connect to my Vista (from work) laptop.

In Ubuntu - nada. Ping won't work, and therefore networking (file sharing etc won't).

HOWEVER, after trying to ping, "arp -a" reveals the correct MAC of teh laptop. So somethings communicatiing.

Network settings (router and subnets) are correct. The Dual-boot has a fixed IP, to eliminate any DHCP problems.

This is starting to be a serious problem. I was hoping to convince my boss to run some form of Linux on the laptop (who wants Vista), but I can't make a case for it if I can't run it at home .... :-(

any help gratefully received

---

### Post by sillyxone on 2008-04-21
can you specify more to make sure you do have connection under Ubuntu such as can you ping the router, does your wireless have WEP/WPA, can you browse the internet?

I'm asking because usually with DHCP, you can tell that you are communicating with wireless router if you have an legitimate IP, but with static IP, it's hard to tell.

---

