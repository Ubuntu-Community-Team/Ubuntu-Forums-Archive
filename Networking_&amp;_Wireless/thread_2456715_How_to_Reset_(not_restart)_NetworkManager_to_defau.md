---
title: "How to Reset (not restart) NetworkManager to default settings?"
date: 2021-01-17
forum: Networking &amp; Wireless
---

### Post by illmortal on 2021-01-17
Hello, 

I'm on a fresh install of Ubuntu 20.04.1 LTS with GNOME desktop manager. 

I'm having an issue where for some reason my ethernet adapter - eno1 is configured with incorrect IP settings. 
[Here is my Pastebin showing ifconfig results]("https://pastebin.com/Dxu14Upm")

[NetworkManager Pastebin]("https://pastebin.com/dJbdXD9t")

[Running gnome-control-center display]("https://pastebin.com/jc9MTWGf")

[Here's my nmcli]("https://pastebin.com/H9cVJseq")

This is a headless Ubuntu box, I'm currently remoting into it via RDP session. Once this is resolved I'd like to move onto getting VNC working as I'm logging into a black screen. Apparently will only work with SSH. However this IP settings issue is a more pressing matter.

---

### Post by simon-webb on 2021-01-21
If you can't edit your networks through GNOME (on my XFCE desktop it's as easy as right-clicking on the networking panel indicator, choosing "edit connections"), you can edit them directly as text files under the /etc directory. Under /etc/NetworkManager/system-connections you'll see your networks listed as plain, easily editable text files. You could either edit the network you want to modify (your adapter's IP settings will be assigned by NetworkManager from the specific network settings), or just delete it so that the auto-configuration for that network can be done again.

---

### Post by grahammechanical on 2021-01-21
For an ethernet connection on 20.04, open System Settings>Network. Alongside the ethernet connection is a cog icon. Click that and click Remove Connection Profile. For a wireless connection click WiFi and again click the cog icon alongside the WiFi connection and then click Forget Connection.

Regards

---

