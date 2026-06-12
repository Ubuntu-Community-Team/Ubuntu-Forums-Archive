---
title: "Acer 5101AWLMi wireless problem"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by G-start on 2007-09-23
Hi all,

I've got a problem. At home we have a static ip-address network which I need to use to have internet access. We use WEP for encryption.

The problem is as follows:
- I try to connect via gnome network manager using static ip-address. 
- There comes a screen which asks for the WEP-encryption key.
- I insert the key
- The thing tries to connect to the access point, but somehow doesn't get connected.
- After a while, the same screen apears, which asks for the WEP-encryption.

For wireless access I use the Atheros AR5BMB5 chipset, in an Acer 5101AWMLi laptop. 

Can anyone help me to troobleshoot this problem?

 
-----

By the way: via a very strange way I am able to connect to the internet. I downloaded by accident the Wireless Assistant for KDE (while using GNOME). Somehow i does get connected. The procedure is as follows:
- Via Gnome network manager I try to connect to the internet using DHCP. 
- In the screen that follows, I insert the WEP-key etc.
- Then I open a console
- I type sudo wlassistant
- Wlassistant opens
- I edit the essid of my wireless network to use static-ip. 
- Try to connect
- Get internet access. 

So, I know the system should be working, but it doesn't work in the normal way. Does anyone also know how Wireless Assistant works?

---

### Post by G-start on 2007-09-25
Problem seems to be an error in Gnome Network Manager. It uses wlan0 as networkinterface. Wireless Assistant for KDE uses instead of wlan0 the normal ath0. When using ath0, my wireless internet just works. How can I disable network manager and use somekind of script instead?

---

