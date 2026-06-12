---
title: "Reestablishing connection to wireless network"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by Timothy Butwinick on 2006-09-10
Hello.
I am using a wireless network for my laptop, which works great, apart from one little problem: When it loses connection with the router if I, say, walk out of its range, it will not automatically reestablish it if I put it within range again. The only way to do this that I know of, is rebooting the computer. Is there some other way (automatic or manual) to do this?

By the way, the wireless card made Windows XP freeze at the instant I inserted it, while Ubuntu, using the drivers for WinXP, managed to do it more or less automatically! Since both the hardware and the drivers are working, it only proves another aspect in which Linux beats Windows. Thanks to the ones who made ndiswrapper!

---

### Post by andmar on 2006-09-10
i was wondering the same thing i have only been using it since last night .and was looking for over an hour how to detect a wireless network ,and could only do it thru a reboot.plus the wireless card would not work from the cd i had to install os to get it up.so i installed on a old harddrive i had .not sure if you go to system/admin/network tools then go to wireless /config and it list available networks you can connect to .

---

### Post by linuxusr50 on 2006-09-10
This should do it.

```
sudo ifup -a
```
```
sudo dhclient
```

---

