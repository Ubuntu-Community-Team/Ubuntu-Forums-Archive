---
title: "Wireless not connecting automatic"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by bernt on 2007-02-15
Hi!

Running Kubuntu 6.10.

To get connected after boot I need to start Wireless assistent, type password and click on the Wireless network.

How do I make it start automatic?

Kind regards
/Bernt

---

### Post by bnuytten on 2007-02-15
First open a console. There are probably other GUI like ways to this.

Bring the wireless network interface down, adjust the configuration and bring the wireless network interface up. I assume the network name of your wireless interface is wlan0. Type ifconfig and the command line and take a good guess if you don't know the name.

```
ifdown wlan0
vim /etc/network/interfaces
*<scroll>*
auto wlan0
iface wlan0 inet static
wireless-essid linksys
address 192.168.0.6
netmask 255.255.255.0
gateway 192.168.0.1
**wireless-key s:putyoursecretSTRINGkeyhere**
[I]#for a hexadecimal key I guess you have to leave the "s:" away
#see "man iwconfig" and look for key
[/I]
ifup wlan0
```

---

### Post by bernt on 2007-02-16
Thanks for the answer.

I'm not using any encrytion or static address.

Should this do it?

```
ifdown wlan0
vim /etc/network/interfaces
<scroll>
auto wlan0
wireless-essid linksys
#for a hexadecimal key I guess you have to leave the "s:" away
#see "man iwconfig" and look for key

ifup wlan0
```

---

### Post by bnuytten on 2007-02-16
If you add one line, it is correct and should be enough to bring up the interface correctly.

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys
```

For more options: see man interfaces and man iwconfig.

---

### Post by bernt on 2007-02-16
> **bnuytten said:**
> If you add one line, it is correct and should be enough to bring up the interface correctly.

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys
```

For more options: see man interfaces and man iwconfig.


It was already there. Anything else I can check?

---

### Post by bnuytten on 2007-02-17
Let's see if we can find some kind of error message when the system boots. Please post 
```
grep wlan /var/log/dmesg
grep wlan /var/log/messages
```

If you restart the machine, what is the initial state of the wlan interface? So before you change anything of the configuration?
```
ifconfig wlan0
iwconfig wlan0
```

---

### Post by bernt on 2007-02-17
I think this is the problem but have no clue to fix it.

amanda@vv56b:~$ iwconfig eth1
eth1      802.11g zd1211  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          Link Quality=91/100  Signal level=91/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have replace wlan0 with eth1 before running the commands.

grep wlan /var/log/dmesg
grep wlan /var/log/messages

did not find anything.

---

### Post by bnuytten on 2007-02-18
Two things:
-  the SSID is not set, regardless of it specified in the config file
  you can use wifi with a blank SSID however, check your acces point for the correct setting
- more important: Access Point: Invalid
  try setting any, access point with "iwconfig eth1 ap any"
  alternatively, if you know the MAC address of your AP you can set "iwconfig eth1 ap 00:11:22:33:44:55"

If that succeeds and after a reboot for some reason the interface does not come back up correctly, you can bypass the issue with the post-up command (man interfaces).

---

