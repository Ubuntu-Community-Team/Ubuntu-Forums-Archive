---
title: "How to connect broadband"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by satimis on 2006-10-18
Hi folks,

Ubuntu-6.06.1-server-LAMP-amd64
For test only
dynamic IP
eth0 (one ethernet card)


Following Server Guide
html - [https://help.ubuntu.com/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/ubuntu/serverguide/C/index.html)

/etc/network/interfaces
auto eth0
iface eth0 inet dhcp

But I can't figure out where to put login and password so that ISP will be connected automatically at boot.  Please advice.

TIA

pppoe-setup, pppoeconf, etc. did not work here.

B.R.
satimis

---

### Post by handy on 2006-10-18
Do you have an adsl modem/router?  You will need to access it via it's IP address & Firefox (or whatever browser) & configure it.

Your manual for the modem/router will have info' about this, also they often have the IP address & default user name & password printed on the ID label of the modem/router.

---

### Post by satimis on 2006-10-18
Hi handy,

Tks for your advice.

> Do you have an adsl modem/router?
Yes.  Connection via ADSL modem to telephone socket.  


> You will need to access it via it's IP address & Firefox (or whatever browser) & configure it.

Your manual for the modem/router will have info' about this, also they often have the IP address & default user name & password printed on the ID label of the modem/router.
Whether "man modem"?  I'm now answering this posting on another PC.

TIA


B.R.
satimis

---

### Post by mips on 2006-10-18
You connect via Ethernet, thus you have a ROUTER. No need for pppoe or pppoa. Just setup DHCP and you should be good to go.

Double check your routers config.
Ensure it is in routed mode and not bridged mode.
Esure it has the username & password specified under authentication.
Ensure the encapsulation is correctly setup to pppoe or whateve you use.

---

### Post by satimis on 2006-10-18
Hi mips,

Tks for your advice.

> Just setup DHCP and you should be good to go.
Connection is via ethernet --> ADSL modem/router --> telephone line.

Whether you meant setup /etc/network/interfaces```

auto eth0
iface eth0 inet dhcp
```

Where shall set```

config_eth0=( "adsl" )

```
On which file?  Tks.

> Ensure the encapsulation is correctly setup to pppoe or whateve you use.
pppoe is not available.  What shall I use there?  TIA


B.R.
satimis

---

### Post by mips on 2006-10-18
Open a web browser and type in your routers IP address, it will open the routers management interface, that is where you configure your router. Leave ubuntu alone, just enable DHCP from the gui for network settings.

---

### Post by handy on 2006-10-18
You need to be able to access your router through firefox, so you can check **_*ITS*_** configuration.  This is ***_NOT_*** in Ubuntu, this is in your hardware router. OK? :)

**[Edit:]** Sorry Mips, dual posting, I'll bail out... :)

---

### Post by satimis on 2006-10-18
Hi mips,

> Leave ubuntu alone, just enable DHCP from the gui for network settings.
Sorry, no X is running on LAMP-server.  I'll check later what text-browser is running there.

Tks.


B.R.
satimis

---

### Post by satimis on 2006-10-18
Hi handy,

Tks for your advice.

> You need to be able to access your router through firefox, so you can check **_*ITS*_** configuration.  This is ***_NOT_*** in Ubuntu, this is in your hardware router.
There is no GUI browser running because no X-window avoiding creating a risk hole on the server.  I'll check afterwards which text-browser is running.

Tks.


B.R.
satimis

---

### Post by mips on 2006-10-18
Dont you have another pc or laptop you can plug into the router to check it's config ?

---

### Post by satimis on 2006-10-18
Hi mips,

> Dont you have another pc or laptop you can plug into the router to check it's config ?
Yes, I have another PC.

Just looked at the ADSL modem/router, no socket available there execpt a serial port, I supposed, which is marked "console" 

one port connected to teleplone line
one port connected to LAMP server

Please advise.  TIA


B.R.
satimis

---

### Post by handy on 2006-10-19
You can disconect the server to access the modem to check/configure it with the other computer.

---

