---
title: "trying to add wirless router to existing network"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by Dragonbite on 2008-08-20
I have a wired network set up with an old CPU running IPCop for firewall/router/content filtering purposes and I am trying to bring in a wireless router so I can use my laptop freely. I prefer if the wireless passes through IPCop as well, for system-wide content filtering.

```
{internet}->[DSL_modem]->[IPCop]->[switch]->[computers]
```

Is there a good source of documentation on the types of wireless security methods and which work best with Linux?

I see WPA, WEP, Wireless MAC Filtering,Encrypting, Passphrase, and other things.

It is a Linksys [[COLOR="Blue"]WRT54G2[/COLOR]]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175244179609&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=7960933028B04").

I am thinking of using MAC address filtering to only allow my laptop's MAC address to have access but is that enough?

My neighbors have open wireless signals and I hope to keep from allowing mine to be open too.

I am very new to networking and it seems to not like me very much.

---

### Post by Sooner Al on 2008-08-20
WPA2 is stronger that WPA. WEP is basically hacked and should not be used. MAC addresses are easily spoofed and are not a valid security measure. Your best off using strong encryption, ie. WPA2/WPA, and a long random ASCII key. Personally I use WPA-PSK [AES] with a 63-character random ASCII key to protect my home wireless network.

In any case use the strongest security supported by all of your wireless router and clients.

My general wireless security guidelines. Note some information is directed to MS Windows users only...

[http://theillustratednetwork.mvps.org/LAN/SoHoWirelessSecurity.html](http://theillustratednetwork.mvps.org/LAN/SoHoWirelessSecurity.html)

Online key generators...

[http://www.kurtm.net/wpa-pskgen/](http://www.kurtm.net/wpa-pskgen/)
[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

---

