---
title: "NetworkManager: tethering through ethernet port needs manual off/on"
date: 2024-02-01
forum: Networking &amp; Wireless
---

### Post by foggy67 on 2024-02-01
Hello,
I am using Ubuntu 22.04.3 LTS on a Lenovo G70-80 laptop and am connected to my box through a Wifi link, which works fine.
I need to share this link to a device connected to my ethernet port (driven by the r8169 module). To achieve this, I set up the NetworkManager like this way for the ethernet link: IPV4 sharing, IPV6 sharing disabled, no security, automatic connexion, sharing allowed to all users.
When the laptop boots up, it gets the wifi connexion, sets up the Internet access very well. But it doesn't share my internet link to the ethernet port, so I have no tethering for my device.
I found this solution :  I manually switch off the ethernet link in NetworkManager and switch it manually on one or two seconds after, and then the internet sharing trough ethernet works fine.

Why does my configuration not set up this tethering automatically ? Is there a misconfiguration anywhere? Is it a bug?

I have to add that I also share at the same time my Wifi Internet  connexion through bluetooth with the blueman application (local  services). This bluetooth tethering sets up automatically and works  fine, no manual intervention is necessary. There seems to be an  interference between the two connexion sharing, between bluetooth and  ethernet. Can the bluetooth sharing taking it all?

I tried the exactly same configuration of NetworkManager in Debian 11 (I have dual boot on my laptop), and the tethering trough ethernet is set up automatically at boot time. There is no further manual intervention necessary.
So I am lost and cannot explain that behaviour in Ubuntu.


Thank you in advance for your help.

---

