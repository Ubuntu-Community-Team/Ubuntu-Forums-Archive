---
title: "Netgear Wireless PCI adapter - Connecting to a WPA encrypted network"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by JayFM on 2006-11-05
Dear Ubuntu Forums Users,

I have recently set up a dual boot with ubuntu and WinXP, and have had some trouble connecting to a WPA-PSK (TKIP) Secured network. The network card works fine in windows, although it required a CD install.

I have a Netgear 108 Mb/s Wireless PCI adapter (WG311T), which Ubuntu can see, though it can only connect to WEP secured networks. I am usually unable to get an ethernet connection, as my nearest ethernet cable can only reach about 1/5 of the way to my computer.

I have tried the defult network manager, by going system > administration > networking, but have not installed any other periferals. I have heard that you need to use something like 'sudo apt-get install network-manager-gnome', but it returns an error which i don't know about. I also heard of using ndiswrapper, or something to replicate the windows driver.

Please keep in mind that i'm very new to linux, so i'm sorry if i appear to be a bit 'newbie'. I have next to no experience using the terminal, but i'm keen to learn.

Thanks for your help,
-Jay.

---

### Post by wieman01 on 2006-11-06
Let's drop NetworkManager because the tool is not perfect. Are you ready to do some manual work from command line? If yes, then I can help.

Open a terminal and type these commands (then press enter):
> iwlist scan
> sudo gedit /etc/network/interfaces
When ask for your password, please enter your default password.

I need the output of the first command. Highlight the resulting text/output with you mouse (that's "copy"), then copy it to share it with us (crtl + v = "paste").

As for the second command, a window will open with some stuff in there. Simply copy & paste it in the used (Windows) manner. Then I can help you.

Are you using DHCP?

---

