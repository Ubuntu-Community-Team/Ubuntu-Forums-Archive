---
title: "Help with Network-Manager Setting to Have VPN Auto-Connect"
date: 2018-07-27
forum: Networking &amp; Wireless
---

### Post by j.kemp on 2018-07-27
Hi everyone,

I would like to have my VPN auto-connect upon login. 

I can achieve this in 16.04 using network-manager. By selecting "Automatically connect to VPN when using this adapter" then selecting the VPN profile to use under the "general" tab of the ethernet adapter.

Now under 18.04 there is no setting like this that I can find.

What file can I edit to make this happen? So when I log in the VPN auto-connects? The network-manager looks different. I'm using the communitytheme in Gnome.

Thanks in advance to anyone who can point me in the right direction.

James

---

### Post by j.kemp on 2018-07-27
Hello,

I found a solution in this thread: [https://askubuntu.com/questions/1048352/bionic-how-can-i-automatically-enable-vpn-on-a-network-connection?noredirect=1](https://askubuntu.com/questions/1048352/bionic-how-can-i-automatically-enable-vpn-on-a-network-connection?noredirect=1)


I had to run nm-connection-editor and the setting was there, but not from the network-manager. That has changed in 18.04.

James

---

