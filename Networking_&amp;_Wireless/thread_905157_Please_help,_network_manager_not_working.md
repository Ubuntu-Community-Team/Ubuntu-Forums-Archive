---
title: "Please help, network manager not working"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by michaelbr on 2008-08-30
:confused:Hi:

It's much appreciated if someone can show me how to fix my network problem. I have an Acer Aspire 4715Z laptop, I just installed Ubuntu 8.04 LTS along with Windows XP, so far everything is fine, until I tried to configure my wired network (I have an ADSL modem to connect to my ISP, so I'm using PPPoE), then find out it's not working (I'm not sure if the rest is working, but my priority right now is try to solve one problem at a time). I'm new to Linux/Ubuntu so please bear with me, I'm quite comfortable with Windows but would like to switch to Linux/Ubuntu, and this is what I've done so far:

I went to System > Administration > Network > Unlock > then selected my location > in Wired connection I selected Automatic configuration (DHCP) and Enable roaming mode deselected,

and Point to point connection,
In General tab I have the following settings:
Enable this connection selected
Connection type: PPPoE
Account data: username and password filled out

In modem tab:
Modem settings: Ethernet interfaces eth0 selected (this is the only option I have)

In Options tab:
Connection Settings:
Set modem as default route to internet selected
Use the internet service provider nameservers selected
Retry if the connection breaks or fails to start selected

When I tried to select the checkbox of Wired connection, it kept selected, but when I tried to select the Point to point connection checkbox, in few seconds the check mark was reset, it seems something is wrong and won't enable it.

How can I see what's wrong with my settings? BTW I used lspci command to output my hardware, it seems Ubuntu could see my network card:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)

04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

What else can I do to troubleshoot/enable my network?

---

