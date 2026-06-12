---
title: "How to start up with Bluetooth and Wi-fi disabled?"
date: 2017-06-19
forum: Networking &amp; Wireless
---

### Post by Richardcavell on 2017-06-19
Hi, all.  I'm on 64-bit Ubuntu 16.04 LTS MATE.

My computer has Bluetooth and Wi-fi hardware. But I want it to start up with those items disabled. How do I do this?

Richard

---

### Post by Bucky Ball on 2017-06-19
You could try going to 'Sessions and Startup' and unticking Network and whatever bluetooth is enabled there. Restart and see if that works.

---

### Post by Hadaka on 2017-06-20
Hi, please post the output of...
```
lsmod
lspci -nnk | sed -n '/Wireless/,/driver/ p'
```
This will tell us what drivers are being used for Wireless and Bluetooth.
We can blacklist the drivers and they will not start on "Startup or reboot"
Thanks.

---

### Post by Richardcavell on 2017-07-04
Here's the log.

---

### Post by Hadaka on 2017-07-05
Hi the command...
```
[COLOR=#ff0000]*[/COLOR]lspci -nnk | sed -n '/Wireless/,/driver/ p'
is one command only..the **[COLOR=#ff0000]'[/COLOR]** | **[COLOR=#ff0000]'[/COLOR]** is called a pipe and is part of the comand
```

To disable your wireless and bluetooth please COPY and paste this long ONE line command.
```
echo -e "blacklist wl\nblacklist bluetooth" | sudo tee -a /etc/modprobe.d/blacklist-wl-bluetooth.conf
```

[COLOR=#ff0000]*****[/COLOR] To remove the modules from the blacklist file and restore them to default use
simply remove the blacklist file with..
```
sudo rm -rf /etc/modprobe.d/blacklist-wl-bluetooth.conf
```
boot and the modules will be restored.

Please do not post a file that has to be downloaded to view. "highlight,copy and past the file to your post'**[COLOR=#ff0000][/COLOR]**[COLOR=#ff0000][/COLOR]
Thanks.

---

