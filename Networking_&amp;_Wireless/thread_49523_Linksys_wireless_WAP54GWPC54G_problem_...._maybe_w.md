---
title: "Linksys wireless WAP54G/WPC54G problem .... maybe with DHCP?"
date: 2005-07-16
forum: Networking &amp; Wireless
---

### Post by tICT on 2005-07-16
Hi All,

I am trying to seup Hoary 2.6.10-5-386 on my laptop with the wireless combo of Linksys WAP54G (AP) and WPC54G (PCMCIA card). Trouble is I can only connect intermittently.

Have setup ndiswrapper with wlan0 assigned a manual IP. I am guessing at a DHCP problem because the card never worked with DHCP in WinXP (although the router accepts DHCP using ethernet) AND get a DHCP failure from the 'Wireless Connection Manager" even though I have setup not to use DHCP!

Using the gui network tools I can see the network ESSID & have set the WEP code. I have had occasions where I can get the internet through the AP but not been able to ping it or the WinXP desktop on the network.

Other related warnings include a 'wlanctl-ng: no such device' when I bring the device up using ifup wlan0 (although it does show as active in ifconfig!). I also loadnisdriver ignored warnings on boot after the initial driver is shown as working.

Troubleshooting gives - 

lspci: shows Broadcom BCM4306 controller (rev 03)

lsmod: pcmcia used (x4) ip_tables (x1) iptable_filter (x0) pcmcia_core (x2) pci_hotplug (x0) ndiswrapper (x0)

dmesg: wlan0 ndiswrapper using lsbcmnds, encryption modes supported, no IPv6 routers present

ifconfig: shows wlan0 UP with inet addr: 192.168.1.102 Bcast: 192.168.1.255 Mask:255.255.255.0 inet6 addr: fe80::20f66ff:feaf:3694/64 

I can ping localhost

interfaces are as follows:

auto wlan0
iface wlan0 inet static
name Wireless LAN Card
wireless_essid HEN2004
wireless_channel 11
wireless_mode managed
wireless_key 781xxxxxxxxxx
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.1.0


I'm not really sure what the different elements are for the interfaces configuration so would appreciate some guidance on this, but the general plea is - why has it stopped working?!

Thanks
John



HP Omnibook 6000

---

### Post by stevenyu on 2005-07-16
can u do a test using dhcpclient

I can't remember the command but it start with dh something

just do dhcpclient wlan0

---

### Post by whitesox on 2005-07-29
no, the command is "dhclient", so you would type
dhclient wlan0

I doubt it will work though

---

### Post by nige on 2005-08-20
I dont know if WEP works in the /etc/networking/interfaces configuration area.
I use the wpa_supplicant for wpa, I haven't tested it with WEP, but I don't know how well it works with WEP. Try it with wpa_supplicant.

---

### Post by murph2481 on 2006-04-05
[QUOTE=nige]I dont know if WEP works in the /etc/networking/interfaces configuration area.
I use the wpa_supplicant for wpa, I haven't tested it with WEP, but I don't know how well it works with WEP. Try it with wpa_supplicant.[/QUOTE]

I have Dapper running and I have edited my /etc/networking/interfaces file and configured the WEP properlly and I have no issues.  So as far as I know there isn't a problem configureing you WEP there

---

### Post by klumix on 2006-12-26
I have a linksys wireless pcmcia card and it works fine. After you install ubuntu edgy 
go to System->Administration->Networking

Your card should appear there in the list should say "wireless connection" select it click the properties button.  Then where it says network id (essid) put the name you have given your wireless router. for example "linksys" password type plain  configuration DHCP Click OK and it should link up. Mine did. works perfect.

[email]bryan@klumix.com[/email]
[www.klumix.com](www.klumix.com)

---

