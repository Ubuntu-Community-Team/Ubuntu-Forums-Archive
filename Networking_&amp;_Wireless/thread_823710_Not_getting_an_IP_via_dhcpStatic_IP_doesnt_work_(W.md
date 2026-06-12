---
title: "Not getting an IP via dhcp/Static IP doesnt work (Working in Windows)"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by Woodman on 2008-06-09
Im having a bit of a problem connecting with Ubuntu 8.04 which I just installed. Internet works under Windows XP on the same computer. I have a dhcp connection but with a static ip adress, but Im not getting an ip-adress over dhcp in Ubuntu (I am in Windows) and I've tried dhclient eth0. I've also tried releasing dhcp in Windows before rebooting to Ubuntu just to make sure. Static IP doesnt work either, cant ping my gateway, which also works in Windows.

Interesting part is that a month ago or so I had a server with Debian set up as my router, worked flawlessly until blam, one day I couldnt get it working, seems like the same issues as Im having now. I didnt really need the server at that point so I just let the problem slip.

When this happened to the Debian-box I called tech-support which looked into it but found nothing on their side, they could see my mac-adress etc from their side.

I definatly do know my way around internet connections and Im not terrible at Linux either (but please assume I am). Do you guys have any ideas?

---

### Post by FreakTech on 2008-06-09
> **Woodman said:**
> Im having a bit of a problem connecting with Ubuntu 8.04 which I just installed. Internet works under Windows XP on the same computer. I have a dhcp connection but with a static ip adress, but Im not getting an ip-adress over dhcp in Ubuntu (I am in Windows) and I've tried dhclient eth0. I've also tried releasing dhcp in Windows before rebooting to Ubuntu just to make sure. Static IP doesnt work either, cant ping my gateway, which also works in Windows.

Interesting part is that a month ago or so I had a server with Debian set up as my router, worked flawlessly until blam, one day I couldnt get it working, seems like the same issues as Im having now. I didnt really need the server at that point so I just let the problem slip.

When this happened to the Debian-box I called tech-support which looked into it but found nothing on their side, they could see my mac-adress etc from their side.

I definatly do know my way around internet connections and Im not terrible at Linux either (but please assume I am). Do you guys have any ideas?

If I am reading this correctly, you have a DHCP server, but are using a static IP on your workstation.  Your XP installation works fine, but the Ubuntu installation will not pull an IP from DHCP nor work with the static..  I am correct?

Could you please do an ifconfig and repost?

---

### Post by Woodman on 2008-06-09
Yeah, thats correct. I was starting to think it was the duplex mode messing with me, I suddenly remembered I had to set that manually in Windows to get it to work. Neither ethtool nor mii-tool worked for me though, operation was not supported by the card.

Funny thing is, now its working and I'm posting from inside Ubuntu, I haven't changed a setting but hey, if its working its working. ;) Thanks for trying to help!

---

