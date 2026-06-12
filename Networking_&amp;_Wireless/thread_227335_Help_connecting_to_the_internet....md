---
title: "Help connecting to the internet..."
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by Virtuosity0021 on 2006-08-01
Hi,
I currently have a WRT54G Wireless Linsys Router and a WMP54G Wireless Linksys PCI card.  While im on windows (im using the Ubuntu live CD) the internet works fine.  

FYI, these are the commands ive tried, and their results:
> 1. ifconfig -a [lists my interfaces, works fine]
2. ifconfig <interface> up [SIOCSIFFLAGS: Permission Denied]
3. iwlist <interface> scanning [eth1  no results]
4. iwconfig <interface> essid <ssid> [obviously doesnt work]


Can anyone help me with the problems from numbers 2+?  I can't understand why i get a permission denied.  

Any help is great, thanks.

---

### Post by stupidkid on 2006-08-01
You must add a sudo infront of it. Normal users can't enable networking.

sudo ifconfig <interface> up

---

### Post by Virtuosity0021 on 2006-08-01
I believe I have tried that, to no avail.  If i can remember right...it said that the command did not exist.

---

### Post by bensexson on 2006-08-01
try /usr/bin/sudo ifconfig <int> up.  If this works sudo is not in your path.

---

### Post by Virtuosity0021 on 2006-08-01
Tried it, still to no avail.

Does anyone have any more help?  If i don't get this firgure out...i probably will stop using ubuntu...:(

---

### Post by amp_man on 2006-08-02
can you post the output of lspci? also, sudo shouldn't be needed on the livecd (methinks) because the livecd uses root user permissions. Not positive on that one though, I haven't used the livecd

edit: got the info I needed, and my suspicions were correct: your card is based on the bcm43xx chipset. This card is odd as far as drivers go, you can either use ndiswrapper and blacklist the native driver, or extract the firmware from the windows driver to make the native one work. This is why your wireless hasn't been working, it's trying to use a driver that doesn't have the firmware it needs to operate. There's an entry in the wiki on the [here](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper), I personally would try to get the native driver working first, and rely on ndiswrapper as a last resort. feel free to post back if you're confused, I have the same chipset and have been through this mess myself.

---

### Post by Virtuosity0021 on 2006-08-02
Damn...im super confused.  I looked at that page, and its a lot of code to write down, since i cant be on windows and ubuntu at the same time.  I have a feeling it may be simpler than whats on that Wiki.  

Also, what Wireless (G) Adapters would be suitable for 0 trouble in a linux system?

AAAlso, is there a way to save all these settings...so i dont have to keep doing it everytime i use the liveCD?

---

