---
title: "Acer Ferrari - Can't get WLAN(Atheros) to work"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by m4rtin on 2007-02-13
I have a bit of a problem here.

I bought a Acer Ferrari in December, and since then I ran Slackware 11.0 without any big problem with the WLAN.
But I got sick of all the configurating on everything to get stuffs to work. 
So i desided to give Kubuntu a chance. It looked good, and almost every workd 'out of the box'. Except my WLAN.
I don't know what kind of Atheros it is, all 'lspci' gives me is:
"07:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)".

Then I downloaded and compiled Madwifi-ng-current. Everything went well, I could no see my network by scanning. But not connect to it.
My router is a Linksys WRT54-G with WPA encryption.

After compiling the module, and loaded it.
I did the following:
```
ifconfig ath0 up
modprobe wlan_scan_sta
wlanconfig ath0 list scan
```
And here if my net
```
<my network>    00:18:f8:4a:f5:dd   11   54M 45:0   100 EPSs WPA
```
then
```
iwconfig ath0 key s:<acsiipassword>
iwpriv ath0 authmode 2
dhclient ath0

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:cf:65:50:2d
Sending on   LPF/ath0/00:16:cf:65:50:2d
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

acerhk is also loaded, but i cant get my LED's flashing (or even light).
So i *think* my problem is there.


-Martin


EDIT:
I also tried acer_acpi, but when I try to load the module I get this error:
"FATAL: Error inserting acer_acpi (/lib/modules/2.6.17-11-generic/extra/acer_acpi.ko): No such device"
And 'dmesg' tells me this:
```
[17182539.088000] ath0: no IPv6 routers present
[17183273.580000] acer_acpi: Acer Laptop ACPI Extras version 0.3
[17183273.580000] acer_acpi: No WMI interface, unable to load.

```

---

### Post by m4rtin on 2007-02-14
Solved. Had to change from DHCP to Static.

But why isn't DHCP working, when it works on wired connections?

---

