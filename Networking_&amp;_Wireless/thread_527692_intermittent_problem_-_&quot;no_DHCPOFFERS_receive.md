---
title: "intermittent problem - &quot;no DHCPOFFERS received&quot; (r8169 - Biostar TF7050-M2)"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by AlpineCarver on 2007-08-16
[repost from HW forum; i'm sure this is a better place to post this]

i'm having intermittent DHCP problems with my Biostar TF7050-M2 motherboard, which has a Realtek RTL8111B chip, which uses the r8169 driver in ubuntu 7.04.

about half the time, it works fine. if i boot and it works, it will continue working until the next reboot.

every 2nd or 3rd reboot, i have no connectivity. i find this in var/log/syslog: "no DHCPOFFERS received"

runnning ifdown/ifup doesn't help. rebooting usually solves the problem.

the dhcp server is a netgear RP614v3, which is working flawlessly with many other devices.

i'm not dual-booting with windows, ubuntu 7.04 (feisty) is the only installed operating system.

i'd appreciate any help anyone can offer...

---

### Post by noob12 on 2007-08-17
Next time you have a boot where you get into the no offer condition, try some of the following to help narrow things down.

Save the output of **dmesg** and of **grep dhclient /var/log/syslog** away. Post it when you can get on.  We kind of expect to see some issue during boot in **dmesg** since you report rebooting fixes it.  Or there may be a race between your firewall coming up and the DHCP interaction which the firewall sometimes wins. List any firewall filter rules you have active on the box using **iptables -nL** and save that in a file to post.

Check your link state using **sudo ethtool eth0** (or whatever the name of your interface is).  Check the link LED.

Try configuring an address, netmask, gateway, and dns servers manually using the System | Administration | Network menu (or using the command line if you know how).  See if the card is functioning even with a manual address.  Once you've configured it manually, try pinging your local DHCP server/router and something outside your net.  For example, ping one of your external DNS servers by ip address not name.

---

### Post by AlpineCarver on 2007-08-17
thanks **VERY** much for your helpful post!

unfortunately (or fortunately as the case may be) i can no longer reproduce this problem. it was happening frequently the first few days after i brought up the system. then, it ran unmolested for a couple of days. now, i can't make a dhcp failure happen. i've rebooted at least 15 times, sometimes powering down for various periods and sometimes not. i also left the power off overnight last night; this morning, the network came up perfectly.

oh well... if it ever happens again, i'll try the things you suggested and post here.

---

