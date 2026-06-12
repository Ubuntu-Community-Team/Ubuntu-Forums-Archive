---
title: "[SOLVED] Wireless problem, restricted driver wont stay"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by Nehvrook on 2007-10-19
Hi. I recently got my dads laptop to conect to his wireless network in 7.04 using ndiswraper. Yesterday he updated to 7.10 and it found a driver out of the box with restricted drivers manager. We had to connect to the network with a wire to download this driver, but then the wireless worked perfectly.

However on restart, the restricted driver for the wireless card still shows as enabled, but it will not recognise the card or any network. The only way to get it working again is to disable the driver, plug in an ethernet cable, download the driver again and re enable it. But this is lost every restart.

Does anyone know why the driver isn't sticking, or how to fix this?


He is using a broadcom airforce wireless card built into his acer laptop.

---

### Post by ddrichardson on 2007-10-20
Yes, whatever kernel module the driver is needs to be appended to /etc/modules to be enabled on boot. This appears to be a Gutsy problem as I never experienced it under earlier versions.

---

### Post by Nehvrook on 2007-10-21
Sorry, dont exactly understand what you mean.

How would I find out what the kernal module is and how would I append it to /etc/modules

I've never had to deal with anything like this before so I'm a bit lost.

---

### Post by ddrichardson on 2007-10-21
Well, if using ndiswrapper then try```
sudo -s
cat ndiswrapper >> /etc/modules
exit
```

---

### Post by shad0w_walker on 2007-10-21
ddrichardson: I doubt he is using ndiswrapper as he said it was installed from Restricted drivers manager, also the card is a broadcom so i assume it is using the native bcm43xx driver.


If your are using a broadcom card i believe the module you need is

```
bcm43xx
```

What you need to do is to add that to the file that tells Ubuntu to load any extra modules required when it boots up. To do this follow these steps

1. Hit Alt + F2 to open the run dialog and run this command:

```
gksu gedit /etc/modules
```

2. This will open up gedit with the modules list. Put this at the bottom of the file, hit save and close the file. 

```
bcm43xx
```

3. Reboot. Hopefully this is the module you need, if so then it should be working just fine.

---

### Post by Nehvrook on 2007-10-21
Thanks I understand. Have it working properly now :)

---

