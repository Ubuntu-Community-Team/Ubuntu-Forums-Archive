---
title: "Cannot connect to VPN before login"
date: 2018-01-23
forum: Networking &amp; Wireless
---

### Post by godatum2 on 2018-01-23
I am trying to connect to my VPN before logging in but get a "the VPN connection failed because there were no valid VPN secrets" error. I am using 16.04. It does however work when I am logged in. My VPN uses a user cert, CA cert and private key configured in he network manager. "All users may connect to this network" is checked.

---

### Post by TheFu on 2018-01-23
Don't use network-manager.  Setup the VPN to run just after networking starts at boot.

That means you can't use any GUI.

I have openvpn running on multiple devices without any GUI. Don't remember it being very hard, but I'm not a point-n-click user.

---

### Post by godatum2 on 2018-01-24
> **TheFu said:**
> Don't use network-manager.  Setup the VPN to run just after networking starts at boot.

That means you can't use any GUI.

I have openvpn running on multiple devices without any GUI. Don't remember it being very hard, but I'm not a point-n-click user.

Thanks for the suggestion. Unfortunately we don't need to VPN running all the time as sometimes we plug in directly to the network. So if the VPn auto-connects, the user will need to manually disconnect?

---

### Post by TheFu on 2018-01-24
> **godatum2 said:**
> Thanks for the suggestion. Unfortunately we don't need to VPN running all the time as sometimes we plug in directly to the network. So if the VPn auto-connects, the user will need to manually disconnect?

So you want to connect to the VPN at boot, but only sometimes?  
How do you suppose to control whether that happens or not?  
The requirements conflict, it appears.

But many things CAN be scripted.  I use different system network settings which depend on the network I'm connected onto - wired ethernet or wifi.  You can probably do something similar, if you can determine when using VPN is necessary and when it isn't with a script.

---

### Post by godatum2 on 2018-01-25
> **TheFu said:**
> So you want to connect to the VPN at boot, but only sometimes?  
How do you suppose to control whether that happens or not?  
The requirements conflict, it appears.

But many things CAN be scripted.  I use different system network settings which depend on the network I'm connected onto - wired ethernet or wifi.  You can probably do something similar, if you can determine when using VPN is necessary and when it isn't with a script.

Sorry i did not make myself clear. I am saying the VPN does not connect at all on the login screen. I want the user to connect to the VPN manually before logging in.

---

### Post by TheFu on 2018-01-25
> **godatum2 said:**
> Sorry i did not make myself clear. I am saying the VPN does not connect at all on the login screen. I want the user to connect to the VPN manually before logging in.

I know of no way for a user to do anything on a system that doesn't have them logging in.

---

### Post by godatum2 on 2018-01-25
> **TheFu said:**
> I know of no way for a user to do anything on a system that doesn't have them logging in.

:( In Ubuntu 12.04 I can connect to the VPN before logging in, so I don't understand why I cannot in 16.04.

---

