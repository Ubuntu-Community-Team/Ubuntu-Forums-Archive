---
title: "Xenial 16.04 - Could not find VPN plugin service for 'org.freedesktop.NetworkManager."
date: 2016-04-27
forum: Networking &amp; Wireless
---

### Post by felgro on 2016-04-27
Hello, 

I installed OpenVPN as per instructions given by privateinternetaccess.com smoothly with no errors. My networkmanager VPN connections section links all their access points. Connecting to any gives a shared secret error. Going into connection editor and attempting to edit any of the access points gives the following error -

```
Could not find VPN plugin service for 'org.freedesktop.NetworkManager.openvpn'
```

OpenVPN service is running, but no plugin service present. Searching syslog for VPN errors gives this message -

```
** Message: vpn: (openvpn,/usr/lib/NetworkManager/VPN/nm-openvpn-service.name) file "/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-vpn-plugin-openvpn.so" not found. Did you install the client package?
```

There is no vpn-plugin-openvpn.so anywhere on system. Google not much help. I'm pretty much lost here. Any pointers?

---

### Post by pegngary2 on 2016-04-27
Same problem here.

---

### Post by felgro on 2016-04-27
> **pegngary2 said:**
> Same problem here.

With PrivateInternetAccess? If so, I have a workaround.

---

### Post by Adam_Dobrawy on 2016-04-29
> **felgro said:**
> With PrivateInternetAccess? If so, I have a workaround.

Same problem here. No PrivateInternetAccess, private non-commercial openvpn.

---

### Post by creurlas on 2016-04-29
> **felgro said:**
> With PrivateInternetAccess? If so, I have a workaround.

Not wishing to hijack this thread, but I have had this issue with PIA. Would you mind sharing your workaround?

I suppose there may be a slim chance that it would help the OP?

---

### Post by holden2 on 2016-04-30
I ran in to the same problem with a vanilla install of 16.04 Ubuntu

I found this blog from a Google search
[http://www.regtechsupport.com/linux-and-open-source-software/34-pia-linux-mint](http://www.regtechsupport.com/linux-and-open-source-software/34-pia-linux-mint)


I tried the following command from that blogpost and it worked for me

```
sudo apt-get install network-manager-openvpn-gnome
```

---

### Post by nicknefarious on 2016-06-06
Same problem as the OP.
I can confirm that holden2's solution above works just fine.
As suggested in the blog he links to - [http://www.regtechsupport.com/linux-and-open-source-software/34-pia-linux-mint]("http://www.regtechsupport.com/linux-and-open-source-software/34-pia-linux-mint")

---

### Post by crankyoldbugger on 2017-02-25
Holden2's message (#6) worked for me.

Ubuntu 16.10
PIA

---

### Post by ianwu on 2017-04-28
it works for me

 apt-get install network-manager-l2tp-gnome

---

