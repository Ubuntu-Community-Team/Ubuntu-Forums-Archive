---
title: "Can't get internet through windows"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by xlinuks on 2007-10-19
Hi,
I installed Ubuntu (Gutsy) for the first time in our office. At home there's no problem with the internet cause I have direct DSL modem connected to it through DHCP.
But here in the office my computer is supposed to connect to the internet through another computer which runs windowsXP SP2.
Here's a screenshot of the "Internet Settings" on my computer when I boot to windows:
[http://xlinuks.googlepages.com/windows_ip.png](http://xlinuks.googlepages.com/windows_ip.png)

Please letl me know what settings needs Ubuntu.
I tried using a static address of 192.168.0.4, with mask 255.255.255.0 and main gateway 192.168.0.1 but it didn't seem to work. Besides there's a "Roaming Mode" - does it have to be enabled?
Maybe I need to install kindof Samba? If so - how am I supposed to do it since I got no connection to the internet..

---

### Post by Hero of Time on 2007-10-19
Does the computer you need to connect trough have a second NIC? If so, is Inteternet Sharing enabled? If so, all you need is connect your Ubuntu machine to the second interface and get a dhcp address. That's all. You can also try to set a manual IP, put it in the correct subnet, set the right gateway and most important, set the correct DNS server. Either check your Network Manager, or /etc/resolv.conf if the address is correct.

---

### Post by xlinuks on 2007-10-19
It doesn't have a second NIC.
If I do as you said - set a manual IP, in what range should it be, something standard like 192.168.xxx.xxx? And the second question: in this case how can I detect the "correct DNS" (a simple example woule be great).

---

### Post by Hero of Time on 2007-10-19
The IP range need to be withing the network itself. Since you use 192.168.35.x, you give the linux box 192.168.35.x. As for the DNS, best to point it to the default gateway or the DNS servers you already have in Windows. Just try and see what settings work.

---

