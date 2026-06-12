---
title: "WUSB54G &amp; Feisty Fawn"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by abalgach on 2007-09-08
Greetings All -

I am having some super weird problems with fiesty fawn and my usb54g usb wireless adapter from linksys.  so the system boots up and in the upper right hand corner of the screen i see a wireless indicator that says i am connected to my wireless network, with a strength of 89%  awesome i think.

however, upon further examination, I am not connected at all.  ifconfig shows:

rausb0  but doesnt have an inet/inet6 IP address

iwconfig should that i have an associated access point [which is NOT my router]  but no ESSID, and no IP address.


I should also note, that I have a broadcom 4318 internal wireless card, which I had working for about 15 minutes, and then upon a reboot, refused to obtain an IP address [in much the same circumstances now]

i have tried everything from removing one of the devices, turning off encryption on my router, altering the settings in /etc/network/interface  using iwconfig,  using the gui.  it seems no matter what i do I can't associate with an access point.

i feel like i have so many half configured wireless settings they are all conflicting with each other.  can someone give me some guidance on how to get the wusb54g working, connected, resolving an IP address, and perminantly stay like this so i can reboot the computer without having to do a bunch of steps each time?

thanks.

Adam.

---

### Post by noob12 on 2007-09-08
If  you are using NetworkManager, and it keeps associating with the wrong open AP, you can try to find and remove the folder for that network under: **~/.gconf/system/networking/wireless/networks/**.

Lots of people are recommending wicd as a better alternative to NetworkManager, but I have not used that.

---

