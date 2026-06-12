---
title: "Remote desktop authentication error"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by lintoon on 2008-08-17
Hi, 

I am trying to get vnc working between my Ubuntu server and my ubuntu laptop.  

On the Ubuntu server I have configured Remote Desktop and set a password but when I go to the terminal and test it with "vncviewer localhost:0" I get an authentication failure error message.

The server is running 7.10 and my laptop is running 8.04.   

Does anyone have any ideas on how to fix this problem or can point me towards a good troubleshooting guide.

Thank you.

PS.
I know I could use FreeNX but I need to get vnc working because I have a  vncviewer on my ipod touch.

---

### Post by lintoon on 2008-08-17
I've sorted it.  

I disabled and re-enabled remote desktop.  Simple as that.  Now I feel stupid for even asking about it.

---

### Post by lintoon on 2008-08-17
Also, I forgot to mention that I upgraded to 8.04 and it still didn't work until I disabled then re-enabled remote desktop (on the server).  This was even after a reboot at the end of the upgrade - strange.

I think I shoud restart the server to confirm it's ok.  I'll post the result.

---

### Post by lintoon on 2008-08-17
Still working after a reboot.

---

