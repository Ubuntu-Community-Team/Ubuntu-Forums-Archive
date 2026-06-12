---
title: "Ubuntu 19.10: Lenovo Ideapad Flex 14 Intel 9560 - Adapter not found"
date: 2020-04-15
forum: Networking &amp; Wireless
---

### Post by ngupta9 on 2020-04-15
Hi,
I just dual-boot my new Lenovo laptop. 
While installing Ubuntu-19.10 the Wi-Fi was working. However, when I am using Ubuntu, it says the Wi-Fi adapter not found.
Somehow, when I boot Ubuntu from Advanced options to an old kernel, the Wifi works.

Can someone please suggest something?
My earphones are not working too. 

I saw some steps online. But, they require Ethernet jack or adapter. I don't have both.

---

### Post by chili555 on 2020-04-15
Please run:

```
sudo modprobe iwlwifi && dmesg | grep iwl | tail -n3
```

Please post the result.

---

### Post by ngupta9 on 2020-04-15
@chili555
This is the terminal output

[ 3.105393] iwlwifi 0000:00:14.3: Failed to start RT ucode: -110
[ 3.105395] iwlwifi 0000:00:14.3: Firmware not running - cannot dump error
[ 3.117203] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110

---

### Post by chili555 on 2020-04-15
Please check here: [https://askubuntu.com/questions/1218141/dell-vostro-5490-no-wifi-in-ubuntu-18-04/1218262#1218262](https://askubuntu.com/questions/1218141/dell-vostro-5490-no-wifi-in-ubuntu-18-04/1218262#1218262)

---

### Post by ngupta9 on 2020-04-15
Renaming the file solved the problem. 

Thank you so much for your help.

---

### Post by chili555 on 2020-04-15
Awesome! Glad it’s working. Please use thread tools at the top to mark Solved.

---

