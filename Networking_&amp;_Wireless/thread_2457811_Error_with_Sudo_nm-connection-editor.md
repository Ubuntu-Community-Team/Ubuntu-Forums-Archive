---
title: "Error with Sudo nm-connection-editor"
date: 2021-02-10
forum: Networking &amp; Wireless
---

### Post by rescu2000 on 2021-02-10
Hey guys,
I'm trying to make changes to my wired connections, like automatically connecting to the VPN. I can do a straight nm-connection-editor and the connection editor GUI comes up, but it won't let me change anything. So I thought I would try SUDO NM-CONNECTION-EDITOR and that gives me the follow error

No Protocol Specified
Unable to init server: could not connect" connection refused

I have gone through the update steps in the sticky before posting and that didn't help. I've also searched the web for this type of error and can't find anything this specific.

One other thing I'm trying to do is get PLEX to bypass the VPN. I have it setup up in the GUI. There is no CONFIG file in /etc/openvpn/client. If I create one in there with just route plex.tv 255.255.255.255 192.168.1.1 will that work, or do I have to create the whole VPN config file with all the settings. I really would like to just keep the GUI setup and control.

Details -
I am running this on Ubuntu 20.04 LTS
The server has a dual NIC setup and I get the same results on both NICs (deactivating one doesn't help)
Both nics are just connected to my switch

---

### Post by praseodym on 2021-02-10
Does it work with
```

sudo -H nm-connection-editor
```

---

### Post by rescu2000 on 2021-02-10
It does not. Same error message.

---

