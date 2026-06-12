---
title: "network-manager-pptp plugin does not produce anything"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by mja on 2006-12-07
Hi,
I'm trying to establish a VPN-connection to my work. I've installed network-manager, network-manager-gnome and network-manager-pptp. I get the menu for VPNs in the network-manager menu but clicking the "Define VPN" (or whatever it is in English; I'm running Finnish) does absolutely nothing. I know there should be something coming up but..nothing. 

Any clues?

T.y. in advance,
Miika
-------------------------
Kubuntu Edgy, IBM T43 etc.

---

### Post by Saxis on 2006-12-19
Make sure pptp-linux is installed?

---

### Post by knud on 2007-02-20
Well, is there help around? I even get no option entry "Configure VPN..." at the network-manger applet after installing network-manager-pptp anr rebooting.

Looking for hints.

---

### Post by mojorising on 2007-02-22
I think I am having the same problem as well, although I am running feisty herd 4.

I installed the pptp component to network-manager via apt-get and it installed a ton of Gnome stuff (I use KDE) 

I now have a VPN option in the menu when I click the Network Manager icon -- VPN Connections. If I click VPN Connections > Configure VPN nothing happens -- really disappointing since I'm dying to get connected to my company network via VPN with Linux (I usually use a Windows VM in order to do this, which I hate).

Hopefully someone out there knows what's wrong/ missing on this. I tried KVPNC also but am having limited success with that one too. 

Mike

---

### Post by knud on 2007-02-26
> **knud said:**
> I even get no option entry "Configure VPN..."

I reinstalled ubuntu and let the network device get an IP address by DHCP (not static). Now the network-manager is active saying something like "network cable connection". The pptp-plugin is present and I configured my VPN connection.

I get connected to the VPN-server I wanted to but I cannot see any machines. The /etc/resolv.conf is changed but nothing than a comment is entered.

How to configure a DNS by network-manager-pptp ?

Regards

---

### Post by itsdaveperdue on 2007-03-01
I'm having the same problem in Kubuntu.  I installed network-manager, knetworkmanager, and network-manager-pptp.  I get an item in the kde menu named "VPN Connection Manager (PPP Generic)" but it points to a program called nm-vpn-properties that isn't on my system.  I can only assume that the knetworkmanager option to "Configure VPN..." is pointing at the same place.

I installed the same on Ubuntu (GNOME) but with network-manager-gnome and the VPN worked splendidly...but i want to run KDE.

Anyone know where the nm-vpn-properties app should be?  I can't find it anywhere on my system.

Thanks.

[EDIT] Read this bug for knetworkmanager problem as descibed: [https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/74351]("https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/74351")

The original problem you've reported works in Edgy.

---

### Post by itsdaveperdue on 2007-03-01
> **knud said:**
> I reinstalled ubuntu and let the network device get an IP address by DHCP (not static). Now the network-manager is active saying something like "network cable connection". The pptp-plugin is present and I configured my VPN connection.

I get connected to the VPN-server I wanted to but I cannot see any machines. The /etc/resolv.conf is changed but nothing than a comment is entered.

How to configure a DNS by network-manager-pptp ?

Regards

Can you access the systems or can you just not "see" them?

Windows machines use netbios broadcasts to discover and "see" each other which are typically not broadcast through the VPN.  This may be an option on your VPN box, however.  I'm not sure of anything for that on your Ubuntu system.

---

### Post by gewfie on 2007-10-03
The reason that this does not always show up is that the Wired Connection must be set to "Enable Roaming".

Once you do this then the VPN Connections will appear on the Network Manager Icon.

-gewfie

---

