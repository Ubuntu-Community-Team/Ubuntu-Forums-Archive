---
title: "VP N Network connectios"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by edentonjr on 2009-05-31
Hi everyone I am very new to Lunux and just purchased and new laptop with Ubuntu 8.04 installed. I need help setting up a VPN network connection on my laptop to connect to my Novell network and windows desktop at work.

When I tried going to system> administration > Network manager> VPN connection> under configure the VPN tab all options are grayed out.

Can someone please give me easy step by step instructions on any way to accomplish this.

please excused my being so naive, but I need Ubuntu for dummies instructions.

Thx., Earnest

---

### Post by steeleyuk on 2009-05-31
The VPN connections are plugins. If you're connecting to a Microsoft VPN then you'll need PPTP. There are other types such as OpenVPN and VPNC.

To install them all, you'll want the command:

```
sudo apt-get install network-manager-pptp network-manager-openvpn network-manager-vpnc
```

---

### Post by edentonjr on 2009-05-31
> **edentonjr said:**
> Hi everyone I am very new to Lunux and just purchased and new laptop with Ubuntu 8.04 installed. I need help setting up a VPN network connection on my laptop to connect to my Novell network and windows desktop at work.

When I tried going to system> administration > Network manager> VPN connection> under configure the VPN tab all options are grayed out.

Can someone please give me easy step by step instructions on any way to accomplish this.

please excused my being so naive, but I need Ubuntu for dummies instructions.

Thx., Earnest
I ran the command and it worked fine (no error messages), but it totally disabled my wireless device, I can't get back on my wireless network in my home. I'm replying from my windows laptop.
 
How do I get my wireless turned back on, at this point I'd just like to get back on line. The wireless icon isn't on my desktop anymore.

---

### Post by edentonjr on 2009-05-31
> **edentonjr said:**
> Hi everyone I am very new to Lunux and just purchased and new laptop with Ubuntu 8.04 installed. I need help setting up a VPN network connection on my laptop to connect to my Novell network and windows desktop at work.

When I tried going to system> administration > Network manager> VPN connection> under configure the VPN tab all options are grayed out.

Can someone please give me easy step by step instructions on any way to accomplish this.

please excused my being so naive, but I need Ubuntu for dummies instructions.

Thx., Earnest
PLEASE anybody how do I enable my wireless network device.....HELP

---

