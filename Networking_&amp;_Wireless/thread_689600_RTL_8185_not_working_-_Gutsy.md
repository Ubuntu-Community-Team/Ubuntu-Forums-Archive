---
title: "RTL 8185 not working - Gutsy"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by HangLoose on 2008-02-06
Hi there,

So I have a RTL 8185 wireless card that is not working in my Desktop.
I did some of what was said in the forum but without any success.
So I hope with this information below I can get some more ideas:
```

 hangloose@kauai:~$ lspci | grep RTL
04:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

```

and

```

hangloose@kauai:~$ dmesg | grep rtl
[   34.547857] rtl_ieee80211_crypt: registered algorithm 'NULL'
[   34.547860] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[   34.547862] rtl_ieee80211_crypt: registered algorithm 'WEP'
[   34.547864] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[   34.589293] rtl8180: Initializing module
[   34.589341] rtl8180: Wireless extensions version 22
[   34.589390] rtl8180: Initializing proc filesystem
[   34.589481] rtl8180: Configuring chip resources
[   34.589706] rtl8180: Memory mapped space @ 0xfebffc00 
[   34.590671] rtl8180: MAC controller is a RTL8185 b/g (V. D)
[   34.590728] rtl8180: This is a PCI NIC
[   34.590778] rtl8180: Reported EEPROM chip is a 93c46 (1Kbit)
[   34.596563] rtl8180: Card MAC address is xxxxxxxxxxxxxx
[   34.610987] rtl8180: EEPROM version 105
[   34.612939] rtl8180: Card reports RF frontend Realtek 8225
[   34.612987] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
[   34.613049] rtl8180: WW:use it with care and at your own risk and
[   34.613097] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[   34.613160] rtl8180: Energy threshold: b
[   34.613206] rtl8180: PAPE from CONFIG2: 6
[   34.613335] rtl8180: IRQ 17
[   34.613460] rtl8180: Driver probe completed
[   38.686528] rtl8180: Bringing up iface
[   38.896444] rtl8180: Card successfully reset
[   39.922879] rtl8180: Setting SW wep key

```


What should I do people?
I`m using WPA-PSK with the authentication and TKIP for encryption.
Should it be changed to WEP?

Thanks folks.

---

### Post by HangLoose on 2008-02-07
up

---

### Post by HangLoose on 2008-02-07
up again

---

### Post by kevdog on 2008-02-07
Where did you get that driver -- it looks like it is working -- I like the output in dmesg -- 

use it with care and at your own risk

Sounds dangerous and exciting

Can you please post
iwlist scan

---

### Post by HangLoose on 2008-02-08
This is the output:
```

lo        Interface doesn't support scanning.

wlan0     No scan results

```

---

### Post by kevdog on 2008-02-09
Can you list lshw -C network?

---

### Post by HangLoose on 2008-02-10
```

  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: wlan0
       version: 20
       serial: 00:1a:9f:91:b4:38
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g

```

---

### Post by jjrp78 on 2008-02-13
Hei,

I have a A-LINK WL54PC, which uses a  RTL-8185 chip and Gutsy. If you only wanna have wireless it worked for me the windows XP driver that you can download from Realtek Home Page with ndiswrapper.

I would love to make the native drivers work but with the linux drivers I downloaded from the same site I can do a scan but get every AP with 0 signal strength and can't connect.

Let me know if you know a way around this or if you need help installing the XP drivers

---

