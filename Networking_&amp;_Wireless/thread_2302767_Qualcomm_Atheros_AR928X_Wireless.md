---
title: "Qualcomm Atheros AR928X Wireless"
date: 2015-11-13
forum: Networking &amp; Wireless
---

### Post by robbert-vanzuiden on 2015-11-13
Dear all,


I couln't find my old login anymore therefore i created a new,
pls i hope that you can help me with getting up my wireless... 
after the upgrade to 15 it stopped...
tried a lot to solve. but no luck yet.
i've included the output of the script created by a senior member :)

awaiting any feedback...

thanks already.

---

### Post by Hadaka on 2015-11-13
Hi, from a working wired connection please COPY and paste
one line at a time.
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo iw reg set NL
sudo sed -i 's/^REG.*=$/&NL/' /etc/default/crda
sudo apt-get autoremove && sudo apt-get autoclean
sudo modprobe ath9k
sudo reboot
```

remove wired connection test wireless

*

---

