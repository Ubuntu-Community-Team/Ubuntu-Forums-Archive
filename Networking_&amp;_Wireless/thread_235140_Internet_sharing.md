---
title: "Internet sharing"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by ojinka on 2006-08-12
I have got ubuntu 6.06 :D on my desktop and i want browse web on my notebook (Win XP)which is conected to my desktop via LAN cable. How can i configure that? 
eth0 - conected to internet
eth1 - conected to my notebook

Can you help me, please? :confused: 

Thanks :wink:

---

### Post by Matchless on 2006-08-12
Hi,
   I am assuming that your XP laptop and the Ubuntu Desktop is properly setup and can talk to one another via the network and that the Desktop can browse the internet? If not then you first have to get this working.
Now install Firestarter and when you are connected to the Internet, run it and use the wizard to set up internet sharing and you should be OK.

---

### Post by ojinka on 2006-08-12
when i start firestarter i can not conect to internet from anywhere. When i turn it off, my internet si all right, but sharing is not working. I configure firestarter apsolutely right, so i do know where is problem :-k

---

### Post by Matchless on 2006-08-13
Hi,
   I am not very experienced in this area, but it is necessary that you have your ISP DNS addresses specified in the eth1 of the PC connected to the internet (gateway PC) and in the eth0 of the other PC's. You also need to have the gateway PC address in the other PC to point you back to your gateway PC.
Someone with detailled knowledge will have help you from here if this does not help you.

---

