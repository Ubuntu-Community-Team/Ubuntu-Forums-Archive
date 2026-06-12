---
title: "Please Help"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by PsychoticSheep on 2007-02-26
Is it possible to set up a wireless ad hoc connection in dapper? If so how do you do it?! My wireless network card is working and Ubuntu recognises it but i have typed in the SSID and no WEP encryption is on the connection and nothing appears to happen.

Thanks in advance

---

### Post by spd106 on 2007-02-27
You need to switch the wireless card into adhoc mode. This can be done at a terminal with iwconfig. Try these commands
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode ad-hoc
sudo ifconfig wlan0 up
```

Assuming your wifi card is called wlan0.

---

### Post by PsychoticSheep on 2007-02-27
I dont know what my wireless card is called and i think it is already on ad hoc mode! What should i do?

---

### Post by PsychoticSheep on 2007-02-27
Ok i have removed all settings can someone talk me through setting it up again?

---

### Post by chili555 on 2007-02-27
Open up a terminal,  Applications -> Accessories -> Terminal, and type in this command:
     iwconfig

You will see output similar to this (mine):
```
 iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"GBR1"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:62:8D:F7   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/92  Signal level=-55 dBm  Noise level=-140 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:0   Missed beacon:0

```
As you can see, in my case, eth1 is the only interface with wireless information. eth1 is my wireless interface.

Also, as you can see, it is in the managed mode.

---

