---
title: "wireless doesn't work!!"
date: 2013-09-20
forum: Networking &amp; Wireless
---

### Post by Manson_Chuh on 2013-09-20
Wireless doesn't work after the latest update!

Kernel:ubuntu12.04 LTS
OS Type:64-bit

root@manson-Lenovo-KL6B-KL6C-Z475:~# ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill


root@manson-Lenovo-KL6B-KL6C-Z475:~# rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by Kirboosy on 2013-09-20
Welcome to the forums!

```
sudo rfkill unblock all
```

[rfkill Documentation]("http://wireless.kernel.org/en/users/Documentation/rfkill")

Hope that helps!
~Caboose

---

### Post by benpietras on 2013-09-20
sudo rfkill unblock all 

If that doesn't work, check your wifi enable button on your laptop, fn + f2 or something

---

### Post by Kirboosy on 2013-09-20
Upon further research  it looks like the wireless is physically turned off. A softblock means its shut off by software. A hard block means a physical switch or the actual card is shutoff at the hardware level.

So my previous post is only good if **soft blocked: yes** is the case. However yours is a **hard block**. (It won't hurt to run the rfkill command just know it most likely won't do anything)

~Caboose

---

### Post by Manson_Chuh on 2013-09-21
I tried,but help with nothing,it seems that the problem is not hardware failure

---

### Post by varunendra on 2013-09-21
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It'll give us all necessary details to possibly pin-point the problem.

---

