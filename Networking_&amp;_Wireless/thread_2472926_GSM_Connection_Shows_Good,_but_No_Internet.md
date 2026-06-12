---
title: "GSM Connection Shows Good, but No Internet"
date: 2022-03-17
forum: Networking &amp; Wireless
---

### Post by tbnrc on 2022-03-17
[COLOR=#000000]Hello folks,[/COLOR]

[COLOR=#000000]I'm working with some SBCs (multiple of the same model). I've installed Ubuntu Server 20.04 LTS. I'm using a Telit LE910C4-NF LTE modem over USB (and mPCIe on USB rails).[/COLOR]

[COLOR=#000000]Following initial setup, I install network-manager and modemmanager.[/COLOR]

[COLOR=#000000]I setup a new gsm connection with nmcli named "LTE", and set the appropriate gsm.apn. Lastly, "nmcli con up LTE".[/COLOR]

[COLOR=#000000]"nmcli device status" shows my gsm connection active, green, connected on cdc-wdm0.[/COLOR]

[COLOR=#000000]"nmcli r" indicates all radios are active.[/COLOR]

[COLOR=#000000]"ip a" & "ifconfig" both indicate the correct IP (static from the ISP end), DNS servers, etc.[/COLOR]

[COLOR=#000000]"mmcli -m 0" indicates the modem is working, connected, signal is good at 60%.[/COLOR]

[COLOR=#000000]But I get no internet.[/COLOR]

[COLOR=#000000]"ping 8.8.8.8" results in "Host unreachable". "ping google.com" results in Temporary resolve failure.[/COLOR]

[COLOR=#000000]I attempt to set "ipv4.dns" to 1.1.1.1 1.0.0.1 in the LTE profile on network manager, with no change.[/COLOR]

[COLOR=#000000]In Ubuntu Desktop, the modem works without any trouble. What is happening on Server?[/COLOR]

---

### Post by Andrew_Welham on 2022-03-31
do you have  a default route ?

can you ping yourself ?
Can you ping other devices in the local subnet ?
Can you ping other devices outside the subnet ?

---

