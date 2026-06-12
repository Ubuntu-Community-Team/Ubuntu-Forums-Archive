---
title: "Wireless setting won't stick after reboot"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by humptruk on 2007-12-17
Hello all,
  I have a Toshiba Satellite M45-S265 laptop loaded with 7.10.  Everything is fine except that the wireless connection setting (which works right now!!!) wont start at reboot.  I have to goto the "System->Administration->Network application and restart the connection.  The wireless connection and its settings are displayed in the GUI, as well as the check mark which I thought meant "default" next to the wireless connection.  How do I get this connection to be started at boot time.

sysadmin@jabuntu:/etc$ lspci | grep -i net
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
05:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
sysadmin@jabuntu:/etc$ 

sysadmin@jabuntu:/etc/network$ cat interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.100.202
netmask 255.255.255.0
gateway 192.168.100.1
wpa-psk fa8dd507d034e6f506b1500efc679651fa4edb2182dda71092686a6c4d511210
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid cajaca







auto eth0



Can anyone point me in the right direction?  Thanks,

-Chad

---

### Post by matthewboh on 2007-12-19
I have the same problem, and after many boots, discovered that if I wait about five seconds to enter my username and password, it works fine.  I think NetworkManager is dependent on a service that doesn't quite make it up if you quickly type in your name and password.

---

### Post by wieman01 on 2007-12-19
See post #2 of my WPA tutorial. This is a bug and I have posted a workaround there.

---

