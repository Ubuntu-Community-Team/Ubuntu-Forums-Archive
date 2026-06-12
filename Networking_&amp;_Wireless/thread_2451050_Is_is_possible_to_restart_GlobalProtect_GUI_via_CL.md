---
title: "Is is possible to restart GlobalProtect GUI via CLI?"
date: 2020-09-25
forum: Networking &amp; Wireless
---

### Post by dougfir2 on 2020-09-25
Not sure if this is the right forum, pointers welcome. Tag suggestions welcome.
I am using a VPN with Palo Alto Networks and GlobalProtect. Ubuntu 18.04.
When I login I am prompted to sign in via Okta before clicking 'connect' on the small GlobalConnect Gui. This works and I am able to connect.
However, if I have been logged out for a while, e.g. overnight, then when logging back in I get an endless 'connecting' message on the Gui and am unable to connect. If I restart, all works fine.
To save me from restarting I wondered if there was a way to restart the GlobalConnect Gui from the terminal?
I posted the same on reddit [here]("https://www.reddit.com/r/paloaltonetworks/comments/izmqup/infinite_connecting_on_globalprotect_app_on/"). I was told to try the following:
```
`**sudo systemctl restart gpd.service**`
```
Outcome: I lost the vpn connection and in the upper right app GlobalProtect tool like in the screen, it still says 'connected'. I tried pressing 'disconnect' and now I have an indefinite 'disconnecting' message!
I then tried:
```
**globalprotect disconnect**
```
Outcome: 
```
    
globalprotect disconnect
Cannot parse your input. 
The valid CLI commands that you can now use are:collect-logimport-certificatelaunch-ui

```

Is there a way I can restart the Global Protect gui from the command line?

---

### Post by TheFu on 2020-09-26
For commercial products, best to ask for help through their support channels.
Most of the people in these forums won't have much direct experience with commercial programs. My old job forced only commercial solutions onto me (legal was afraid of F/LOSS lawsuits), but that was over a decade ago.

Perhaps the better answer is to find a *timeout* or *keepalive* parameter so the connection doesn't drop overnight?

---

### Post by dougfir2 on 2020-09-27
Makes sense, I'll post at Global Protect forum

---

