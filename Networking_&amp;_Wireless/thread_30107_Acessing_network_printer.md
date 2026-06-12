---
title: "Acessing network printer"
date: 2005-04-27
forum: Networking &amp; Wireless
---

### Post by Sabator on 2005-04-27
Phew...after spending too long digging out my old HP and hooking it up, the damn thing doesn't work. Jammed print heads or something.

My Mom has an old printer on her PC, running XP home. How can I access that?

---

### Post by Fab on 2005-04-27
[QUOTE=Sabator]Phew...after spending too long digging out my old HP and hooking it up, the damn thing doesn't work. Jammed print heads or something.

My Mom has an old printer on her PC, running XP home. How can I access that?[/QUOTE]
 she needs to enable printer sharing on her computer
then, (if you havent already) install the samba packages on your (linux) box, then go to the printer preferences and choose networked printer and smb, put in her computer's name and the name of the printer (in my case thats "XXXXX" and "PRINTER") and try to print the test page (beware, its full of colorful joyness :P)

---

### Post by Gallows on 2005-04-27
Have a look at....

[http://ubuntuforums.org/showthread.php?t=25557&highlight=networking+howto+data](http://ubuntuforums.org/showthread.php?t=25557&highlight=networking+howto+data)

Get that working
If you don't have DHCP on the network or a static IP on the XP box - Use 169.254.0.0/255.255.0.0 as XP *should* automagicaly get an address from that range...

Share the printer on the XP box - Right Click - Sharing and Security
If you have XP SP2 - Open up the firewall for the LAN connection
Install the Samba client in the Ubuntu box (If it's not already)
Add your new shiny network printer

If that works first time then you might want buy yourself a pint...

---

