---
title: "Did my NIC die?"
date: 2004-11-20
forum: Networking &amp; Wireless
---

### Post by Rotarychainsaw on 2004-11-20
n00b to linux in general here.
So I put warty on my back up computer and everything was fine. Internet worked and all that. So I upgraded to hoary and that worked for about a day, then it stopped connecting. If I go to that networking control panel I cant  activate eth0. 

After rebooting a couple times the bios went wonky. So I took out the battery for a little and booted back up and am now back where I started. No eth0 connection and I dunno what to do. 

I tried reinstalling warty off the same disk that worked before, but I stopped when it told me it couldnt find a network adapter. It should also be said that I found this NIC in the trash so.....

Any help would be greatly appreciated.

PS I just ran dhclient and the things that caught my eye were:

sit0:unknown hardware address
and a bunch of premission denieds
TIA

---

### Post by randy on 2004-11-21
When you start dhclient you'll need to start it with root permissions.  Thats why your getting permission denied errors.  I'm not sure about your other problems. I'd need to see more output.

---

### Post by MatthewMetzger on 2004-11-25
My NIC died, too. But I don't think it died. I think there is a configuration problem. I put a wireless card in my ubuntu linux system to see if I could get it working. I could not, but when I took the wireless card out my old fashioned ethernet NIC did not work. I have put two different cards that I know work into the system and they are not installed into the hardware configuration. They are not listed in the Device Manager (they were before).

My network settings shows no network devices even though I get a green connection light on the NIC when a network cable is plugged in.

This is a major problem for me. Any help would be greatly appreciated.
Thanks,

Matthew

---

### Post by MatthewMetzger on 2004-11-26
I corrected the problem, but didn't really fix it. I ended up reinstalling Ubuntu and using a different NIC. The wireless card caused by /etc/network/interfaces file to be so messed up that I didn't know where to start. But my original network card also wasn't detected in the Hardware Manager and wouldn't detect upon Ubuntu reinstallation. My internet was getting sluggish and it is possible that my card was on the way out anyway.

At my knowledge level, wireless has proven to be a pain and I will only attempt again by putting the card in the system and running a clean install of ubuntu. I don't need wireless now anyway, so I won't be trying any time soon.

Another note for others with similar problems: It looks like ubuntu does not recognize old (ancient) ISA NICs. My ISA 3com 3c509b card was not detected during ubuntu installation. Lucky for me I have a box of NICs and just kept trying. A Lynksis was what eventually worked.

---

