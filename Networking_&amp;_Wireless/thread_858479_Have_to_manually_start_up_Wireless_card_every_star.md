---
title: "Have to manually start up Wireless card every start up"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by Soapy Toboggans on 2008-07-13
Whenever I restart Ubuntu I have to type:
```
sudo modprobe ndiswrapper
```
into the terminal. Is there anyway I could get this happen automatically on startup?

Thanks in advance for your replies.

---

### Post by kevdog on 2008-07-14
echo ndiswapper | sudo tee -a /etc/modules

Type that once and then it will be loaded at boot.

---

### Post by Soapy Toboggans on 2008-07-14
I put exactly what you said and it didn't work:(. Thank You for your response though. Any other ideas?

---

### Post by kerry_s on 2008-07-15
put> modprobe ndiswrapper & <in /etc/rc.local, it will run the command as root at start

---

### Post by kevdog on 2008-07-15
Can you list your /etc/modules file?

---

