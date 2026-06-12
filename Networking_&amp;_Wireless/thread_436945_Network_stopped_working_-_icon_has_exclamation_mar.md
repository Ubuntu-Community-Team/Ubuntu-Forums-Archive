---
title: "Network stopped working - icon has exclamation mark and card greyed out?"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by RLamb on 2007-05-08
Hi all, 

For some reason my network has stopped working. When I start my PC Firestarter comes up saying eth0 is not ready, and the network icon in the system tray has an orange exclamation mark on it. I can't access the internet at all, and when I left click on the icon I can see my network card is there but it is greyed out? Usually it is black and the little circle to the left of it is selected.

I tried rebooting several times but that hasn't helped. Does anyone have any idea what could be wrong and ideally point me in the right direction for fixing it? 

Thanks in advance for any and all suggestions.

edit: Sorry to be more specific, it is an NTL cable modem connecting through my network card not a homel network. IP's are assigned by DCHP I believe.

---

### Post by rich.bradshaw on 2007-05-08
What is the output of dmesg, lspci and ifconfig?

---

### Post by RLamb on 2007-05-08
> **rich.bradshaw said:**
> What is the output of dmesg, lspci and ifconfig?

Hi thanks for the reply. Sorry I am a total linux noob I've heard of ipconfig before but not the others. Could you tell me the commands I need to use please?

Thanks again.

edit: sorry I see they work on their own. I'l reply with the data shortly.

---

### Post by RLamb on 2007-05-08
Hi,

 I've put a link to the file so it doesn't clog the thread if you'd rather I posted it though please just say.

[output <--]("http://www.varidev.co.uk/misc/output")

---

### Post by RLamb on 2007-05-08
*bump*

Really don't want to uninstall I love ubuntu but I really need the internet up :(

---

### Post by tonytux on 2007-05-09
> **RLamb said:**
> *bump*

Really don't want to uninstall I love ubuntu but I really need the internet up :(

just starting to get used to the whole ubuntu thing myself, and have ran into some personal problems with my connection form time to time.  and when my network seems to not be recognized or my connection is "lost' I always check my router and modem first, if you just unplug the modem for like 30 sec, while your computer is still up and running, and then plug it back in, your DHCP should ask for another IP address, usually ending up to be the same one, and your Icon will flash and start doing a whirlly thing and then you should pick up a connection.  Mine ends up being the cheap router I have, so it might not work, but it's worth a try.  Good luck, and keep at it.

---

### Post by RLamb on 2007-05-09
Hi,

Thanks for the reply. I've tried doing that several times and in different orders to (ie before computer turns on) and to no avail. I dual boot with XP not sure if that makes any difference.

Also I'm not using a router but rather a cable modem. Do you think that might be causing a problem?

---

### Post by RLamb on 2007-05-09
Still noone? :confused: :(

---

### Post by RLamb on 2007-05-10
Well somewhat of a fix was plugging the modem into the PC through USB instead of ethernet, and switching back to ethernet for windows. 

Still have to reboot the modem everytime I start into an OS but it works I guess.

---

