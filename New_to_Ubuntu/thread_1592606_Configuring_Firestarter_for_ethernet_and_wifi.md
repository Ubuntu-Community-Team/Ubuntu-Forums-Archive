---
title: "Configuring Firestarter for ethernet and wifi"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by CommuneOfLoon on 2010-10-10
I downloaded Firestarter earlier today and configured it on an ethernet connection.

Right now I'm on a wifi connection and wanted to confirm it is working and it's not. I went to Firewall->Run Wizard and tried to configure it for wifi as well, but it only gives me the option of ethernet (eth0, eth1, the same options as earlier).

So how do I dual configure?

Thanks.

---

### Post by andrewthomas on 2010-10-10
You do know that it is a dead project that is unsupported?

---

### Post by CommuneOfLoon on 2010-10-10
No, I didn't.

Is there another way to enable the firewall?

---

### Post by andrewthomas on 2010-10-10
ufw is enabled by default.  
 
If you want a graphical interface.  
 
```
 
sudo apt-get install gufw

```

---

### Post by CommuneOfLoon on 2010-10-11
Okay, thanks.

---

### Post by Calash on 2010-10-11
If you search in the software center Firestarter comes up high on the list and says nothing about the life of the project.

Is there a way to get dead projects removed from the Software Center?

---

