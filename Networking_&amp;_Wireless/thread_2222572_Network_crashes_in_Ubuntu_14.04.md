---
title: "Network crashes in Ubuntu 14.04"
date: 2014-05-07
forum: Networking &amp; Wireless
---

### Post by davoudi on 2014-05-07
Hi Folk,

 I just recently installed a fresh Ubuntu 14.04 on my laptop. It first had a graphic issue which I solved it with help of people here but now network crashes every other time.

 Thank you very much in advance for your time.
Best wishes,
Bahman.

---

### Post by varunendra on 2014-05-07
Please explain in more detail what you mean by "network crashes". Which network interface are you talking about (Ethernet, WiFi, USB adapter etc..??) and what exactly happens?

---

### Post by davoudi on 2014-05-07
I didn't check my wireless but I have no wire connection after facing an error pop-up with a message saying that Ubuntu faces an internal error . The network-mannager shows that I am connected but I cannot connect to net. The command sudo service networking restart fails and I have to restart my computer to have the connection back.

---

### Post by grahammechanical on 2014-05-07
Network manager only establishes a connection to the router. If the router is dropping the connection to the Internet Service Provider (ISP) then Network Manager will still show us connected but we will not have access to the Internet. I have found that using the Network Manager icon menu to disable and enable Networking will push the router to try to re-connect to the ISP. And that sometimes fixes things without re-booting.

Of course if my ISP is, for some reason, failing to provide a good service at that time the problems will continue. There are times when I have to switch the router off and on and times when I have to wait until my ISP fixes things.

Regards.

---

### Post by varunendra on 2014-05-07
When you loose the connection, please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
lspci -nnk | grep -iA2 net
nm-tool
dmesg | egrep -i 'network|error'
```

---

### Post by davoudi on 2014-05-10
Here are the outputs:

lspci -nnk | grep -iA2 net

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Foxconn International, Inc. T77H126.00 802.11bgn Wireless Half-size Mini PCIe Card [105b:e017]
    Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller [11ab:4380] (rev 10)
    Subsystem: Sony Corporation Device [104d:9072]
    Kernel driver in use: sky2

nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:24:BE:B4:47:48

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         194.225.69.233
    Prefix:          25 (255.255.255.128)
    Gateway:         194.225.69.129

    DNS:             194.225.73.141
    DNS:             194.225.152.10


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        2C:81:58:EC:85:AB

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    physics2:        Infra, 98:FC:11:54:D4:69, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA
    Mobin:           Infra, 04:C0:6F:5F:BF:77, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA
    setareh:         Infra, 00:1F:FB:35:40:A2, Freq 2457 MHz, Rate 54 Mb/s, Strength 20 WPA2
    FSEN 2013 - 5:   Infra, 28:94:0F:F9:44:BB, Freq 2437 MHz, Rate 54 Mb/s, Strength 37
    AAA-Soli:        Infra, 78:54:2E:7F:FC:0E, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WEP
    elin:            Infra, 00:1F:FB:24:42:86, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA2
    Soheil:          Infra, AC:E8:7B:AB:84:0B, Freq 2432 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2


dmesg | egrep -i 'network|error'

[    0.733356] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[   13.308110] type=1400 audit(1399632096.184:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=408 comm="apparmor_parser"
[   13.308498] type=1400 audit(1399632096.184:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=422 comm="apparmor_parser"
[   13.308952] type=1400 audit(1399632096.188:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=408 comm="apparmor_parser"
[   13.309325] type=1400 audit(1399632096.188:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=422 comm="apparmor_parser"
[   15.881866] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[76796.836454] vpnagentd[1130]: segfault at fe000eff48 ip 00007f64b4aa79ce sp 00007f64b28ddf10 error 4 in libvpnagentutilities.so[7f64b4a3b000+ae000]

---

### Post by davoudi on 2014-05-12
Any help?

---

### Post by varunendra on 2014-05-12
Sorry for not being able to reply sooner. I didn't get an opportunity to check on the forums even on Sunday this week....

I can't see any obvious hints/culprit in the above outputs you posted. Can you post an screenshot of the error message please?

Also, can you test the connection in a Live session (running off a Live DVD/USB) and see if the problem exists there as well?

We don't have the slightest hint yet to guess whether the problem is network (service, or a component) related or something else and networking problem is just a result of that. As such, we can only try a few blind shots. For example, you can try a couple of driver parameters available for you driver as follows -
```
echo "options sky2 disable_msi=1" | sudo tee /etc/modprobe.d/sky2.conf
```
..then reboot. This will create a file "sky2.conf" that will cause the driver to load with "disable_msi=1" parameter. I don't know exactly what this parameter does, but it appears to be acpi/interrupts related, so may be critical. In some cases, improper setting to such things may even prevent the kernel to boot properly. So if something bad happens after the reboot, keep a Live DVD/USB handy to delete the file (/etc/modprobe.d/sky2.conf) to get back to defaults.

Another parameter that looks worth trying (and less critical) is "legacy_pme". To try that one run the following command in a terminal -
```
echo "options sky2 legacy_pme=1" | sudo tee /etc/modprobe.d/sky2.conf
```
..and reboot as earlier. If no change, delete the file (to go back to defaults) with -
```
sudo rm /etc/modprobe.d/sky2.conf
```

You can also try both the parameters simultaneously -
```
echo "options sky2 legacy_pme=1 disable_msi=1" | sudo tee /etc/modprobe.d/sky2.conf
```

I have warned you though - I have no hints so far and these are just blind shots, one of which can be critical for proper booting. So try them at your own risk, I don't take any responsibility for the sparks and smoke that may come through the ethernet port after trying them. :p

---

