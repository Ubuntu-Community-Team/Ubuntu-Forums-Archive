---
title: "WPA-TKIP, ndiswrapper... ugh!!!!!!!!"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by NCUNIX on 2006-11-06
Ok, I have the latest Ubuntu, ndiswrapper, wpa_supplicant, and linksys driver (WPC54G ver 2) installed (using ndiswrapper).

My access point is doing WPA-TKIP encryption. I can see the wlan0interface up (ifconfig wlan0) and iwconfig shows the interface.

In Gnome, when I go to network and configure the network with my HEX key, IP address, gateway, and DNS I get a signal bar in gnome but an X over network connections.  I've seen some mention of network-manager-gnome having an option especially for TKIP but I dont seem to have network-manager-gnome installed because it isn't running.

Any help establishing a connection would be great!

Michael

---

### Post by wieman01 on 2006-11-06
If you wish to configure WPA manually, you can follow this thread:

[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

Post #4 shows an example for WPA-TKIP, however, pay attention for the key generation... Do it according to the section that follow point 9 of post #1 ("wpa_passphrase <your_essid> <your_ascii_key>"), otherwise your PC won't connect.

---

### Post by NCUNIX on 2006-11-06
awesome, thank wieman01... trying now....

---

### Post by wieman01 on 2006-11-06
Ok, simply post your "/etc/network/interfaces" if you need a hand. WPA-TKIP should not be a big problem.

---

### Post by NCUNIX on 2006-11-06
interfaces:

auto wlan0
iface wlan0 inet static
wpa-driver wext
wpa-conf managed
wpa-ssid linksys
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <wpa-password linksys passphrase> replaced what I got after psk=
address 192.168.254.9
netmask 255.255.255.0
network 192.168.254.0
broadcast 192.168.254.255
gateway 192.168.254.1
dns-nameservers 68.10.16.25 68.10.16.30

When I ran sudo /etc/init.d/networking restart:

* Reconfiguring network interfaces...
wlanctl-ng: Operation not supported
Failed to enable the device, exitcode= 1
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1

---

### Post by NCUNIX on 2006-11-06
ok, replaced wp-ap-scan with 1 instead of 2 and I'm almost sure I am connected now, howeever when I run firefox it dosent load..lol... hum...

---

### Post by wieman01 on 2006-11-06
First of all, "wpa-ap-scan" should only be "2" if your ESSID is hidden. Otherwise it should be "1".

Before we go ahead, can you please do a scan for me & post the results:
> iwlist scan
I want to see if there is an issue with your adapter first. Does it connect to unsecured networks without a problem? I would test it first.

---

### Post by wieman01 on 2006-11-06
> **NCUNIX said:**
> ok, replaced wp-ap-scan with 1 instead of 2 and I'm almost sure I am connected now, howeever when I run firefox it dosent load..lol... hum...
Ok, please ping your router and see if you get a response:
> ping 192.168.254.1
Then do:
> route

---

### Post by NCUNIX on 2006-11-06
ok, yes I am connected because I can ssh to a remote internet host. You ROCK wieman01!!!   Now, why my firefox isnt loading...lol

---

### Post by NCUNIX on 2006-11-06
yep yep, pinging the router and yahoo.com works. Guess I need to reinstall firefox. Dude, again, you rock!

---

### Post by wieman01 on 2006-11-06
You need to disable IPV6...

To disable ipv6 in Firefox:

> 1. URL: "about:config" then <enter>.
2. Search for "ipv6" (use the Filter).
3. Right-click on "network.dns.disableIPv6" and select "Toggle".

Then try browsing... If you want to take it a step further (makes sense for performance reasons), the disable IPV6 globally.

To disable "ipv6" globally see this thread (first post): [http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6]("http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6")

---

