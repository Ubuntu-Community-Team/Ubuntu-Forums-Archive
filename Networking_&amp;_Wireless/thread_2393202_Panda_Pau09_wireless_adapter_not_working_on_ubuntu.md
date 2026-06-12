---
title: "Panda Pau09 wireless adapter not working on ubuntu 18.04"
date: 2018-05-30
forum: Networking &amp; Wireless
---

### Post by mangrobot on 2018-05-30
Hello, I've been researching online on how to troubleshoot Panda PAU09 but I cannot seem to find a solution. They claim that it's a plug and play device on version 16.04 and 17.10 but it seems that it's not working anymore on the new lts version. I'm not sure if there's a conflict with the internal wifi card  but I'm not too sure about it since it's using intel drivers. Here's the diagnosis by running the wireless script i found on the forums. Please note that I've already upgraded my system and I've rebooted it already. Thanks in Advance

[URL="http://paste.ubuntu.com/p/XNNHWK9BC3/"]http://paste.ubuntu.com/p/XNNHWK9BC3/

[/URL][URL="http://paste.ubuntu.com/p/XNNHWK9BC3/"]
[/URL]

---

### Post by jeremy31 on 2018-05-31
I would disable wifi power management with ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*  && systemctl restart network-manager.service
```
The internal might work better.  The internal can be disable by unloading the driver ```
sudo modprobe -r iwlwifi
``` or you can prevent the module from loading at startup with ```
echo "blacklist iwlwifi" | sudo tee /etc/modprobe.d/blacklist-iwlwifi.conf
```
If you need the internal to work after using the blacklist ```
sudo modprobe iwlwifi
```

---

### Post by superguyver on 2018-06-13
I don't know why you said Panda PAU09 is not working for Ubuntu 18.04 TLS.
Panda PAU09 is called "[COLOR=#000000]wlx9cefd5fd0e53" and the internal wireless card is called "[/COLOR][COLOR=#000000]wlp3s0"[/COLOR][COLOR=#000000]in the output of iwconfig command.[/COLOR][COLOR=#000000] "[/COLOR][COLOR=#000000]wlp3s0" is connected to your network. [/COLOR][COLOR=#000000]You should see two wireless interfaces in the Network Manager. The first interface is the internal wireless card and the second one is Panda. You should disconnect the internal wireless card and connect panda to your network. Hope this helps.[/COLOR]

---

