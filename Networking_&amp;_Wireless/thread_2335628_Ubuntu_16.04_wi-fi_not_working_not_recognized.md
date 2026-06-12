---
title: "Ubuntu 16.04 wi-fi not working/ not recognized?"
date: 2016-08-30
forum: Networking &amp; Wireless
---

### Post by patkins1992 on 2016-08-30
Hello! I don't know where to go and I hope you all can help me...

I have an HP ENVY x360 m6 Convertible laptop (not sure how much info you guys need...), and have dual booted Windows 10 and Ubuntu 16.04 onto it. The installation was smooth, but I cannot for the life of me, figure out why Ubuntu is not connecting to my WIFI... I know there are several posts all over the place about this, but I don't want to blindly follow and accidentally nuke my laptop. 

So, if anyone can help me get my wifi working so I don't need to always be connected to an ethernet cord, that would be awesome! I will provide any terminal readouts you need or request. I really want my laptop to work...

Thanks in advance and sorry for being stupid...

---

### Post by jeremy31 on 2016-08-30
See the wireless script link in my signature and post your results

One thing to check with an HP laptop is ```
lsmod | grep acer
```
If this returns ```
acer-wmi
```
Then blacklist that module with ```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by patkins1992 on 2016-08-30
I followed your instructions and it stared detecting wifi.

It then hit me with 

     "Failed to add/activate connection
      (1) insufficient privileges"

i went to terminal and typed "nm-applet" and that seemed to fix it? I don't know...

Either way, problem mostly solved, thank you very much!

---

### Post by bad94 on 2017-02-01
This worked for me too! You should change this to solved/answered for future users!! Thanks to all involved here.

---

