---
title: "how to connect to windows network in the office"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by arek_chicago on 2008-09-24
i have ubuntu 8.04 installed on my laptop, in our office we are using windows server. i can install windows shared printers and print, server never asks me for password or username ?  but i cannot login to the file share. when i double click the share it doesnt ask me for the user name/password. it just shows empty folder

2)i tried "connect to server" but it doesnt help
server: i entered "marble" that is server name 
share: server-1 that is server inside marble
domain: marble 
and it never worked 
it asks me to enter user and password but it says "Can't display location "smb://marble/server-1/"

any solutions? 
i know i did it couple months ago but i forgot :-) i tried many tutorial but i cannot find solution

plz help, i'm trying to swich to linux completely, i run windows in VM but never use it anymore. At home i use apple hackintosh, at work my laptop but i need to connect to windows share. 
plz, help

---

### Post by AJB2K3 on 2008-09-24
Have you tryed installing samba yet?
You need the samba client for ubuntu to connect to windows smb shares.

---

### Post by superprash2003 on 2008-09-24
go to places->computer and under location type smb://x.x.x.x where x.x.x.x is the ip address of the windows machine you want to access files from

---

### Post by arek_chicago on 2008-09-24
i installed samba, i just don't know why it doesnt ask for login and it just opens window with blank folder

---

### Post by arek_chicago on 2008-09-24
how do i get ip address of my windows server?
ifconfig?

---

### Post by arek_chicago on 2008-09-24
i figured it out myself, there was nothing wrong with the way i tried to login to windows share. i tried all possible ways and apparently nautilus has a bug. i installed smb4k which is kde share browser and everything works, when i click the share it asks me to enter password and user name.
that's it. i thought 8.04 is supposed to be LTS release. can't they fix it.

---

### Post by arek_chicago on 2008-09-24
[http://www.itwire.com/content/view/19728/1162/](http://www.itwire.com/content/view/19728/1162/)

---

