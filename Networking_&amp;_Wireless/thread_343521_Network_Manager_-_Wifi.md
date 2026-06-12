---
title: "Network Manager - Wifi"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by Village on 2007-01-21
Hi there,

I'm having a real headache setting up wifi access on my desktop (running Ubuntu 6.10). It did used to work but I've had to reinstall, previously it just started working once I put Kubuntu and wifi-radar onto the machine, Network Mananger never did seem to work. I've tried that again but no luck this time.

I have a RT250 based card (Belkin Manufacture F5D7000)

This time I've also added WPA2 though a Netgear router (DG834N)

I don't know if its the WPA or the Network Manager, under wifi-radar I can see the network but I can't get access to it,

Is there a good guide somewhere for WPA on Ubuntu or Kubuntu?

Thanks in advance,

Village

---

### Post by phossal on 2007-01-21
First, you should try connecting to a non-protected router. In other words, disable WEP/WPA until you have a working connection.

Second, you can issue configuration commands via *sudo iwconfig*. Google iwconfig if you don't know its arguments. Then, when you've issued the proper iwconfig statement, issue:

```
sudo dhclient wlan0[COLOR="DimGray"][SIZE="1"](where wlan0 is *your* wireless interface.)[/SIZE][/COLOR]
```

---

### Post by Village on 2007-01-23
Thanks for replying;

I've disabled all wifi security and I was able to connect though the wifi, so I know that works. I then switched on MAC address filtering and was still connected (no reason why I shouldn't be). 

Then I switched on WPA-PSK and no luck. I've got a network key (ASCII) do I put the key in or use wpa_passphrase to get the full key (is that what a hex key is?) and paste that in somewhere?

Finally even though I was able to connect over my wifi under kubuntu (wireless assistant) I still can't in Network Manager, GNOME, it still just shows wired networking when I click on it.

Any ideas?

Thanks a lot,

Village

---

