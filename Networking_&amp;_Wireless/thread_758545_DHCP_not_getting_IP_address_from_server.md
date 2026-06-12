---
title: "DHCP not getting IP address from server"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by venkatat on 2008-04-18
hi, 

My NIC is not able to get the IP from dhcp server. same card is working fine windows ( i have a dual boot with XP) . I will explain my findings below.

I will get my IP address in the range of 123.XXX.XXX.XXX ( IPv4) usually. But one more interface is showing in network interface list with alias avahi. when i click on this one , error message coming up as no such interface.... This aliased device is gettting ip address 169.XXX.. , that the normal eth0 should get.


i found a work around for this , REMOVING the gnome-network-manager and avahi-autoipd packages.
this trick is working only in feisty not in Gutsy again. When newly installed gutsy the same avahi problem coming up.  what is this bloody  avahi....

Is it a bug....due to this no internet connectivity to my system...i have to reboot to windows to access the internet.

:(

---

### Post by superprash2003 on 2008-04-18
have you tried going to System->administration->Network then selecting wired connection(eth0) and then selecting Automatically assign ip (DHCP)

---

### Post by venkatat on 2008-04-18
yes , i did the same.. some times when i installed the fiesty or gutsy first time internet is coming. after reboot avahi aliased eth0 entry is also showing in the list. i can configure only the eth0 entry details ...roaming mode chek box uncheked and made it to dhcp.

done /etc/init.d/networking restart

DHCPDISCOVER not able to discover any thing. please help me. if boot into windows the i am able to get the internet . 

This is show stopper to my work..i damn need internet. though i can use internet from windows but i don't want to coz of viruses. if this problem us fixed , i will remove windows from my system....


Thanks in adavace..
venkat

---

### Post by superprash2003 on 2008-04-19
please go to the terminal and type ifconfig and post results here

---

