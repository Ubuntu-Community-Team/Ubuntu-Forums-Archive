---
title: "wifi-radar &quot;No wifi-device found. Exiting.&quot;"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by Mariane on 2010-01-28
I cannot connect to the wifi network. Please help.

My version is 2.6.26-2-686

iwconfig:
lo no wireless extensions.
eth0 same

iwlist scan:
lo Interface doesn't support scanning
eth0 same

lspci:
Network controller: Intel Corporation Wireless WiFi Link 5100
The rest does not seem to be related to network stuff

Please don't tell me "What is your so-and-so" without telling me how I can find out this information. I typed these inquiring commands because other people had been told to type these, out of my head I know very few commands.

Mariane

---

### Post by eaglator on 2010-01-28
i am new to ubuntu 9.1 n my wifi doesnt work...
i am using a toshiba satellite ..its about a 4 yr old model having aethros ar5006eg pci card
so i read a few archives on this post...seems outadated fr 9.1, or really cant figure out how to proceed... madwifi.org doesnt help either...plz help... 9.1 my only hope fr my old horse..help plz

$ iwconfig

lo       no wireless extensions.

eth0  no wireless extensions 

wlan0 IEEE 802.11g ESSID:off/any
            mode: Maanged Frequency: 2.412 Ghz Access Point: Not-Associated
            Bit Rate:54 Mb/s
            Power Mangement min timeout : 0us  mode: All packets recieved
            Link Quality:0   Signal Level:0  Noise Level:0
            Rx invalid nwid:0   Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0

help is needed asap

---

### Post by warfacegod on 2010-01-28
iwlist generally works better as:

```
sudo iwlist scanning
```

Go to:

System> Admin.> Hardware Drivers> and activate the recommended wireless driver, if one is listed.

---

### Post by Mariane on 2010-01-28
iwlist scanning

lo interface doesn't support scanning
eth0 interface doesn't support scanning
wlan0 no scan results

Mariane

---

### Post by warfacegod on 2010-01-28
> **Mariane said:**
> iwlist scanning

lo interface doesn't support scanning
eth0 interface doesn't support scanning
wlan0 no scan results

Mariane

Did you type sudo first?

And did you check Hardware drivers for a recommended driver?

---

### Post by Mariane on 2010-01-28
Sorry I'm late in answering. 

I've got my driver now, it wasn't the case before. And yes I did type this as root, I just omitted to write it down here. 

Before I got my driver wifi-radar just exited, now it runs but I have not been able to figure out the correct settings for it. 

WIFI Options:
- Mode: auto
- Channel: auto
- Key (I have that)
- Security: no

No WPA

Automatic network configuration (DHCP)

Connection Commands: none

Something has to be wrong in all that, but what??? 

Mariane

---

### Post by warfacegod on 2010-01-28
Is the Encryption on the router off?

---

### Post by Mariane on 2010-06-07
The router encryption is always off. 

The answer was to type:

```

sudo dpkg-reconfigure wifi-radar

```

Mariane

---

