---
title: "wireless network found but cannot connect to internet"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by petteri on 2005-12-01
Sorry for the vague title.  Anyway just installed Ubuntu and during the install I think I entered in a bad IP address and now I cannot connect to the internet.  Ubuntu see my wireless network but I cannot connect to it.  I have a wireless card and a wired ethernet card installed.  I am only using the wireless card.  Both are listed in Network settings as active. The default gateway field is blank, but even if I change it nothing hapens. I have DHCP activated.  In the initial set up though I typed in 198.168.1.1 for the DNS server, when it should have been 192.168.1.1. Any ideas on how I can "reset" all of these settings to the correct ones?  I have tried to edit the /etc/network/interfaces file, but I don't really understand what I'm doing here...

Thanks for any help you can provide!

Peter

---

### Post by jafenske on 2005-12-01
This worked for me... It's not a very good permanent fix!

```
sudo dhclient ath0
```

change ath0 for whatever your wireless card is called eth0, eth1, wlan0... whatever.  I use wpa supplicant and madwifi and I been reading that there is a  bug.  There is a patch but I haven't tried it yet.

---

### Post by petteri on 2005-12-01
[QUOTE=jafenske]This worked for me... It's not a very good permanent fix!

```
sudo dhclient ath0
```

change ath0 for whatever your wireless card is called eth0, eth1, wlan0... whatever.  I use wpa supplicant and madwifi and I been reading that there is a  bug.  There is a patch but I haven't tried it yet.[/QUOTE]

That didn't work, but thanks!

---

### Post by cwaldbieser on 2005-12-01
[QUOTE=petteri]Sorry for the vague title.  Anyway just installed Ubuntu and during the install I think I entered in a bad IP address and now I cannot connect to the internet.  Ubuntu see my wireless network but I cannot connect to it.  I have a wireless card and a wired ethernet card installed.  I am only using the wireless card.  Both are listed in Network settings as active. The default gateway field is blank, but even if I change it nothing hapens. I have DHCP activated.  In the initial set up though I typed in 198.168.1.1 for the DNS server, when it should have been 192.168.1.1. Any ideas on how I can "reset" all of these settings to the correct ones?  I have tried to edit the /etc/network/interfaces file, but I don't really understand what I'm doing here...

Thanks for any help you can provide!

Peter[/QUOTE]

Can you just change it through the GUI under the Admin -> Networking menu?

---

### Post by petteri on 2005-12-01
Yes I can change the settings there but it doesn't seem to affect anything.  I get the "spinning circle" and then I try to connect and can't.  If I try to set up a static IP then under the connection properties program (added to the toolbar) I can see the IP address (192.168.1.101) and subnet 255.255.255.0 and the broadcast address (what is this?) 192.168.1.255

I ran iwconfig and my network was listed correctly. Is there a way I can reinstall the networking support to start from a clean slate?

---

### Post by gruepig on 2005-12-01
DNS settings are in /etc/resolv.conf.  Either correct the IP, or if you're running DHCP, you can just remove the nameserver line entirely (though you don't have to).  As for your other network settings (IP, netmask, network address, broadcast address), modify /etc/network/interfaces or go the networking GUI and set your ethernet card to use dhcp (e.g., 'iface eth0 inet dhcp').

---

### Post by tonyw50 on 2005-12-03
is it an open connection or are you using WEP?  If WEP, be sure both access point and card can support the encryption level you'rs using.  You may need to step down the encryption level.

---

