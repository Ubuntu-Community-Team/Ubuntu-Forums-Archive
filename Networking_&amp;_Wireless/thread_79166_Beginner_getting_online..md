---
title: "Beginner getting online."
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by mokeyjoe on 2005-10-19
Hi there. I've just signed up for ADSL broadband at my new home with Zen Internet. How do I go about settinng it up on Ubuntu (Hoary) when its activated. I have a  Voyager 205 modem on the way which lets me connect either by ethernet or USB and I have received an email containing 'technical details' from Zen, telling me amongst other things, my IP address and that the connection type is PPPoA.

What do I need to do to get online? I'm new to Linux and don't know where to start. Will it just plug and play or will I have some configuration to do?

---

### Post by imad_b on 2005-10-19
Hi there,
Regardless of whether it's Linux or Windows, usually you'll have to set up some modem settings first.  Like your user/password.

Plug everthing in, as per the instructions of your ISP.
You've probably got a Starter pack of some sort.
Follow the instructions, plugging in all the cables etc.

Once all plugged in, reboot, and then navigate to your modems control panel.
This is usually done via the Browser.
In Linux you could use the Mozilla Browser for example.
Your instructions should give you the address to go to.
For example: 192.168.1.1 (or something similar).  Put that in the address bar.
Then follow the instructions provided by your ISP to set up your modem settings.

Usually after that is just a matter of restarting, and browsing.

---

### Post by mips on 2005-10-20
Use the Ethernet port !!! USB is way more complicated.

Configure the ADSL router with VPI/VCI, Encapsulation, PPPoA, DHCP Server, DNS + Username & Password. As per the guide they supplied you.

Next configure your PC's Ethernet Card TCP/IP settings for DHCP.

---

