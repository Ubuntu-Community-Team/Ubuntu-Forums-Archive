---
title: "BCM4306 Rev2 Wireless Help, nearly suicidal"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by ambderm on 2010-11-14
I thought I would give this ubuntu stuff a try and rehab an older Dell E510, that we basically use as a Media extender, netflix/hulu etc...  It had gotten painfully slow so I just did a complete reformat clean install of Ubuntu 10.10 off a thumb drive.  

I moved the desktop into the office to hook it up to the ethernet for the setup.  Normally it uses  the Linksys PKW-WMP54g which I have found through hours of research that it has the BCM4306 Rev2 chip which requires the B43legacy driver.  

Everything went smoothly.  I am stuck now still without wireless connection.

Additional drivers windows says the B43legacy driver is installed, activated and currently in use.   Which I thought was a good thing.  

Still there are no wireless connections being found under network connections.  Don't know if this is still a driver problem or just a configuration problem? 

I spent the entire night reading forum after forum but could not find anyone in this situation.

I am not a professional so please speak slowly and I appreciate any help.  I think I am going to love it if I could just get passed this.

---

### Post by cariboo on 2010-11-15
What is the output of:

```
sudo lshw -C network
```

---

### Post by Hippytaff on 2010-11-15
This is a good for reference [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
and the output of the command posted by cariboo907 will help work out whats happening.
 
```

rfkill unblock all

```
is also worth a punt :-)

---

### Post by TBABill on 2010-11-15
I just did an install on 10.10 with the BCM4312 and I was quite unhappy till I got it working. To start with, I had to do as Hippytaff posted above. However, to know if you are hard or soft blocked, which it appears the driver does in 10.10 for some (@#!@#) reason, type in a terminal ```
sudo rfkill list
``` Once you know if you are blocked then you will know if the unblock command will help. If it returns "Yes" to either soft or hard blocked, then you know to use the other.
 
I had to install, uninstall, reinstall, reboot, reinstall, reboot.....and on and on it went till it finally decided to work. Mine uses the STA driver, but I would be willing to bet you will go through similar steps and it will just all of a sudden work after you have repeated the same steps a few times. No explanation I can come up with, but a few complete removal and reinstall in Synaptic and it finally decided to play along.
 
Wireless in 10.04 is just rock solid for my Broadcom BCM4312, but a total pain to get working in 10.10. Gotta love progress :)

---

