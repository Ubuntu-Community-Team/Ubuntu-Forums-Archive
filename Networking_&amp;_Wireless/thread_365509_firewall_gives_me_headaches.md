---
title: "firewall gives me headaches"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by louis_nichols on 2007-02-19
Hi!

I've been using firestarter for quite a while now with very good results. But a while ago I made a clean reinstall and I've been having some trouble ever since, It doesn't make sense to me.

My computer is connected to the internet directly via eth0, with an IP assigned via DHCP by my ISP. I also have another ethernet card, eth1, to which I gave the IP 192.168.0.1 and enabled a dhcp server for it. I set Firestarter to share the internet connection with PCs behind my firewall.

The problem is that the firewall is acting very weird. The policy for outbound connections is open+blacklist items and I have a list for incoming that I manually edit. now let me give you an example to see how this is weird.

I use samba. I set the incoming connection to accept connections on ports 137-139 and 445. Outgoing connections are, as I said, open by default, However, when I try to use the command ```
smbclient --list=*hostname*
``` it won't work. But, if I disable the firewall, the command will work and I can see in firestarter's monitor an outgoing connection on port 445. Of course, if I disable the firewall, computers behind it can't access the internet anymore. Anyways, I get a very similar situation with dc++ on the internet.

I'd really appreciate some pointers on this issue. Because I use firestarter, I didn't even try to learn how to use IPTABLES.

---

### Post by handy on 2007-02-20
Maybe this link can help you:

***_[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)_***

---

### Post by louis_nichols on 2007-02-20
> **handy said:**
> Maybe this link can help you:

***_[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)_***

Thanks for the tip! I was hoping I can avoid going directly to IPTABLES commands, but I might have to.

My concern is that firestarter will always reset settings I do directly using iptables. Of course, I could just drop firestarter altogether... pretty tough decision.

---

### Post by handy on 2007-02-20
It takes me only a few minutes to cut & paste from the IP-tables tutorial & a machine is invisible on the net.

I have never used Firestarter, I have only used IP-tables in the above manner on multiple installs of both Dapper & Edgy, never a problem.

You will have to spend a little more time configuring for your particular set up, I don't think it will take you very long though... 

All the best :-)

---

