---
title: "VMWare and Gateway Address"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by the_0ne on 2006-10-08
Just finished installing Edgy Beta in a VMWare virtual machine.  I'm having a strange problem with networking.  I know it's a beta, so I'm sure there are still bugs here and there, but this one seems too plain.

If I go into the System -> Administration -> Networking app, I can choose "Wired Connection" and change my Configuration to DHCP, it pulls an ip from my router and dns with no problem.  However, if I go and set to standard, set my ip, my subnet (255.255.255.0) and then my gateway address to my router 192.168.1.1.  The gateway disappears.  I click Close, my network settings change (confirmed by using ifconfig), however, my gateway disappears.  I can't ping anything.  DNS is fine, everything is fine except my gateway is gone.  I tried this over and over again, setting it back to dhcp and back again also and everytime my gw disappears.

I'm not new to networking and have several machines in my house with no networking problems.  Is this a bug I should report?  Can someone else confirm this problem?  I am able to get around it by manually setting /etc/network/interfaces and putting in the gateway, however I should definitely not have to do that?!?!

Thanks in advance.

---

### Post by thomas79 on 2006-10-26
I have a similar problem, running kubuntu on vmware. Other preference values such as DNS server address works fine, but the Gateway address doesn't seem to get stored when I push the Apply button. The next time I open the Network Settings window, the gateway address is gone.

---

