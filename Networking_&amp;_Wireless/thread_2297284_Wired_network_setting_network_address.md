---
title: "Wired network setting network address"
date: 2015-10-02
forum: Networking &amp; Wireless
---

### Post by mike.franky on 2015-10-02
Hi,

I have just installed the new version of Kubuntu (15.04) in parallel to Windows 7 on my university desktop. The installation went very well and everything was working fine. At some point I booted to Windows to check something and when I booted back to Kubuntu, I had not internet. In the system tray the icon for the network has a circulating animation in front of it suggesting that it is still trying to connect. When I click on it, it says "Wired connection 3" and underneath it says "Setting network address". This never goes away and a connection is never established. The wired connection works fine on Windows.

The ifconfig command suggests shows that the interface no longer has an inet address (although there is a inet6 address). After a number of unsuccessful attempts to resolve the issue (by changing the /etc/network/interface file to automatically setup my interface to dhcp), I decided to re-install Kubuntu. This time, during the installation, I had no connection. 

Can anyone figure out what is going on?

Thanks in advance for any help.

---

