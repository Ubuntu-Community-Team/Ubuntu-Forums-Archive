---
title: "Last set of auto updates to 7.10 caused Firefox and Samba to fail"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by calif99x on 2007-11-09
Hi:

I am running Ubuntu 7.10 (upgraded by auto-update from original 7.04 install) on a dual core Intel 6750 CPU 4GB RAM, and a 10/100 PCI network card.

After accepting the last set of automatic updates, Firefox now gives a "server not found" error message, and the shares I had working with Samba are no longer accessible from my windows XP system.

I am pretty stumped as it initially appeared to be the ipv6 regression bug, so I applied the suggested fix turned up by google of editing the aliases file.

I also ran the dpkg --configure -a command, but no job.  Firefox cannot seem to find it's way to my router.

ifconfig shows an address of 192.168.1.101 for eth0.

The somewhat odd things is that if I use VMware workstation 6.0 on the system, Firefox on the virtual machine (under Windows XP as a guest OS) can access the internet fine.  At that point, Ubuntu system monitor shows network traffic.

I have searched this forum, but did not find any obvious references to this problem, I would appreciate any pointer to solving the problem.

Thanks

---

### Post by Peter09 on 2007-11-10
Yep, the shares no longer working in Samba is the same as I have. I am pretty sure its all to do with a DHCP problem, can you ping the share machine by IP but not by name?

As for firefox not working, check the you have the gateway set up and DNS is working. Can you ping an external ip address and can you ping an external host by name?

---

### Post by calif99x on 2007-11-13
Hi:

Thanks for your reply, it gave me a couple of ideas to check out, and the problem seems to be solved at least for now.

The problem turned out to not be in Ubuntu (or is it??), rather in my Linksys router.

I noticed in the router application & games management settings that dns was check "on" but the address it referred to for DNS resolution was itself; which would make sense since this is really a DNS forwarder.

For whatever reason, Ubuntu does not like the setting, while MS Windows XP does not care and works anyway.  This was Windows XP both on another stand alone computer and one running in VMware Workstation 6 as a VM using bridged networking.

End result was that I removed the setting, and Ubuntu now find the network fine and Firefox/Samba work as expected.  Windows continue to work, so that part is also good.

Thanks

---

