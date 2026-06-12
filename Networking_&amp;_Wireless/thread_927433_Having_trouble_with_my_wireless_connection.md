---
title: "Having trouble with my wireless connection"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by lcruz007 on 2008-09-23
Hello!
I'm new to Ubuntu, and I am currently having problems trying to find my network. I am not really sure about how discovering a wireless connection, but I clicked the "edit wireless networks..." option, but there doesn't seem to be my network there.

I have searched every option available, but I can't find any solution.

How can I connect to my wireless router???



Thank you in advance.

---

### Post by kidnot0ri0us on 2008-09-23
If you have the drivers for your wireless card installed correctly, simply left-click on network manager in the panel to view available wireless networks

If your card is connected and you can't see any networks, you haven't installed the right drivers

---

### Post by kidnot0ri0us on 2008-09-23
On a similar note, I am having trouble connecting to my wireless AP using Network Manager and using a 64 bit (10 digit) WEP key

when I try to enter the key using the WEP 64/128 HEX option, It fails

but I can connect manually from the terminal using the guide from this forum

anyone know whats up with that?

---

### Post by lcruz007 on 2008-09-23
Ok... So, where can I download the drivers to install them??

---

### Post by kidnot0ri0us on 2008-09-23
a simple google search helped me find the drivers i needed

you'll have to search by the type of wifi card that you have, if you don't know what kind you have you may have to run some commands from the terminal to find out

if you have Ndiswrapper installed, you can use the windows drivers

look around here on the forums, theres a ton of info that might help you

---

### Post by superprash2003 on 2008-09-23
please post the output of lshw -C network and iwconfig

---

