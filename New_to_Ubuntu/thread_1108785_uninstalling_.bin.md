---
title: "uninstalling .bin"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by dimitriv on 2009-03-28
hi

I installed Google Earth 5 but it's got a bunch of problems. How can I uninstall remove it? It was installed using GoogleEarthLinux.bin

Installed on Intrepid 8.10.

Thanks

---

### Post by gandaran on 2009-03-28
you'll have to find an uninstall file in the GE install directory in /opt I think then cd the terminal to that directory and run **./uninstall**

---

### Post by dimitriv on 2009-03-30
thanks gandaran

cd /opt/google-earth
sudo su
./uninstall

did the trick

---

