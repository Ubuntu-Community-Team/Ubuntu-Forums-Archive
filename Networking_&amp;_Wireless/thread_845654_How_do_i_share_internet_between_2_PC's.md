---
title: "How do i share internet between 2 PC's?"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by Hayesio on 2008-06-30
Hi everyone,

I was wondering if someone could point me in the right direction here. I have two computers; a desktop computer running Hardy which connects to the internet via its wifi card, i also have a Mythbuntu box in the loung room that has no wifi card and no internet.I have connected a network cable from the desktop pc to the Mythbuntu box. 

Now, this is my problem. I want to share the internet and files/folders on the desktop with the Mythbuntu box. i guess the desktop needs to be setup as a server somehow?. 

Could you tell me the best way to do this?

Thanks

---

### Post by flytripper on 2008-06-30
internet connected pc + ```
sudo apt-get install firestarter
```

run the wizard enable connection sharing in the firewall "firestarter" taking care to make sure you set eth0 +eth1 right and the ubuntu box ethernet card should be 192.168.0.1 or somatt like that.. forgive me for being windozy.

---

### Post by Hayesio on 2008-07-01
Ok, i have done that but i cant start the firewall.  It keeps returning this:
```
gksu /usr/sbin/firestarter
Internal network device eth1 is not ready. Aborting.
```

What should this device be set to in the Network Manager?

---

### Post by TenPlus1 on 2008-07-01
In Firestarter, make sure the "Enable DHCP for local network" is NOT ticked, then use Network Manager to set your wireless card's ip address (ip: 192.168.0.1, sub: 255.255.255.0) and the usual wireless stuff, and on the computer sharing the connection,make it (192.168.0.2, sub: 255,255,255,0, gateway: 192.168.0.1) and the same wireless stuff (essid, pass etc.) and get Firestarter on the main computer to allow access from 192.168.0.2 to your internet pc... (otherwise it wont work)...

---

### Post by Hayesio on 2008-07-01
Brilliant! Thanx for that. It was that DHCP was enabled.
Internet is now working on both computers!

---

