---
title: "Need help, im stuck!"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by Jenkins020 on 2008-10-11
Hi all,

I recently installed ubuntu 8.04 64bit. Everything works fine, except the wireless. Its a SMCWPCIT-G EU. I tried using ndiswrapper,  loaded the inf file with ndisgtk. Ndisgtk said that the hardware was present but nothing really happend. still no wireless, even after a reboot. I tought that this card was supported out of the box? Or is it just because im running the 64bit version? 

Thanks in advance ;)

Jenkins

---

### Post by damis648 on 2008-10-11
Edit /etc/modules and add ndiswrapper to the list of modules and then type in terminal
```
sudo modprobe ndiswrapper
```
and it should work.

---

### Post by Jenkins020 on 2008-10-12
It doesnt work when i do that, i tried installing the most recent madwifi drivers but that didn't do anything either. I even tried installing the 32 bit version, but that didn't help. The weird thing is that when i type iwconfig the wifi istnt even listed. when i type sudo modprobe ndiswrapper nothing happens. I dont know what to do next.

---

