---
title: "Qualcomm Atheros QCA6174 Wifi won't turn on, 17.10"
date: 2018-01-26
forum: Networking &amp; Wireless
---

### Post by antttren on 2018-01-26
Hi, I am new here so please forgive me if I stray from the usual convention in my post here from time to time. 

I just setup my Lenovo Yoga 920 to dual-boot Windows 10 and Ubuntu 17.10, although I am currently unable to access windows but that's a story for another thread. My wifi seems to be nonexistent, although I'm able to connect through Ethernet. 
Here is a link to the usual diagnostics recommended by the sticky:

[https://pastebin.com/A6ehyzFP](https://pastebin.com/A6ehyzFP)

I try to turn it on with the "Turn on" option in the top right of the window but it just exits and is still turned off when I check again. 

I hope this provides some helpful information, any help would be greatly appreciated.

---

### Post by jeremy31 on 2018-01-26
A few things going on, in terminal
```
echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/ideapad-laptop.conf
```
```
sudo apt-get remove bcmwl-kernel-source
```
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Then reboot

---

### Post by antttren on 2018-01-26
That did it! You're a god, thank you Jeremy.

---

