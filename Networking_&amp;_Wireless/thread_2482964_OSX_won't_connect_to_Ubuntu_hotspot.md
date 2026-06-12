---
title: "OSX won't connect to Ubuntu hotspot"
date: 2023-01-15
forum: Networking &amp; Wireless
---

### Post by dwater on 2023-01-15
SSIA really.

I have a MacBook Pro (unfortunately) and would like it to join the hotspot I created on my Ubuntu laptop, but it persistently refuses. I have other devices that manage to connect and use the shared internet connection, so it doesn't appear to be anything to do with Ubuntu or the hotspot.

The other devices that I have successfully connected to the hotspot are: Google Pixel, Google Pixel1, Huawei Mate 30 Pro 5G, Apple iPhone 7.

Ubuntu is on 22.10, and OSX is on 13.1 (Ventura).

When I try to join using the OSX [networksetup]("https://www.unix.com/man-page/OSX/8/networksetup/") command, it tells me:

```
Error: -3912  The operation couldn’t be completed. (com.apple.wifi.apple80211API.error error -3912.)%
```

I used the networksetup command to add the network as a 'preferred' network (index 7, securitytype WPA), and that seemed to do that - ie it now appears in the GUI and in the output of `networksetup -listpreferredwirelessnetworks en0`, but trying to join it still fails, and in the same way.

Interestingly, the ubuntu hotspot shows 'security type **WPA**', and the QR-CODE has 'Encryption: **WPA**', but the dialog that OSX pops up when it fails to join shows:

```
The Wi-Fi network "bla bla" requires a **WPA2/WPA3** password.
```

IE, it seems to want a WPA2/WPA3 password, but the network is actually WPA.

One other thing...when I was initially testing, I attempted to join the pixel phones to the ubuntu hotspot by selecting the network from the UI list on the phone and typing in the password - but it didn't seem to want to join. However, when I used the phones' cameras to scan the QR-CODE on the ubuntu hotspot setting panel, they joined just fine.

It's possible this WPA vs WPA2 discrepancy is a red herring, but I'm not sure.

Any thoughts?

[EDIT] I used the `[nm-connection-editor]("https://askubuntu.com/questions/180733/how-to-create-a-wi-fi-hotspot-in-access-point-mode#:~:text=up%20and%20running!-,Advanced,-Stuff")` to edit the `hotspot` config to WPA3, and the OSX dialog changed to say that it was WPA3, but it still doesn't manage to connect (same error 3912); so I guess it isn't related to WPA/WPA2/WPA3. I also changed the password to one that was less prone to error when typed manually (ie doesn't contain a zero), but no joy.
[EDIT2] Oh, I should point out this isn't the first time I've seen this problem...I also have an old Mac Mini and that had the same problem.
[EDIT3] I found someone [asking]("https://developer.apple.com/forums/thread/692730") about a similar problem on apple developer forums.

---

