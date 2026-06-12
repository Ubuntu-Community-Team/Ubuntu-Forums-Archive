---
title: "Changed Authentication mode and now it won't boot"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by omansf on 2008-02-26
Hi All

Ive just installed my first Ubuntu and am very pleased. 
IBM X20 all hardware is (was) working until i tried to change the authentication mode of my Wireless Network card. Its a TrendNet TEW-301PC using texas driver and works like a charm under WEB. But setting it to WPA caused the OS to stall.

After reboot nothing but black screen. Take away the wireless PCMCIA card and everything boots fine. How can i remove / reset informations about the wireless adapter?

Can anyone give me a repair suggestion?
Thanks in advance.

Regards omansf

---

### Post by ntetreau on 2008-02-26
I copy this from the Ubuntu NetworkManager [wiki]("https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-ff9d8283e9943f3acf81df57073fe7590fbe37a8"), you might find more information there.  In the mean time, boot without the pcmcia card, go into gconf-editor following these instruction and remove your network.  Next time you try to connect to it, you will be asked again about network security and passphrase.

Navigating gconf-editor

Once you have connected to a network, even unintentionally, it's configuration details will have been stored in the GConf registry. This means that Network Manager will automatically reconnect to any network it finds nearby that is stored in GConf. The order of preference is based on the time you last connected. To access these details open gconf-editor.

gconf-editor

Now navigate to system -> networking -> wireless -> networks. There you will find separate directories for each network under it's network name (essid).
Preventing automatic connection to particular networks

In gconf-editor select the essid of the network you wish to edit. For each of the keys, right-click the key and select Unset Key... Once done quit gconf-editor. If you reopen gconf-editor, you will now see that the network has been removed. This will only prevent automatic connection to a network, you can manually re-connect at any time.

---

