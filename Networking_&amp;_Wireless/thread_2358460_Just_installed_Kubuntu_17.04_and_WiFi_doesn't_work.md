---
title: "Just installed Kubuntu 17.04 and WiFi doesn't work..."
date: 2017-04-13
forum: Networking &amp; Wireless
---

### Post by marer13 on 2017-04-13
Hi,

I just installed Kubuntu 17.04 on my HP Mini alongside Win10 and my WiFi doesn't work at all... doesn't even show in Taskbar, only Wired (which isn't connected anyway).

Why is WiFi not working? It seems like a simple and very important thing... So disappointed with Kubuntu... In the past it always worked...

---

### Post by wildmanne39 on 2017-04-13
*Thread moved to **Networking & Wireless**.*

---

### Post by marer13 on 2017-04-14
No, still not working...

---

### Post by wildmanne39 on 2017-04-14
Click on the wireless script in my signature and follow the directions for running it and posting the link created to pastebin here, which is where the file will be posted.

---

### Post by marer13 on 2017-04-15
Hi,

I followed the steps and in Terminal it says:

Pastebin successful:

[http://paste.ubuntu.com/24389802](http://paste.ubuntu.com/24389802)

---

### Post by chili555 on 2017-04-15
Is the correct driver installed?```
sudo dpkg -s bcmwl-kernel-source
```If it is installed, what is the exact response to the terminal command:```
sudo modprobe wl
```

---

### Post by marer13 on 2017-04-15
It says:

Package: bcmwl-kernel-source
Status: install ok installed

sudo modprobe wl is returning:
modprobe: ERROR: could not insert 'wl': Required key not available

---

### Post by chili555 on 2017-04-15
Please see: [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

The quick and easy way is to disable secure boot.

---

### Post by marer13 on 2017-04-15
I've changed that and now when I type    
sudo modprobe wl

It shows nothing

---

### Post by marer13 on 2017-04-15
It's working now! Thank you!   :D

---

### Post by chili555 on 2017-04-15
Awesome! Glad it's working.

I wish they were all that easy.

---

### Post by ariario on 2017-04-25
I have a similar problem.

I upgraded from kubuntu 16.04 to 16.10 today. Everything went smooth so I proceeded to upgrading to 17.04 right away. It installed without problems, but for some reason I can't use my wifi internet anymore. Neither of my wifi cards can get a connection. I also tried using my phone as a hotspot, but it didn't help.

When I choose a wifi network from the list, it tries to connect for like 15 seconds and then says Disconnected.

See the attached file for the wireless-info output.

Please, somebody help me, I'm writing this on my wife's windows laptop... :D

---

### Post by ariario on 2017-04-25
Oh glory I got it fixed!

Editing NetworkManager.conf helped. ([https://ubuntuforums.org/showthread.php?t=2354066&page=5](https://ubuntuforums.org/showthread.php?t=2354066&page=5))

---

