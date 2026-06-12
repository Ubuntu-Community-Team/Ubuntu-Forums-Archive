---
title: "SSH to virtual machine works only in one specific way"
date: 2021-02-21
forum: Networking &amp; Wireless
---

### Post by forumate on 2021-02-21
I have Ubuntu 20.04 installed on VMware Workstation 16 Player. I installed SSH server. To test it I did not use any key-pair, but only password.
From the Windows host the only way I can SSH into the machine is by using the command [B]"ssh username@<LAN IP address*>". *address as seen in `ip a` command (in Ubuntu) near `inet`
[/B]
If I try to use the same command from another PC I will get **"ssh: connect to host localhost port 22: Connection timed out" **(But that's obvious, because the IP is internal for the same network of the virtual machine and the Windows host)
But, If I try to use **"ssh username@localhost" **(from the Windows host)I get **"ssh: connect to host localhost port 22: Connection refused"**

Also, If I try to use **"ssh username@<public IP address>" **I get[B]"ssh: connect to host localhost port 22: Connection refused"

[/B]To sum it up, the only way I can SSH to this virtual machine is from the host it runs from, and only using **"ssh username@<LAN IP address**[B]*>"
*address as seen in ip a near inet


[/B]How to fix it? how to be able to SSH to it from other PCs on the internet as well?

Thanks

---

### Post by TheFu on 2021-02-21
_bridged networking_ in the VM settings.

---

### Post by forumate on 2021-02-21
> **TheFu said:**
> _bridged networking_ in the VM settings.
Thank you.
I just changed it from NAT to Bridged, and now I get "connection timed out" whenever I'm trying to connect from any other pc than the host

---

### Post by TheFu on 2021-02-21
> **forumate said:**
> Thank you.
I just changed it from NAT to Bridged, and now I get "connection timed out" whenever I'm trying to connect from any other pc than the host

is the bridge connected to the right interface?
reboot the VM?
firewall?

NAT was never going to work.

---

### Post by forumate on 2021-02-22
> **TheFu said:**
> is the bridge connected to the right interface?
reboot the VM?
firewall?

NAT was never going to work.

Thank you! How do I tell if the bridge is in the right interface?
By the way, it's weird because I managed to connect once using user@<public IP address> after changing to bridged mode, and then it timed out again! So confusing.. why it worked once? ](*,)

---

### Post by TheFu on 2021-02-22
Please understand that we don't know what you are doing, what you know, what you don't know, and how strong you are in anything. If you don't tell us exactly what you are doing, we don't know.

Can you ping the VM from every other system on the network?  By name **AND** by IP?  ssh really likes for the name resolution to match in certain configurations.  It is part of the security to prevent MiTM or redirection attacks.

If you don't tell us stuff, we don't know it.

---

