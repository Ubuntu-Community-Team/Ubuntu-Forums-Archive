---
title: "Simple Network Question"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by autocrosser on 2007-09-21
Can you peer-to-peer two Linux computers with wireless cards or do you need a router between? Have never setup a wireless network before.

---

### Post by Paris Heng on 2007-09-21
> **autocrosser said:**
> Can you peer-to-peer two Linux computers with wireless cards or do you need a router between? Have never setup a wireless network before.

Yes.  You can try to make the two PC (eg. PC1 and PC2) become **Ad-Hoc** mode. You can try this,

**At PC1:**
> iwconfig <wifi interface PC1> mode ad-hoc
iwconfig <wifi interface PC1> essid <preferred ssid name>


**At PC2:**
> iwconfig <wifi interface PC2> mode ad-hoc
iwconfig <wifi interface PC2> essid <preferred ssid name>


The SSID for both PC must be the same name, if you set PC1 NAZI, PC2 must also with the name NAZI.

Goto **nano  /etc/network/interfaces** on both PC, enter static ip address for both machines,

PC1:
> address 192.168.0.1 
netmask 255.255.255.0

-----------------------------------------

PC2:
> address 192.168.0.2 
netmask 255.255.255.0

If you are using the PCMCIA. please save all the configuration and restart your machine. If mini PCI, just try ping from the two PC. Just ping the static ip address. Then, ad-hoc is setup.

---

### Post by autocrosser on 2007-09-21
Thank you Paris--
 
The only thing I can't seem to change is mode--it is still on managed--where do I change it to ad-hoc?

---

### Post by autocrosser on 2007-09-21
OK--

This is where I am at---the two units--one running Dapper (all updates done) will accept "wireless-mode ad-hoc" in the /etc/network/interfaces & the panel monitor shows that the signal strength about 70/80%. The other unit--running Gutsy (all updates current) will not accept "wireless-mode ad-hoc" & iwconfig still shows Mode:Managed even after restarting the network & a couple of reboots. Panel monitor shows no signal.

iwconfig shows Mode:Ad-Hoc with the Dapper unit.

Any ideas gladly accepted:)

---

### Post by Paris Heng on 2007-09-22
Did you try this? 

> iwconfig <wifi interface PC1> mode ad-hoc

What that it shown after the key the Enter? No error? or most probably your Wifi NIC did not support Ad-hoc, but I believe that most of the NIC support Ad-hoc. Did you check on the driver? Maybe the driver problem. I am using Feisty anway. I never try on Gusty yet. If is about the Kernel problem and the driver, i really no ideas. :D

---

### Post by pyronicte on 2007-11-03
I comfirm that, in feisty I have in /etc/networks/interfaces the line wireless-mode ad-hoc, and it works fine, but since I updated to gutsy always shows "managed" owing me to change manually each time to ad-hoc with iwconfig mode ad-hoc.
One more thing, after doing that command, I have to introduce also the wireless-essid, because the first one destroys the essid previously showed.

It seems to be a bug in gutsy.

---

### Post by nrasmus on 2007-12-10
Has anyone reported this as a bug?  I'm having the same problem.  Gusty doesn't seem to want to accept the mode parameter.

---

