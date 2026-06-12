---
title: "Samba cant detect other windows computers"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by mrcdan on 2006-10-26
I cant see any other windows computers in nautilus. When i click on "Windows Network" nothing is there. Interestingly, i can access shares with the smbclient command but i want it in nautilus. The windows computers have no trouble seeing me. Also, i can never use an actual windows host name, i always have to use an ip address.

---

### Post by rmjb on 2006-10-26
Hi mrcdan,

That's interesting that you have to use an ip address. Can you ping another computer's name from ubuntu? Open a terminal the enter *ping <other computer name>*

If not you may not be getting all the needed network settings, check your DNS Server setting in Network Settings (System -> Administration -> Network Settings -> DNS). Under DNS servers there should be at least one ip address, which may be your home router or other name server if you have one.

Hope this helps.

- rmjb

---

### Post by mrcdan on 2006-10-26
No, when i ping the name of a windows computer it doesnt work. In the DNS settings tab I have my default isp dns server(s) 64.x.x.x but nothing else. Should i put my router in (192.168.1.1)?

---

