---
title: "Xubuntu - Connecting to a Wired Network 802.1x P(EAP) - help please"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by drspastic on 2007-09-13
Hi there

I'm trying to connect to my University network. I am using **Xubuntu** on a quite old **Compaq Presario 2100 Laptop**, _since neither standard Ubuntu or Kubuntu would instal_l (not sure why, but maybe due to not enough RAM).

I have looked into various HOWTOs on using *wpa_supplicant* and *xsupplicant* but there's no clear step-by-step explanation anywhere as to what steps are required to set up the network or the configuration file(s).

To access the same network through XP, I only have to specify **MAC address**, a Username and Password, and Proxy details and XP does the rest for me.

Compared to Ubuntu, which I've used on a few different computers, Xubuntu seems a lot harder to use. A lot of the tools I'm familiar with are not present, and when I look in Add/Remove it says they are 'not available for installation' on my laptop, but doesn't say why. e.g. Searching/Indexing, Configuration Editor, Network Manager etc..

Can anyone help me please


1. How do I set the right configuration for SSID, MAC address and so forth?

2. How can I install some software to alter my network configuration, or get a script to follow to enter the correct commands to set up the connection?

3. How do I connect to the DCHP server using EAP authentication?

4. Why is Xubuntu missing so much functionality compared with Ubuntu? 

If anyone could shed some light on this issue regarding 802.1x, supplicants, and the rest I'd be very grateful. It's all a bit complicated, yet again. Why can't Ubuntu have decent documentation on this kind of thing?

If I could install Ubuntu, I think it would work, but it won't let me.

---

### Post by staticsage on 2007-10-29
If you connection requires MSCHAPV2 like mine does, your wpa_supplicant.conf should look something like this:

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=root
ap_scan=0
network={
key_mgmt=IEEE8021X
eap=PEAP
identity="username"
password="password"
phase1="peaplabel=0"
phase2="auth=MSCHAPV2"
}
```

You would then run wpa_supplicant ```
sudo wpa_supplicant -ieth0 -Dwired -c wpa_supplicant.conf
```

making sure you select the correct interface (eth0) and point to your config file. 
If you run that followed by a ```
sudo dhclient eth0
```

then you will be in business.

Does Xubuntu have NetworkManager, or is that gnome only? Let me know if you need more help.

---

