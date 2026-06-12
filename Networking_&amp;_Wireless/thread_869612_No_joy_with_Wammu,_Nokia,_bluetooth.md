---
title: "No joy with Wammu, Nokia, bluetooth"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by rogerdean on 2008-07-25
Hello folks

I'm struggling to get Wammu to connect to my Nokia 6021 via bluetooth. It's as if the connection gets halfway and then drops

I have python-bluez installed as requested, and the phone paired (see screenshot "phone paired". When going through th Wammu wizard I get 4 or more connection requests on the phone, the first three of which are then reported failed. Finally the phone shows requests to exchange data.

I'm then offered 4 detected phones (see screenshot "phones found"), but whichever one I select I then get the message -

Error opening device
Device 00:17:B0:54:32:8C does not exist!

No idea where to go from here. Any suggestions?
Many thanks all
Roger

---

### Post by aon72 on 2008-11-19
Hi Roger,

I've the same problem today. First of all, I've connect the phone with the "Bluetooth-Manager for GNOME" and during first connection give PIN 5432 in phone (see []("http://www.gammu.org/wiki/index.php?title=Gammu:Connecting_to_phone") bluetooth #9). Then I've close the connection to the phone and run the phone wizzard. I've got the same message "Device xxxxxx does not exist!". Then I say **yes to the wizzard to save the connection** and wammu now can connect to the phone (nokia 6230) from the menu.

Regards Thomas

---

### Post by Daveski on 2008-12-01
> **aon72 said:**
> ...Then I say **yes to the wizzard to save the connection** and wammu now can connect to the phone (nokia 6230) from the menu.


Yep same here except I can only retrieve info and messages, no calendar, contacts etc. I get 'Your phone doesn't support this function'.

Can anyone help?

EDIT: Ah, changing the settings and choosing *Connection* as **bluephonet** and *Model* as **auto** seems to have fixed this for me.

---

