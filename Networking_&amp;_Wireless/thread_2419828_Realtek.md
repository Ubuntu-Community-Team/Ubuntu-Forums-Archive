---
title: "Realtek?"
date: 2019-05-25
forum: Networking &amp; Wireless
---

### Post by texas-slim on 2019-05-25
So I just installed the latest version of ubuntu ( i think) on an old laptop, but it isnt recognizing my wireless card which is some variant of realtek. The only way I can connect to the internet is through a bluetooth connection with my phone, and I'm having  a hard time trying to install whatever driver i need to make my network card work... I'm new to ubuntu and havent used a computer in 10+ years so any help would be really appreciated
Thanks in advance 

Texas slim

---

### Post by wildmanne39 on 2019-05-25
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by texas-slim on 2019-05-26
Thanks for the help, here it is:

[http://paste.ubuntu.com/p/B4X8nYKyxP/](http://paste.ubuntu.com/p/B4X8nYKyxP/)

---

### Post by jeremy31 on 2019-05-26
In terminal do ```
sudo apt update && sudo apt install firmware-b43-installer
```
Reboot

---

### Post by texas-slim on 2019-05-26
Got it working! Thanks again

---

