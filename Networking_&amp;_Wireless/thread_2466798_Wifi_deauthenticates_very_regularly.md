---
title: "Wifi deauthenticates very regularly"
date: 2021-09-06
forum: Networking &amp; Wireless
---

### Post by erik070 on 2021-09-06
Going back to office I was confronted with an annoying issue that my wifi connecting keeps reconnecting every few minutes. Sometimes it takes 45+ minutes, but sometimes within 15 minutes it will reconnect 2 times.

Looking at dmesg logging I see that this line shows up each time the disconnect happens:
wlp61s0: deauthenticating from <MAC address of accesspoint> by local choice (Reason: 3=DEAUTH_LEAVING)

The connection is restored very quickly but it does disrupt any videocalls going on, and it kills any VPN connection I have (which is very annoying to reconnect and authenticate each time).

Followed some other thread ([this one]("https://bbs.archlinux.org/viewtopic.php?id=233365")) that this could be because Networkmanager service and wpa_supplicant service are trying to manage the connection both. Disabled wpa_supplicant service as advised. Restarted Networkmanager, did not see any changes in behaviour. Rebooted laptop, still the same problem persists.

I'm on a fresh install of Ubuntu 20.04.3 (installed a month ago, switched from Pop OS! to be more company compliant)

What could cause this issue? Are there more networkmanagers I should look out for? Or could have a totally different cause?

Pastebin of wireless info script: [https://pastebin.com/vmKVCVvM](https://pastebin.com/vmKVCVvM)

Pastebin of enabled services:  [https://pastebin.com/0xcsV0Qw](https://pastebin.com/0xcsV0Qw)

---

### Post by morrownr on 2021-09-06
Hello erik070,

I'll throw something out but there are much more knowledgeable people here than me:

While looking at the results of the wireless script I noticed the SSID "KPN_Guest" was shown with numerous channels... 1, 6, 11, 40 and 100. That is just what I remember without going back to look again. Some might argue with me but my opinion is that is a really bad way to set an AP up. Network Manager's (NM) job is to keep you connected but it does not always produce optimal end results when confronted with the situation you have. Many things can cause different results when a scan takes place and if all of the sudden NM decides that channel 40 is a better place to be than channel 6 then off it goes and changes networks on you and you may see what you are seeing.

The solution, if you can't reconfigure the AP, is to lock which band or channel your system is using. Now is where the smart people need to take over. Hey chili555, where are you?

---

### Post by morrownr on 2021-09-06
I think I may have found how to lock NM to a band or channel:

```
nm-connection-editor
```

That should bring up a dialog that will allow you to delete and edit connections. You might want to delete all listed wifi connections except for one and then edit it to set a fixed band and/or channel.

There may be a way to start nm-connection-editor in Ubuntu with the gui but I use a distro that is Ubuntu inside but is not gnome on the outside.

---

### Post by erik070 on 2021-09-07
I'm working in an office building, the AP's are managed by our company (one of the largest network/internet providers in our country). I guess they think this is the best setup? Not sure why they have such a large amount of channels open.

Tried nm-connection-editor and configured the connection with the AP to a set bandwidth and channel, but it still reconnects after a while. Even tried setting it to 2.4Ghz band, as the range of those bands is much higher, but still the problem persists.
Non of my colleagues experience this problem, but they are either on a Apple laptop or a Win10 laptop, I don't have any colleagues (in the building) that I know of that is using Ubuntu as well. 

Strangest part is, when I was on Pop_Os! I did not experience this issue at all (same hardware/laptop). Yes, Pop_OS! differs from Ubuntu, but didn't think it would differ this much. Thought it was mostly cosmetic and some tweaks here and there.

I will consider upgrading to Ubuntu 21.04, because the Pop_OS! versions I used in this building were based on Ubuntu 20.10 and up.

---

### Post by morrownr on 2021-09-07
I found this:

[https://wiki.archlinux.org/title/NetworkManager](https://wiki.archlinux.org/title/NetworkManager)

Maybe 8.14 could help.

---

### Post by morrownr on 2021-09-07
More info: Found the below text in an article:

*Locking on to a specific Wi-Fi radio isn’t a feature most people need all the time, but it is useful in some situations. By default, your PC will try to lock on to and use the strongest signal that’s being broadcast with a given SSID.*

*It’s easier for users if a network administrator sets a single SSID for several wireless access points instead of forcing users to re-enter Wi-Fi credentials for each AP they try to connect to (e.g.: Office_floor1 and Office_floor2). As a user moves from one location to another, their device should lock on to the closest access point. But what if you’re somewhere in between?*

*If an SSID has more than one AP with comparable signals, the networking stack on your PC will scan for the best one and switch from one AP to the other, seemingly at random. To stop this, you can “lock on” to one access point by specifying its BSSID.*

*You can “lock on” to a specific Wi-Fi radio by setting the BSSID for a connection.*
*In the Wi-Fi tab for the connection (using [COLOR=#000000][FONT=&quot]nm-connection-editor)[/FONT][/COLOR], simply select one of the BSSIDs from the drop-down menu, click Save, and reconnect to the network. Your PC should now use that specific access point.*

[I]If you still want the ability to get up and roam away from that access point on the same SSID, you can save the connection with a new name (not a new SSID!). Then, copy over all the connection details (SSID, WPA passphrase, etc.) from the other sections of the connection, but leave the BSSID option blank and save under a different connection name from the first one. One you’ve done that, you can select the “roaming” connection if you have to get up and take your laptop to a meeting, and use your preferred access point when you get back to your desk.

-----
[/I]So, I was almost right the first time. You need to set the BSSID to lock the connection, not the band or channel.

---

### Post by erik070 on 2021-09-07
I did try that, setting the BSSID but it would disconnect and then stay disconnected. When I try to reconnect it would create a new SSID name with a 1 added.

Anyhow, I upgraded to 21.04 and after that the connection did not got interrupted a single time (for 3 hours or so), or at least the VPN kept it's connection. So for me this is solved.

---

### Post by morrownr on 2021-09-07
Sounds to me like a correction to undesirable behavior was made somewhere between 20.04 and 21.04. That is good. How about marking the thread solved.

---

