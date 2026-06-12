---
title: "Cant install updates"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by christopherbrown4@msn.com on 2009-02-10
Dell laptop wouldnt startup past the first Ubuntu screen. Reinstalled ubuntu 804 from Ubuntu supplied disk.263 updates showing to install. Wont install, showing " An error ocurred  E: /var/cache/apt/archives/login_1%3a4.0.18.2-1ubuntu2.2_i386.deb: failed in buffer_read(fd) "  It also shows alot of text at start up,which it never did before reinstall?

---

### Post by supersonicdarky on 2009-02-13
try
```
sudo apt-get clean
```
in the terminal, and then try updating again

---

