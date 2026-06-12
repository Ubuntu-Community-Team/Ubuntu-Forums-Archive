---
title: "Gutsy loses network settings"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by watersb on 2008-01-17
I'm a Linux, Ubuntu, networking and virtual machines newbie, so don't assume too much. (I'm a self taught developer who has worked for a while on Windows machines.) Last week I built some virtual machines (VMware Workstation trial version) and installed Gutsy as the guest OS. I'm on a Dell Vista desktop, and it lives on our organisation's LAN behind a Microsoft proxy server. I successfully got an Edgy Eft virtual machine running, though I had to install ntlmaps in order to trick the proxy server into passing my web traffic through it. My network settings are remembered with that Edgy installation. However, every install of Gutsy (whether off of a Live CD, or Live DVD, or an ISO image)  has a nasty property of losing my network configuration settings. They seem to mysteriously revert to the wrong settings that come in the original installation, after some time passes. Moreover, the button to save the new network configuration (in Gutsy, but not Edgy) doesn't work, nor does the Apply button. This has happened to another guy here on our LAN too, who also installed Gutsy yesterday. I don't think it is a VM issue, it seems to be a problem in Gutsy itself. Can this be fixed soon? I very much want to do my work with Gutsy, rather than Edgy. Thanks

---

### Post by kripkenstein on 2008-01-17
> **watersb said:**
> I'm a Linux, Ubuntu, networking and virtual machines newbie, so don't assume too much. (I'm a self taught developer who has worked for a while on Windows machines.) Last week I built some virtual machines (VMware Workstation trial version) and installed Gutsy as the guest OS. I'm on a Dell Vista desktop, and it lives on our organisation's LAN behind a Microsoft proxy server. I successfully got an Edgy Eft virtual machine running, though I had to install ntlmaps in order to trick the proxy server into passing my web traffic through it. My network settings are remembered with that Edgy installation. However, every install of Gutsy (whether off of a Live CD, or Live DVD, or an ISO image)  has a nasty property of losing my network configuration settings. They seem to mysteriously revert to the wrong settings that come in the original installation, after some time passes. Moreover, the button to save the new network configuration (in Gutsy, but not Edgy) doesn't work, nor does the Apply button. This has happened to another guy here on our LAN too, who also installed Gutsy yesterday. I don't think it is a VM issue, it seems to be a problem in Gutsy itself. Can this be fixed soon? I very much want to do my work with Gutsy, rather than Edgy. Thanks

Well, just a guess, but NetworkManager might be resetting your network configuration, I've seen that happen. You can try disabling NetworkManager and seeing if the problem resolves itself. To make sure, you should remove both the applet and the processes, this should do it:
```

killall NetworkManager
killall NetworkManagerDispatcher
killall nm-applet

```
- or, just uninstall NetworkManager and reboot, but then you'd need to reinstall it later if this isn't the issue.

---

