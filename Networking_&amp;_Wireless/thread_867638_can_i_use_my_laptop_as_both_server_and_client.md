---
title: "can i use my laptop as both server and client???"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by sky_knight02 on 2008-07-23
can any one tell me how to connect my laptop as server and client to itself using samba or any other packages????

THANK YOU...

---

### Post by superprash2003 on 2008-07-23
please be more specific on what you want to achieve..if im not mistaken you want to setup samba in your laptop.. and connect to it from your laptop itself.. in that case.. setup samba.. and then go to the terminal and type nautilus smb://127.0.0.1 to connect

---

### Post by sky_knight02 on 2008-07-24
ya you are correct but it is opening in GUI mode... i want to do that in terminal mode... can u tell me how to do that pls????

---

### Post by dmizer on 2008-07-24
to set up your laptop as a samba server, see the first link in my sig.  to set up your laptop as a samba client, see the second link in my sig.

---

### Post by sky_knight02 on 2008-07-24
They are wonderful links.... but i need to do that using loopback ip... i need to create my laptop as server and as client and i need to share them using loopback ip.... can any one tell me how to???:(

---

### Post by dmizer on 2008-07-24
so ... use your loopback ip address, or "localhost"

just out of curiosity, in what situation would you want to do this?

---

### Post by sky_knight02 on 2008-07-25
I just want to experiment that way... pls dont just tell me to "use loopback ip" i want to know how to do that...

---

### Post by superprash2003 on 2008-07-25
your loopback ip would be 127.0.0.1

---

### Post by sky_knight02 on 2008-07-25
guys i know my loopback ip is 127.0.0.1 and i tried to use smbclient -L 127.0.0.1 to see the shared folders but its not working so tell me how to connect now and is there any other command or way to connect???

---

