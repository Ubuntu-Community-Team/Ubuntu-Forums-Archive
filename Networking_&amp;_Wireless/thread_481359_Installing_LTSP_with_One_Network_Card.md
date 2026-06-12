---
title: "Installing LTSP with One Network Card"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by dmarte on 2007-06-22
I am new to the Linux/Edubuntu World. So here it goes... Is it possible to install the LTSP with one network Card? Assuming it is possible and that the server IP address is 192.168.1.4 what changes I have to make on the dhcp.conf so the future thinclients boot from that server? Thanks in adance for any help you can provide.

---

### Post by zixxer on 2007-06-22
yes it is. i am currently doing that with 3 of my servers. they feed the pxe booting clients and all windows workstations get their static dhcp leases from it, all works 100%

BUT...since your posting here i bet you are interested in doing this with ubuntu/edubuntu/xubuntu.....i am currently (as in right this second) working on LTSP5 with 7.04 and its failing miserably. the dhcpd.conf file to edit lives in /etc/ltsp/. i am having a very hard time getting workstations to boot with ltsp5 on 7.04....whereas i could be considered a veteran for the official k12 version of ltsp. ill post if i ever figure out whats wrong.....anyone have any ideas? we need a good up to date how-to for 7.04 (all flavors) to get ltsp working with 1/2 nics. i can post my dhcpd.conf from my single nic fedora servers if you want it, but it wont apply to ubuntu, at least not easily i guess.

---

