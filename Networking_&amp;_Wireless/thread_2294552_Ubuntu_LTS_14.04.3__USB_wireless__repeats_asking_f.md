---
title: "Ubuntu LTS 14.04.3  USB wireless  repeats asking for  password"
date: 2015-09-11
forum: Networking &amp; Wireless
---

### Post by NS on 2015-09-11
[FONT=georgia][SIZE=3]
Installed  Ubuntu LTS 14.04.3 (the Xubuntu version 14.04.3)  64-bit version. After many hours of reading prior posts in this forum, got my wireless USB installed (Linksys AE1200 N-standard).  Used ndiswrapper & Windows XP driver, as suggested in another thread.  Good news is that OS is able to recognize the USB after i used the Windows-XP driver, as suggested in another thread([http://askubuntu.com/questions/100090/how-do-i-install-the-driver-for-my-linksys-ae1200-wireless-n-usb-adapter/671564#671564](http://askubuntu.com/questions/100090/how-do-i-install-the-driver-for-my-linksys-ae1200-wireless-n-usb-adapter/671564#671564)), using ndiswrapper.  The light on the USB comes on and blinks while trying to connect to network. If i plug in the USB wireless dongle, the icon on menubar immediately shows the surrounding networks and "Enable wi-fi"  is check marked. But the problem is that I can not connect to any wireless network. When i choose my network, the light on the USB (which was ON) goes OFF for a bit, and turns ON again before I get the message box that prompts "Authentication required by Wi-fi network".  It does not matter whether I type in correct password or wrong password, the above light-pattern on the USB repeats, and the password prompt keeps reappearing. The same wireless USB was working previously on this machine, when it was running Windows-XP.  I can not even connect to the password free open wifi network provided by my ISP (called xfinitywifi).  I have attached the outputs from various commands and syslog at bottom. Please have a look at all of them, to get all needed details. After looking through them,  here are some things on my mind now:

[/SIZE][/FONT]
[LIST=1]
[*][FONT=georgia][SIZE=3]Am i supposed to list the wireless interface in /etc/network/interfaces  file ?[/SIZE][/FONT]
[*][FONT=georgia][SIZE=3]Why do i see this USB listed as 802.11g  even though this dongle is a N-standard wifi USB ? Do i need to add anything to driver  .inf file ?[/SIZE][/FONT]
[*][FONT=georgia][SIZE=3]Am i supposed to provide the password in some config file ? I thought it was enough if i supply the password, while the prompt appears, while i try to connect to network. But the output (as seen in attachment) from dmesg command has errors.[/SIZE][/FONT]
[*][FONT=georgia][SIZE=3]Why is the link quality zero (see iwconfig output) even though the router is few feet from the USB wifi dongle ?[/SIZE][/FONT]
[*][FONT=georgia][SIZE=3]My installation does not have a /etc/wpa_supplicant.conf   file, which I saw in a man page. Is this absolutely needed ?[/SIZE][/FONT]
[*][FONT=georgia][SIZE=3]Note that i have removed the ethernet addresses from the outputs given.[/SIZE][/FONT]
[*][FONT=georgia][SIZE=3]This is my first post to this forum. Please tell me if i am not adhering to any etiquette here.[/SIZE][/FONT]
[/LIST]
[FONT=georgia][SIZE=3]
I have found 2 other threads that seem to be related.  [http://ubuntuforums.org/showthread.php?t=2036445&page=16](http://ubuntuforums.org/showthread.php?t=2036445&page=16)  is for a Netgear USB  and has different chips.  [http://ubuntuforums.org/showthread.php?t=2294357](http://ubuntuforums.org/showthread.php?t=2294357)  is regarding AE1200 which i am using,  and is marked unsolved yet (at least this guy is able to connect). The wifi router is configured for WPA2-PSK (AES). I noticed in syslog that it mentions WPA instead of WPA2. Is this usual output seen in syslog for WPA2 too ? My system info below:
[/SIZE][/FONT]
[LIST]
[*][FONT=georgia][SIZE=3][The output from commands]("http://paste.ubuntu.com/12343999/").[/SIZE][/FONT]
[*][FONT=georgia][SIZE=3][Syslog  has this info]("http://paste.ubuntu.com/12344169/")[/SIZE][/FONT]
[/LIST]
[FONT=georgia][SIZE=3]Thanks for your time and help.[/SIZE][/FONT]

---

### Post by NS on 2015-09-16
Ping.....Any  ndiswrapper  experts here to comment on this problem ?

---

