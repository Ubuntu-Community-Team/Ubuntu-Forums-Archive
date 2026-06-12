---
title: "Nouveau"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by ben889 on 2011-02-01
With a lot of help I have enough info to install nvidia driver but how do i gain privledge to edit the modprobe folder. also once i have that and have the nvidia driver installed do i need to open a terminal and stop dgm?


thanks Ben

---

### Post by JC Cheloven on 2011-02-01
Hi, surely there is a story behind your question. But to answer you:
If you want to edit any file at the /etc/modprobe.d folder, you may either:
- In a terminal ```
sudo nano /etc/modprobe.d/blacklistxxx.conf
``` where blacklistxxx.conf is to be replaced by the particular file you want to edit.
- Or, from a terminal ```
gksudo gedit /etc/modprobe.d/blacklistxxx.conf
```

As for your second question, if it's about I'm thinking, a restart of your system should do it.

---

### Post by Bölvaður on 2011-02-01
my brain isnt working and after reading over your question again I see I failed....

oh well..going to let this stay here for some people that might need it.


> **ben889 said:**
> With a lot of help I have enough info to install nvidia driver but how do i gain privledge to edit the modprobe folder. also once i have that and have the nvidia driver installed do i need to open a terminal and stop dgm?


thanks Ben

Are you wanting the nouveau driver or the nividia driver?

you install the first mentioned through jockey-gtk (ubuntu's default hardware-drivers program install program).

The nividia drivers you install by going to the nvidia website, put the driver onto the desktop or download folder. Right click on the driver and select properties, in there find permissions and tag so you have rights to execute this file. Press alt+ctrl+f6 (you go back by pressing alt+ctrl+f7), insert your username and password. type
```
sudo gdm stop
```press alt+ctrl+f7 to check if it's down, and then go back to alt+ctrl+f6 and cd to the downloaded driver and
```
sudo ./NIVIDIA...... blabla
```note that I have . /  dot slash, with no space between and then the name of the file to execute, which is the driver.
Then go through the menu, mostly just pressing yes, even if the default might be no.

---

### Post by ben889 on 2011-02-01
thanks for the reply


ben

---

