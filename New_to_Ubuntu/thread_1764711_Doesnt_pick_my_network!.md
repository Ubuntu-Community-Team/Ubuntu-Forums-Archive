---
title: "Doesnt pick my network!"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by mojo706 on 2011-05-22
I set up everything right because it can pick up networks nearby but the problem is that it does not pick up my network. I have been on the forums for weeks to fix the first problem now it doesnt pick my network what might be the problem? lshw -C Network says my driver=ndiswrapper+netathw 
Could someone help me solve this problem? 
Thank You for your help!

---

### Post by bazcor on 2011-05-22
Sounds like a problem with the router.
* is the wireless enabled in the router? I assume you are using a router, if so you can log on to the web interface through a browser to check its settings.

* Maybe try changing the channel your router is using in case there is a lot of other radio signals on the the same frequency.

Can't think of any other reason that you can pick up other routers but not your own, perhaps the router is faulty? Can you find it's signal with another wi-fi enabled computer?

Good luck .. Barry

---

### Post by mojo706 on 2011-05-22
Hey Barry, the thing is on my Windows 7 on the same laptop I use the network but on Natty it doesnt pick what is the problem or mayB its because my wpa_supplicant is empty? Thank you for the help

---

### Post by bazcor on 2011-05-22
I would of thought,('though I'm not certain), that the router would show up even if it's encrypted with WPA.

Can't think of anything else at the moment, but perhaps someone with a more intimate knowledge will turn up!

Good luck .. Barry

---

### Post by gandaran on 2011-05-22
> **mojo706 said:**
> Hey Barry, the thing is on my Windows 7 on the same laptop I use the network but on Natty it doesnt pick what is the problem or mayB its because my wpa_supplicant is empty? Thank you for the help
SSID is hidden? if you know the network SSID try to setup connection in the network manager wireless tab with the SSID and WPA password then watch the panel network icon if it connects.

---

### Post by audiomick on 2011-05-22
> **gandaran said:**
> SSID is hidden? 

Would be my first guess. W7 still finds it maybe because it had been set up before the SSID got hidden?

---

### Post by mojo706 on 2011-05-22
IT says connection established but I cant connect now what could be the problem?  I have been working with wired connection.

---

### Post by crispy_420 on 2011-05-22
Start from the beginning and work your way out. Rule out the router first.

If you take off all security settings from router does it work? If it does, setup security settings again (WPA personal). 

You mentioned Windows 7 connected right? Was it the same machine as a dual boot? 

What chipset is the wireless card?

Hey at least you will get to change your password.

---

### Post by mojo706 on 2011-05-22
Now there is the password nagging haha It seems like today is the day I get all my problems in one package how do I stop it from asking for password all the time?

---

### Post by mojo706 on 2011-05-24
Thank you everyone it picked the network just like magic!

---

