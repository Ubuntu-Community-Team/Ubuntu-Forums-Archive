---
title: "Feisty WPA connection woes"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by betelnut fatboy on 2007-05-11
I've just installed Feisty 7.04 on an old Vaio,  the laptop detects the wireless networks in the area, including my home WPA encrypted network but the network manager only has WEP options on it (network manager applet 0.6.4) so I can't access it via the ubuntu loaded laptop
I believe I'm making a simple error but can't suss out what, since the interface seems different from the one shown on the Ubuntu website and my understanding was that feisty had WPA support built in,

does anyone have any insights into just where I'm messing up here, if you need more info ask

thanks in advance

---

### Post by Emeriz on 2007-05-11
I was having a lot of issues with the network-manager as well and I switched to  wicd ( [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")  )and I am connected through WPA right now.  Just remember to uninstall network-manager first.

Hope that helps.

Em

---

### Post by RichPicker on 2007-05-11
Get a little program from the Synaptic Package Manger called "wifi-radar"
It will accept wpa passwords.

---

### Post by betelnut fatboy on 2007-05-19
guys, thanks HUGELY for your help and advice, the wicd solution worked best for me, 

for the other neonatalbies out there like myself, 

so you don't have to reinvent the wheel
i found removing network manager with the add/remove programs tool insufficient and had to use synaptic packet manager to do it properly, before installing wicd,
and now I too am surfing wirelessly  in my garden on my WPA encrypted wifi , 

cheers

---

