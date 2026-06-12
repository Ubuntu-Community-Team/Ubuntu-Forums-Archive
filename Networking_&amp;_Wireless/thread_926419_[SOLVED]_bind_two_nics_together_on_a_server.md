---
title: "[SOLVED] bind two nics together on a server?"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by iansane on 2008-09-21
Hi,

In windows server classes I set up a DHCP/DNS server and used a option to bind one nic to the other so internet came in one and DHCP handed out IP's and forwarded packets to the intranet on the other.

How do I do that in Ubuntu? I can't find much about binding. Just a lot about bridging. I have a onboard nic and a wireless but the wireless won't work with bridging for my virtual machines so I'm trying to bind the nic to the wireless and then bridge the vm to the nic to get around the wireless problem.

If I need to to make it work, I can set up DHCP server on the host. I just need to get pointed in the right direction. Especially with the binding part.

Thanks

---

### Post by superprash2003 on 2008-09-22
i presume this is similar to what you want to achieve [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by iansane on 2008-09-23
That just might be what I'm looking for superprash2003.

I thought it would have to involve dhcp and bind but I'm going to try this and see if it works.

Also I got a lot more results for bind by looking for "dhcp bind" so if I need to go that way, there's a lot more info available. I just wasn't searching right.

Thanks

---

### Post by iansane on 2008-09-23
Can anyone tell me how to delete the mess I mad in my original attemt to bridge to wlan0? I now have a bridge (br0), and 4 vbox interfaces that I can't get rid of.

I commented out the lines for the bridge in /etc/network/interfaces and then tried VBoxTunctl -d vbox0 to delete the vbox interfaces. It deleted them and they came back after reboot.

With the above link and two other suggestions for shareing wlan with eth0 There's a good chance something will work but as it is, I keep getting errors I think because the br0 and vbox already exist?

I'm trying "VBoxAddIF" to add an interface and I get permission denied when running as root.

Any ideas or how to delete the original mess?

Thanks

---

### Post by iansane on 2008-09-25
Ok I figured out how to remove all the mess. Part of it was ubuntu commands and part was VBox commands but even after starting fresh, and following the steps in the link above from VirtualBox forums, I get no IP's on VM.

I've been real confused about the default gw and subnet so I'm not sure if there's something in the vm's OS I need to change to make it work or if auto dhcp should work in this case.

When I boot up windows or ubuntu vm ubuntu no longer has eth0 and windows fails to get an IP but has a interface in the network connections box.

Two ubuntu vm's actually loose eth0 all together as if the host settings are changeing the guest configuration. They also end up with eth2 and/or eth3 but no eth0 when I list available IF's. Not understanding why they change, and even manually setting up eth2 or 3 still doesn't get IP.

Are there other settings I need to configure on the host or guest besides setting up the bridge and vbox IF?

Thanks

---

### Post by iansane on 2008-10-03
Yeah it was other settings.


To make the settings permanent and fix problems I had to put entries in the /etc/network/interfaces and manually delete my mistakes from /etc/vbox/interfaces.

 The eth0, Vbox, br0, and wlan0 were all configured and connected right. I just needed to learn how to set up iptables to forward packets for me in order for the internal to get to the external.

Figured it out from some tutorials, webmin, and other posts here on the forum.

Anyone else having similar probs with dhcp and multiple nics, look into iptables. It's more than just a firewall. It's also a router. I didn't know that at first.

---

