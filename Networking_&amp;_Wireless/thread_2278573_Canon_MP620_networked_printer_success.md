---
title: "Canon MP620 networked printer success?"
date: 2015-05-17
forum: Networking &amp; Wireless
---

### Post by greg81 on 2015-05-17
Has anyone successfully got this going on lubuntu 14.04 LTS? I am new to this and though I can get the printer connected via USB, I have failed to install via the wireless network. I have installed samba and spent many hours trying lots of things. I just need to know whether it is worth my while persisting, or should I give up?

---

### Post by Vladlenin5000 on 2015-05-17
Hi and welcome.

Assuming it is already working as it should via USB that means the required drivers (and other software) are already in place. Setting up the a network printer is the same as setting up a local one (USB, etc.). You can use the "add printer" dialogue in System Settings > Printers (one will be there already, the local one, if you haven't deleted that - you don't need to -) but choosing network printer instead of local and providing the required data, mainly the printer's IP address. 

All of this, of course, can only be done after properly setting up the printer in the network. Have you done that already? If so, how?

---

### Post by Vladlenin5000 on 2015-05-17
Addendum:

According to this [Network Setup Troubleshooting]("http://gdlp01.c-wss.com/gds/7/0300001557/01/MP980_MP620_NST_EN_V1.pdf") document from Canon, your printer
> • [COLOR=#ff0000]This machine does not support WPA/WPA2-Enterprise.[/COLOR] When you select an access point
set to use WPA/WPA2-Enterprise, it is grayed out and cannot be set up.

Here's the problem: WPA2 is the current standard; nothing else is recommend. **DO NOT use WEP just to accommodate an old printer.** Either buy a new one or use it cabled only. The connection you need to setup from the clients (devices that will be printing to that printer) is exactly the same for Ethernet or WiFi.

---

### Post by greg81 on 2015-05-18
Thanks Vladlenin.
The printer is successfully installed "on the network" (whatever that means). I can print to it wirelessly from other Windows-based machines. It has an IP address and it shows up on my router list of devices connected to the wireless networks (though it has no name, only an IP address). Ping works fine. The trouble is that when I tried to set up a network printer in Lubuntu, Lubuntu couldn't find it, even when I gave it the correct IP address. The furthest I have got to is to install samba, and set up the printer via samba. In this case, it superficially looks like it recognises the printer, and I get the new icon in "my printers", but when I print a test page nothing happens. By looking at the error report it appears that the samba- installed printer routine was not successful (in spite of the appearance of the icon etc). 
This may be relevant: when I was setting up the wireless printer I used canon's network utility software. This involved putting a usb (with some executable software) into each machine that was to be networked to it. I have no idea what I was doing at the time, but it worked. Perhaps what I should do is to uninstall the printer from all machines and start again  from scratch? I will look into your idea of not using WEP. Finally, one think I find confusing is that when I look at printer properties via the windows machines, I find that though they all work via a common Wifi newtwork (named "madshed") they seem to have an extra network that connects them to the printer (named "madshed2"). This makes me think that the printer is connected to the laptops in a star-shaped pattern with it at the centre. (a workgroup?). 
I dunno....I am just groping around in the dark here.

Greg

---

