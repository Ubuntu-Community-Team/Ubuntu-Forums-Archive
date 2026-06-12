---
title: "USB modem no longer asks to open my default keyring, so I cannot connect"
date: 2013-12-02
forum: Networking &amp; Wireless
---

### Post by rdh61 on 2013-12-02
Hi,

I am running Xubuntu 12.10 and connect to the Internet by a USB modem using Gnome PPP.

Then I started to use Ubuntu One and realised that it was not synchronising because it was looking for a connection via Network Manager. So I disabled Network Manager like this from [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager) : 

Stop network manager:

```
sudo stop network-manager
```Create an override file for the upstart job: 
```
echo "manual" | sudo tee /etc/init/network-manager.override
```

After doing that, Ubuntu One works properly, but I find that my USB modem no longer asks me for the password to open my default keyring, so the USB modem cannot be activated and I cannot connect with Gnome PPP. (I can connect using Sakis3G but it is a cumbersome procedure).

Any help gratefully received.

Many thanks.

---

### Post by rdh61 on 2013-12-05
OK, let me simplify. I cannot connect to the Internet using with mobile broadband using Gnome PPP. Can some kind soul please help me find out what is wrong and set it up properly?

Many thanks.

---

