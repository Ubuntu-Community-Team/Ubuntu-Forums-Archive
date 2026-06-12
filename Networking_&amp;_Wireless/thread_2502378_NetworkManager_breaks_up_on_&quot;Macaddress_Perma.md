---
title: "NetworkManager breaks up on &quot;Macaddress: Permanent&quot; / &quot;Cloned Adress: Permanent&quot;"
date: 2024-11-12
forum: Networking &amp; Wireless
---

### Post by bemotion on 2024-11-12
Hey,

I wanted to file a bug report, but it seems like a total hassle for me.
So I will simply post it here and someone else can take the credits for reporting it.

With Ubuntu LTS 22 and 24 using any WiFi or Wired Network and changing the Identity Settings of *Cloned Adress* to *"permanent"* breaks the NetworkManager.
Up on connecting via GUI to the wired or WiFi Device, the devices shut off leaving the Device lists in the Gnome GUI blank.

I know thats just a brief description, but as soon as I edited the netplan file manually again and delete the *macaddress: "permanent" *entry, it works again.
Ive tried that with several wireless network configurations and the wired, and the *permanent* setting always cause this behaviour.

Here are more details of the hardware configuration via System-Info Script
[https://paste.ubuntu.com/p/8WqxpZ9w6v/](https://paste.ubuntu.com/p/8WqxpZ9w6v/)

The issue should be repeatable with that hardware at least.
Maybe others will encounter it with different hardware configurations as well.

If your user experience is that after a reboot no network connection is established automatically that was previously working to auto connect, and your wired/wifi list gets blank as soon as you connect to any selected together with visible "refreshes" of Gnomes GUI and optical glitches, as well as no lists of adapters or visible WiFi reappearing after that crash up to another reboot (or maybe until restarting services), than it may be likely you set the permanent macaddress in some network and forgot about it - like me ;) Instead of troubleshooting software and reinstalling networkmanager and its cfg, maybe check your netplan yaml files for any permanent setting.

Quick help to find the corrupted file:
 [I]grep -ri "macaddress" /etc/netplan/
[/I]or
[I]grep -ri "permanent" /etc/netplan/
[/I]
Cheers

---

### Post by bemotion on 2024-11-22
Ive escalated a bug report:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/2089402](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/2089402)

---

### Post by owenfox on 2024-11-30
This issue with NetworkManager and the 'permanent' MAC address setting is a great example of how small configuration changes can lead to major functionality issues. I was working on larger systems, like learning management platforms or other critical infrastructures, and have a few ideas how help avoid such setbacks. Here is this [expert guide to implementing an lms successfully]("https://ddi-dev.com/blog/programming/main-steps-in-lms-implementation/") that provides a great framework. Main points are careful planning and troubleshooting are keys to the smooth deployment. It is something NetworkManager could definitely win from.


Would you like me to note anything about your work with networking configurations or troubleshooting methods?

---

