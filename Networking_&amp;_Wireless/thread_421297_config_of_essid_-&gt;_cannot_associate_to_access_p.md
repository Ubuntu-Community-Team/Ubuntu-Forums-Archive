---
title: "config of essid -&gt; cannot associate to access point"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by cyber_bushi on 2007-04-24
Hi guys,

I've got a imho pretty mysterious issue: since I upgraded to feisty i cannot access the university wlan anymore. That's so mysterious cause it works with a os of a company from redmond.
Anyways, I configure:
```
sudo iwconfig eth1 essid start
```
to access the UNENCRYPTED net 'start'. But I cannot associate with the access point. Using another unencrypted net there 'unifunk1' it works immediately. Under RedmondOS all networks work. So my question is : does anyone have a clue what's going on?
Below my config, for more just post.

```

Telspci:
02:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

hot33331@x20:~$ egrep -v "^$|^#" /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
hot33331@x20:~$ egrep -v "^$|^#" /etc/hosts
127.0.0.1       localhost
127.0.1.1       x20
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhostsxt

```

I will post iwconfig output but forgot to save it while i was at uni ... but it just shows not-associated in the ap-section and the correct ssid.

Thanks,

cb

---

### Post by bnuytten on 2007-04-24
One. Shouldn't you use wlan0 in stead of eth1. Well anyway...

Two. Check the man page of iwconfig. You may have already associated with another acces point. try adding "ap any" to your command.

Three. The WLAN is MS powered?? Is it an "Ad Hoc network" or does that Redmond company make network devices now?

---

### Post by cyber_bushi on 2007-04-24
One: no, it's eth1, i'm sure, i used it before.
two: there's no mac address in the ap-section so i'm definately not associated to any ap
three: god help us, no! the wlan is fortunately not ms-powered... i am so desperate, I used win eXPensive to try if it works there (connect from my notebook to the ap) or if it is a hardware or driver problem. But since other wlan's work it shouldn't be a hardware or driver problem and since it works under win it should not be a mac exclusion or something like that.... maybe that ap doesn't like linux :(

but thanks for your quick help though...

---

### Post by bnuytten on 2007-04-26
> **cyber_bushi said:**
> One: no, it's eth1, i'm sure, i used it before.
two: there's no mac address in the ap-section so i'm definately not associated to any ap
three: god help us, no! the wlan is fortunately not ms-powered... i am so desperate, I used win eXPensive to try if it works there (connect from my notebook to the ap) or if it is a hardware or driver problem. But since other wlan's work it shouldn't be a hardware or driver problem and since it works under win it should not be a mac exclusion or something like that.... maybe that ap doesn't like linux :(

but thanks for your quick help though...

My last advice would be... Bring the wireless interface up (ifup eth1). And configure ALL the settings you find in man iwconfig manually and try pinging your access point/router while you're at it... Use iwlist eth1 scanning to discover the MAC address of your access point.

Some sample code to get you started:
```
iwconfig wlan0 essid "linksys" channel 11 mode Managed ap 00:13:A0:CC:72:B3
```

---

