---
title: "Using nmcli for creating new connections not working"
date: 2015-09-09
forum: Networking &amp; Wireless
---

### Post by arunb on 2015-09-09
Hi,

I am trying to develop a linux program designed to be run in Kiosk mode (on lubuntu OS), the program allows users to create and edit wireless/ethernet network connection using its own GUI interface instead of the Network manager applet.

I have seen some examples on the internet that show how connections can be created using nmcli con add options, however they dont work in my computer (running on Ubuntu 14.04 OS), an invalid command error.

My version of nmcli is > nmcli tool, version 0.9.5.96

So I manually create the connection file, use the cat /proc/sys/kernel/random/uuid to generate a UUID for the connection. However the networkmanager does not list my connection (when using nmcli con list).

The manually created connection is shown below. It is similar to the one created by Network Manager gui (except for UUID all other details are same), but still Network Manager does not recognize the connection file. I have double and triple checked both the files, one created manually and the other by the networkmanager applet, and there is no difference between them (except for UUID)

A sample of the connection file is shown below. The settings are for a secure SSID, WPA-PSK enabled, automatic IP.

> 
[connection]
id=arun
uuid=635a939e-758c-4ea4-ac37-d06253189340
type=802-11-wireless

[802-11-wireless]
ssid=<ssid>
mode=infrastructure
mac-address=68:94:23:Ab:ac:5E
security=802-11-wireless-security 

[802-11-wireless-security]
key-mgmt=wpa-psk
psk=<password>

[ipv4]
method=auto

[ipv6]
method=auto


I suspect there is some undocumented/hidden feature that is not made public by the developers, this prevents users from manually creating network configuration files.

The connection files are stored in /etc/NetworManager/system-connections

Please can anyone suggest how nmcli can be used to create wifi/ethernet connection...
Also why my nmcli does not support the commands like add reload etc. ?? It seems I need to enable something for this to happen...

Thanks
a

---

