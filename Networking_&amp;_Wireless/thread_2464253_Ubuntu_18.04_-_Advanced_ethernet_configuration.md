---
title: "Ubuntu 18.04 - Advanced ethernet configuration"
date: 2021-06-27
forum: Networking &amp; Wireless
---

### Post by isaak83 on 2021-06-27
hi all,
i recently installed Ubuntu, I have searched google, and ubuntu forums but could not fiind an answer that worked,
how do i set like in windows my advanced ethernet adapter settings such as:
adaptive inter-frame spacing -> disabled
interrupt moderation rate -> off
Receive buffers -> 2048
transmit buffers -> 2048

I found some info about installing networkmanager but it does not launch, trying to resolve it does not work. 

Much appreciated,

---

### Post by TheFu on 2021-06-28
Desktop or Server?

I'll use the shotgun method of answering, because I don't actually KNOW the answer.

**ethtool** is commonly used for many NIC settings. Some are controlled by the kernel, like buffers. Those are in sysctl.conf/sysctl or under pseudo-file systems like /proc in specific "files".

And some are controlled by the driver options. These would be specified where the driver gets loaded, often /etc/modprobe.d/

Network-Manager ain't the place. That is certain, especially in a server install, which wouldn't use network-manager at all.  On servers, the network conf is controlled via either netplan or the old-school "interfaces" file.  Which your 18.04 system uses would depend on whether it was an upgrade or a fresh Server installation.  My 18.04 Servers that were upgraded all still use ifupdown ... which means the "interfaces" file.  But I don't think buffers are specified in there. 

[https://stackoverflow.com/questions/7865069/how-to-find-the-socket-buffer-size-of-linux](https://stackoverflow.com/questions/7865069/how-to-find-the-socket-buffer-size-of-linux) provided some options. All seem to work for the tx and rx buffers.

I was unable to set the adaptive-rx on. The available and installed driver doesn't support it.

---

