---
title: "New to Ubuntu 8.10, Broadcom Help"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by Dr.Suse on 2008-11-14
ok, ive always been interested in linux, just never really made the "complete switch" to it. i tried to install it again but am running into some wlan trouble. my ONLY available connection is by wireless hotspot, i live in an apt complex that supplies wireless but not a wired connection :( so how can i get my wlan card to work if i have no available access to the internet? (until my wlan works, i have no connection, but i need a connection to get my wlan to work, its a vicious paradox)

in the past ive been able to install bcm43xx-fwcutter and then point it to a w_apsta.o on my usb drive, and viola, it would work. but it doesnt seems to work so with 8.10 :(



here are my questions:

whats the difference between bcm43xx-fwcutter and b43-fwcutter?

b43 tries to connect to the internet for the firmware. cant i just point it to my own w_apsta.o and have it use that instead?

or is there a command line where i can install my local w_apsta.o firmware so that i can enable the restricted drivers without it needing to connect to the internet in order to retrieve it?

sorry if there are a million posts about this, but ive searched and cant find the answers to my specified questions ^above. im aware of ndiswrapper and ive tried to use it in the past, without success. so id prefer to use the bcm43xx or b43 method.

im using:
ubuntu 8.10
[compaq presario v5305wm]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00783092&lc=en&cc=py&product=3231960")
i have windows driver versions 4.100.15.5 (10/12/2006) and 4.170.77.3 (3/21/2008 ) available to me, and thats what my card requires.
i have a wireless enabled windows partition

---

### Post by superprash2003 on 2008-11-14
try this [http://prash-babu.blogspot.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://prash-babu.blogspot.com/2008/11/how-to-configure-broadcom-wireless-in.html)

---

### Post by iponeverything on 2008-11-14
Can you install the firmware with:

```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

---

### Post by Dr.Suse on 2008-11-15
> **iponeverything said:**
> Can you install the firmware with:

```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

thank you, this actually helped me alot!

i did a search about what you posted^ and tried it out. i found this thread [http://ubuntuforums.org/showthread.php?t=763995](http://ubuntuforums.org/showthread.php?t=763995) where i was having the same problem.


```

b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o

b43-fwcutter --unsupported -w /lib/firmware /broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

```

after using the above commands, my restricted drivers didnt need to connect to the internet to be enabled!

---

### Post by sclewin on 2008-11-16
I don't know if my problem is the same or not.  My wife's laptop haves a broadcom wireless card and the enable wireless is greyed out.  I tried using everything I found here, but nothing helped.

---

### Post by spyro187 on 2008-12-11
> **sclewin said:**
> I don't know if my problem is the same or not.  My wife's laptop haves a broadcom wireless card and the enable wireless is greyed out.  I tried using everything I found here, but nothing helped.


Mine was also greyed out when I started and the only instructions that I could get to work were these [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Once it is working don't update if Ubuntu asks. I had it working and then some driver update broke it.

---

### Post by Ayuthia on 2008-12-11
> **spyro187 said:**
> Mine was also greyed out when I started and the only instructions that I could get to work were these [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Once it is working don't update if Ubuntu asks. I had it working and then some driver update broke it.

Out of curiosity, what do you mean about Ubuntu asking you to update b43?  Do you mean that you are still using the original kernel version and not upgrading it?

Also, which card do you have (lspci -nn)?

---

### Post by spyro187 on 2008-12-11
> **Ayuthia said:**
> Out of curiosity, what do you mean about Ubuntu asking you to update b43?  Do you mean that you are still using the original kernel version and not upgrading it?

Also, which card do you have (lspci -nn)?

I had base install of 8.10. Then I installed the b43 firmware which got the wireless working. After that I got the message from Synaptic that there were updates available. So I let it update all packages. Following that I got a bubble pop up saying that there was a driver update for my Broadcom so I clicked install which appears to have broken it. 

Broadcom BCM4306 802.11b/g

---

