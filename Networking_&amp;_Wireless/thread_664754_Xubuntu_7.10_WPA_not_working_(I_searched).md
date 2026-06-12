---
title: "Xubuntu 7.10 WPA not working (I searched)"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by ilovebsod on 2008-01-11
sorry for cross posting, but I figured this topic would get more attention here

the original thread is here

[http://ubuntuforums.org/showthread.php?t=663177](http://ubuntuforums.org/showthread.php?t=663177)


I found several posts regarding these 2 problems, but they were all for previous versions of Ubuntu and none of the solutions worked for me (also many steps were different or not available because of version differences).

the most important is that WPA will not work. If I try to connect to a WiFi network detected using the Roaming method I don't even get an option for WPA (just WEP64/12. If I manually try to connect I am able to select WPA/TKP and it attempts to connect but eventually fails. If I go into the manual network settings and turn off Roaming and enter in the SSID/passphrase/DHCP the same occurs.

wpasupplicant is already installed, not sure what else I'm missing.

when I try the connection method in your post (i.e. selecting the essid from the drop down after clicking on Network-Manager) I get prompted to enter the security info for my wifi network. the only encryption options I'm allowed to select from are
WEP64/128 (passphrase, hex or ASCII)
LEAP

no WPA

I turned WEP128 on on my router and was able to connect, also turned off encryption and could connect

if I go back to the network-manager drop down where it lists the wifi networks I can select 'Connect to other wireless network....', If I select this I can manually input an essid and select WPA as the encryption type and input my passphrase, but it won't connect to the network.

I also tried replacing the contents of /etc/network/interfaces with those listed in your thread, but that rendered the wireless features in network-manager inoperative (i.e. they didn't even show up any more).

I thought maybe I had screwd something up with all the fixes I had tried so I reinstalled Xubuntu today and the same behavior occurs.

Thanks in advance!

---

### Post by Cammy on 2008-01-11
Edit: Sorry, just noticed you said Xubuntu.  My bad.

---

### Post by dolphin_oracle on 2008-01-11
mentioning what wireless card you are using may help. 

at a terminal type

$lspci

and look for a line describing your wireless card and post it here.

---

