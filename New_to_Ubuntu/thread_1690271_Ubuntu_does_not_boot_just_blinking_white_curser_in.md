---
title: "Ubuntu does not boot just blinking white curser in black sreen"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by chitragurung on 2011-02-18
Hello,
 
I was trying to upgrade my system from Ubuntu 8.04 to 10.04. During the installation after completion of at least 50% a error message come out. I ignored it and I quite the installation. It took long time to reboot and I switched off to reboot normally. But it does not reboot normally and got blank black screen with white curser. I have no cd drive in this note book but I have UBUNTU 10.04 iso files in external hard drive.
 
How can i solve this. If I need formating, how can I do ?

---

### Post by PunkLV on 2011-02-18
When you get to blank screen press **Ctrl+Alt+F1** then run:
```
sudo apt-get dist-upgrade
```
Unless something more serious had happened, this should solve the problem.

---

### Post by chitragurung on 2011-02-18
No effect  of action.  Nothing happen when I  press those keys

---

### Post by gandaran on 2011-02-18
a clean install is always better than an upgrade.

---

### Post by kamalmv on 2011-02-18
its all the problem with the partial update....
if the update was not complete.. then the only ways is to reformat..
i too have experienced the same...

---

### Post by oldfred on 2011-02-18
If you hold the shift key down from BIOS boot until menu appears, do you get menu? Then you can try booting in recovery mode.

What video card do you have. That could be a problem also, but if install did not complete then you have to do that.

---

