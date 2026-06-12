---
title: "iwconfig problems"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by sankarj12 on 2006-12-24
I am having problems using iwconfig with my netgear wg111 v1 wireless usb adapter.  Everything seems to be configured properly.  When I enter my info. manually, I get an error saying that it could not apply those settings to the device.  What can I do?](*,)

---

### Post by disabled_20220313 on 2006-12-24
Are you sure you used ```
sudo iwconfig
```?

I have a similar trouble when I forget to use the sudo command to do it.

---

### Post by sankarj12 on 2007-01-01
I have entered```
sudo iwconfig
```.  I have permission, it's just that the program could not apply the settings to the device.  All the information shows up correctly (concerning 802.11x type and others) but when I try to manually configure it to work with my router settings, it failed to apply the settings to the device.

---

### Post by phossal on 2007-01-01
Post the command you're using. Post the output. Then post the output of the command:
```

sudo iwconfig wlan0

```

Without seeing anything, all we can do is guess. I use the wg111v2, and it's sometimes difficult to configure even when you can see it.

---

### Post by sankarj12 on 2007-01-02
I know you're not gonna like this, but when I entered all my information, no error messages appeared!:-D   No, it's not something meant to waste your time, it just magically worked.  Although, when I type in ```
sudo iwconfig wlan0
``` I get that there is no such device.  Instead, my device shows up as eth1.  I am sending this reply through Ubuntu.  Thank you so much for helping me.

---

### Post by phossal on 2007-01-02
I'm thrilled. The wg111 is awesome. I'm glad you're up and running. Happy Ubuntu'ing.

---

### Post by disabled_20220313 on 2007-01-03
Well thats still good news! I've also had that problem in the past with a Belkin PCI card.

Enjoy Linux and the internet.

---

