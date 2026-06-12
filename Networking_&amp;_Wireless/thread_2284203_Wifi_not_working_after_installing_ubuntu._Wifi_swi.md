---
title: "Wifi not working after installing ubuntu. Wifi switch ON not working."
date: 2015-06-27
forum: Networking &amp; Wireless
---

### Post by priyanjan2 on 2015-06-27
Hi, 
today for the first time i have installed ubuntu (14.04 LTS).

I am not able to connect to wifi.
It says wifi is disables (by external switch and my wifi button is also not working.)
I have searched for silution but could not get any.
I have also read the two "stick post" before posting here.
I could not find my pci.id  in  the thread, [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) 

The details for my system are: 

**02:00.0 Network controller [0280]Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01) **

And result with **rfkill list **is as below.
[B]0: phy0: Wireless LAN 
            Soft blocked  : no
            Hard blocked : yes[/B]
[B]1: hp-wifi: Wireless LAN 
            Soft blocked  : yes
            Hard blocked : no
[B]2: hp-bluetooth: Bluetooth 
            Soft blocked  : yes
            Hard blocked : [/B]**no**[/B]
[B][B]2: hci0: Bluetooth 
            Soft blocked  : **no**
            Hard blocked : [/B][/B]**no**


Pleae help me as soon as possible.:cry:[-o

---

