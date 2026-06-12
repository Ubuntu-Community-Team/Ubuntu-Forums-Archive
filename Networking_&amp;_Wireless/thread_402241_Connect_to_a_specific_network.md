---
title: "Connect to a specific network"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by stchman on 2007-04-05
Hello all, I have gotten my laptop's buillt in wireless working.  I then enabled WPA2 encryption, enabled MAC filtering changed the SSID on my router to keep thieves out.  I find that if I turn of the SSID broadcast my laptop takes a LOT LONGER to connect to the wireless network.  So I leave it on.  I had the router randomly generated a 16 character WPA2 key, so I figure that if someone has the time and resources to crack that then he/she can come on in.  There are enough unprotected routers out there that an attacker will move on to an easier target than mine.  I am getting off on a tangent as to the purpose of my original post.

When I turn the laptop on and log in the laptop wireless seems to want to connect to the strongest non-encrypted signal.  This just so happens to be my neighbors unprotected router.  My question is how can I get the laptop to default connect to my router and not even try to connect to someone else's.  This is mostly a convenience feature as I can click on the network manager and click on my router name.

Does anyone have a simple solution for this?

Thanks

---

### Post by spd106 on 2007-04-05
I've read that it is recommended you use a minimum of 20 digits in your WPA key. The maximum goes up to something like 63.

Network Manager's default behaviour is to reconnect to the last network on start up. You can aid this by removing any other networks in gconf (assuming GNOME), as mentioned on this [FAQ]("http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ").

---

### Post by stchman on 2007-04-05
> **spd106 said:**
> I've read that it is recommended you use a minimum of 20 digits in your WPA key. The maximum goes up to something like 63.

Network Manager's default behaviour is to reconnect to the last network on start up. You can aid this by removing any other networks in gconf (assuming GNOME), as mentioned on this [FAQ]("http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ").

Ok, I guess one strategy is to set the laptop right next to the router where the signal is strongest.

Next power up the laptop and network-manager will see a VERY strong signal and try to acquire it.  Since it will have been the last network it attempted to connect to then all should be well.

Thanks

---

