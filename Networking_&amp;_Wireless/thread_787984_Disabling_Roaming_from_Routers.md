---
title: "Disabling Roaming from Routers"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by MaddMatt on 2008-05-09
Hey All - interesting network question for you guys! 

The network that I'm connected to contains many wireless access points, and uses a method known as roaming within those access points - that is, for various reasons, one access point can pass my connection to another if it deems it necessary. HOWEVER, this is causing large problems for me in ubuntu- either because Hardy isn't handling this exchange properly, or some other reason I haven't figured out yet. The network DOES check to see if the other router can see me at all, so what I'm wondering is if there is a way to either disable this roaming mode on my end, or lock the connection to a specific access point? In other words, not respond to the attempted connections from other APs so that the network is tricked to only using one?

Background: Using nm-applet to do all of the networking (since it's PEAP) and running a TrendNet TEW-443PI, Madwifi-NG, with a cantenna. 

Here's a sample of what the roaming looks like in the log:

```

{excerpt from daemon.log}
May  8 23:24:56 Sparta NetworkManager: <info>  ath0: link timed out. 
May  8 23:25:48 Sparta NetworkManager: <info>  Supplicant state changed: 0 
May  8 23:25:56 Sparta NetworkManager: <debug> [1210310756.870282] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:0B:86:51:79:A0 to 00:0B:86:51:78:00 on wireless network 'tigernet2' 
May  8 23:26:02 Sparta NetworkManager: <debug> [1210310762.870256] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:0B:86:51:79:A0 to 00:0B:86:51:78:00 on wireless network 'tigernet2' 
May  8 23:26:08 Sparta NetworkManager: <info>  ath0: link timed out. 

```

As you can see, I never am successfully roamed, but my connection drops quite frequently as a result. VERY annoying, and may be responsible for some system hangs I've been having.... Any insight would be appreciated
Thanks!

-Matt

---

