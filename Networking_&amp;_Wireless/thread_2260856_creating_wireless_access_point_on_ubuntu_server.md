---
title: "creating wireless access point on ubuntu server"
date: 2015-01-14
forum: Networking &amp; Wireless
---

### Post by Tate_Porter on 2015-01-14
I have been trying to create a wireless acces point on ubuntu server. I have tried hostapd and also creating an access point through network interfaces. I travel for work so I am in hotels alot. I am using a dell netbook for the serrver. What I am trying to do is connect to the hotel wifi with the netbook with my the onboard wirless card. Then create an access point with a usb wirless card. Both wireless cards have the capability of being an access point. Right now I am using internet sharing on my macbook with an ethernet cord connected between the two. I am trying to eliminate having to connect with the ethernet cord so I dont have to take both the computers with me if I want to move about the room. Example, I like to sit on the bed and watch tv with my macbook. I would like to leave the netbook on the counter plugged into the wall. So to sum it all up what I am trying to do is this. Hotel wifi>Netbook>Macbook. Any help would be greatly appreciated.

Tate

---

### Post by Tadaen_Sylvermane on 2015-01-14
need to set up a dhcp server on the netbook. why though, why not just macbook straight to the hotel wifi?

---

### Post by Tate_Porter on 2015-01-14
Need ubuntu server for work. I had isc-dhcp-server. I almost had it done but after i set up the dhcp server and had the wifi setup i could not connect to it. So i di some research on google and everything i read said that host apd is really buggy and doesnt work correctly. It would prompt me for the wifi password and then after i put it in it failed to connect. I double checked that all my settings and conf files were correct and they were. I rebooted and still the same problem. I am really Getting tired of this darn ethernet cord but im kind of at a loss at this point.

---

### Post by Tate_Porter on 2015-01-14
Oh and before you ask i kno i could just connect both to the hotel wifi but since i have the second computer i use it as my backup device as well also typing on the macbook is much nicer than typing on the tiny netbook so i ssh into the netbook so i can take advantage of the nicer keyboard.

---

