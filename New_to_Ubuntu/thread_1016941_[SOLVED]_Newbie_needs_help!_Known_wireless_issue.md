---
title: "[SOLVED] Newbie needs help! Known wireless issue"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by theair on 2008-12-20
My newly-installed Ubuntu seems to be recognizing my hardware all fine, save for my wireless card. Extensive research on this on my part has failed to this point in fixing anything, but the process is greatly hindered by how much of a newb I am (I'm still figuring out terminals, run commands, etc).

I've found an excerpt from the known issues list that highlights my problem exactly. I can't seem to find the "linux-backports-modules-intrepid-generic package to install, however. 

I'm using a Toshiba Satellite A215 laptop with an Atheros AR5007EG wireless network adapter. I'm currently using dual-booting with Vista and Ubuntu, and I'm without Internet on the Ubuntu side, as I'm not directly hooked up through ethernet or anything. If I'm going to need internet connectivity to fix the problem, please let me know.

The "known issues" information:

Atheros ath5k wireless driver not enabled by default

The version of the ath5k driver for Atheros wireless devices included in Linux 2.6.27 interferes with the use of the madwifi driver for some wireless devices and as a result has been disabled by default. Many Atheros chipsets will work correctly with the madwifi driver, but some newer chipsets may not, and the madwifi driver may not work with WPA authentication. If you have an Atheros device that does not work with madwifi, you will want to install the linux-backports-modules-intrepid-generic package, which includes an updated version of the ath5k driver. While not installed by default, this linux-backports-modules-intrepid-generic package is included on the Ubuntu 8.10 CD and DVD images for ease of installation. 

Thanks in advance for any help. I'm very impressed with how helpful the community is here, and I'm excited to free myself from Windows. :)

---

### Post by nothingspecial on 2008-12-20
***edit*** Read my next post before you try this


In your menus system > administration > hardware drivers
Disable the atheros driver in there. Then accessories > terminal and copy and paste -


  ```
sudo apt-get install linux-backports-modules-intrepid-generic
```

Then```
 sudo modprobe ath5k
```to load the driver.

Then to make the driver load every time you boot ```
gksudo /etc/modules
```

add this to the bottom of the file```


ath5k
```

save
close 
reboot

If that doesn`t work we`ll try madwifi.

---

### Post by nothingspecial on 2008-12-20
Reread your post. You will need an internet connection for the above instructions. Can you plug your laptop into your router?

If not it will be easier to use madwifi. Let me know quick, I`m going to the pub in half an hour.

---

### Post by theair on 2008-12-20
I can hook my laptop up directly to my router.

Thanks so much!

---

### Post by nothingspecial on 2008-12-20
By the way, if apt-get says that it cannot find the package, go to system > administration > software sources and make sure all the sources in the Ubuntu Software tab is checked, (the 2 in the third party tab wouldn`t be a bad idea either)

---

### Post by theair on 2008-12-20
This worked perfectly. You ended an hours-long struggle between myself and my wireless card. Thank you so much!

---

### Post by nothingspecial on 2008-12-20
No problem. Will you mark the thread solved so other users will Know it is a solution.

Click Thread tools near the top of the page and mark it solved.

Glad I could help:guitar:

---

