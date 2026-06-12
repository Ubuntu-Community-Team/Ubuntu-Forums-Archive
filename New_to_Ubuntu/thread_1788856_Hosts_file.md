---
title: "Hosts file"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by Old-un on 2011-06-23
Have been trying to configure the hosts file in Lubuntu 11.04 but when i opened a terminal and typed:
sudo /etc/hosts/ the output was no such file? Could someone tell me where i might find the hosts file please. Thanks

---

### Post by ExileAmongYou on 2011-06-23
The command to edit the hosts file should be
```
gksudo leafpad /etc/hosts
```
The last slash in the command you typed isn't needed. Also, the hosts file is just a plaintext file, so you need to open and edit it with leafpad (I think this is the default text editor in Lubuntu, otherwise replace "leafpad" with "gedit"). Since leafpad is a graphical application, you run it with gksudo rather than the usual sudo.

---

### Post by Old-un on 2011-06-23
Big thanks ExileAmongYou

---

