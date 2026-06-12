---
title: "ubuntu server 12 with wifi and preffered wifi"
date: 2015-07-22
forum: Networking &amp; Wireless
---

### Post by atux on 2015-07-22
[TABLE]
[TR]
[TD="class: votecell"]          

              [/TD]
              [TD="class: postcell"]        I do have a  pc(router_office) that runs ubuntu_server (12.04) and it gets internet from wlan0 and acts as router for eth0 (NAT). It acts as my router. Everything works fine. 
My setup is pretty simple in /etc/network/interfaces:

  auto wlan0
iface wlan0 inet static
    address 192.168.2.49
    netmask 255.255.255.0
    broadcast 192.168.2.255
gateway 192.168.2.1
    wpa-ssid "res_wifi"
    wpa-psk "passw0rd4!"
dns-nameservers 8.8.8.8

auto eth0
    iface eth0 inet static
    address 192.168.1.10
    netmask 255.255.255.0
    dns-nameservers 8.8.8.8
  I have an second wifi that i could get connected to, which has SSID:be_sec_office with passwd:passwfoo
  While in my laptop lxde in the connection  manager if one wifi fails, then it connects automatically to the next  one. How can I do that in my small pc(router_office), please?

     

[/TD]
[/TR]
[/TABLE]
i have read about wpa supplicant, but in my setup i am not using wpa_supplicant and i do not know how to configure the system for wpa_supplicant.

---

