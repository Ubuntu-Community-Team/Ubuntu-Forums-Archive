---
title: "[SOLVED] non-existing wireless driver menu?"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by sennep on 2007-10-23
I apologize if this has been answered before, I tried to search but I couldn't find any info about it..

The thing is, I have a netgear wg111v2 and I'm trying to make it work with wpa-psk in gutsy, network manager can see the signal strength and the name of my network, which I was very pleased with. However, it doesn't seem to be able to actually connect, it tries to connect, but fails.
So I searched the forums and found this quick how-to, there is however a problem with step 2 of the howto, I do not have a menu entry called "Windows Wireless Drivers" under system --> administration.
Does anyone else have this menu? Or does anyone else know anything about this? Any help is much appreciated!

The how-to I found:

This is by far the best and most simple way to do it. NOT A SINGLE LINE OF CODE TO ENTER IN TERMINAL, not even ROOT login:
You need:
Ubuntu 7.10. (Maybe also earlier ones, I haven´t tested.)
WPA encryption (WEP doesn´t seem to work) with a passphrase no longer than 16 letters/numbers.
The .inf-file for Windows XP that is on your Netgear CD. (/Driver/WINXP/net111v2.inf)

1) Have the CD in the CD compartment, and your Netgear WG111v2 plugged in.
2) From the System menu, click Administration, then the last entry: Windows Wireless Drivers.
You will be asked for your password. This is your normal password used for log-in, not any special ROOT password.
3) When the window opens, click "Install new driver". 
4) Browse to the .inf-file location on your CD. click it and choose "open" and when you get back to the previous window, "install". 

Now the installation itself is complete. And you haven´t even opened Terminal. But don´t close any window yet.

Now you must (of course) configure your network to match your wireless router. This is done by clicking "Configure network". (Surprised?)
"Hardware present" should read "Yes" and the box beside Wireless connection should be marked. If not, do so.
Double-click on "Wireless connection" (or click Properties) and...
Fill in your SSID (network name), 
choose WPA Personal, 
fill in your passphrase. 
Finally choose Automatic configuration (DHCP). Click OK. That´s all. 
No need to be a geek anymore, no code hacking in Terminal. No sudo, no ROOT login...
Best regards
/Orvar

---

### Post by spd106 on 2007-10-23
Yep, you need to install the [ndisgtk]("apt:ndisgtk") package.

It's available in the universe repository, accessible through the Synaptic Package Manager.

---

### Post by sennep on 2007-10-23
Ah, I see, thank u!

Btw, does network manager have to be disabled if I use this method? or are they able to coexist?

---

### Post by spd106 on 2007-10-23
These packages won't conflict, because they cover different things. 

Ndisgtk is merely a gui front end to the ndiswrapper driver installer. Network Manager interacts with ndiswrapper to control the wifi card. 

So you can use Network Manager just fine.

---

### Post by sennep on 2007-10-23
I see, Network Manager is more clever than I thought it would be:)

Since I have no internet connection, I downloaded Ndisgtk from packages.ubuntu.com. So I guess the thread is solved really, although my internet doesn't work yet, I can't actually connect, I checked syslog and it seems I recieve no DHCP offers.. so it's back to searching the forums, but thanks for your help man! I appreciate it!:)

---

