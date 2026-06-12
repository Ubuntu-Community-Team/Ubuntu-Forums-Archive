---
title: "Ubuntu hates Broadcom 4318 still?"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by hc803 on 2010-12-15
I don't see a thread where a definite solution is posted for the Broadcom 4318 AirForce One 54g wifi card. 
 
Should I just avoid Linux on any computer with this card? Or am I missing the fix?

---

### Post by Hippytaff on 2010-12-15
I think Broadcom have only recently opened up the drivers for us open source types, so I would imagine better support for broadcom wireless devices is on the way...in the mean time there are the standard fixes that you are aware of? :-)

---

### Post by hc803 on 2010-12-15
I did see that Broadcom has provided Linux drivers.
As for the "standard fixes", it looks like there are several recommendations, but that they work for some and not others.
I guess I'm just looking for a "Yes, this is how you fix the problem" thread.

---

### Post by trinitydan on 2010-12-15
This chipset is actually pretty well supported now.  There is a Broadcom B43 wireless driver available via system>administration>additional drivers.

---

### Post by Hippytaff on 2010-12-15
> 
I guess I'm just looking for a "Yes, this is how you fix the problem" thread.

I haven't searched ;-), but you can always try doing (whilst plugged in via ethernet)
```

sudo apt-get update && sudo apt-get upgrade

```

Then go to System -> Administration -> Alternative Drivers, and install the recommended BCM driver if there is one. If not post back :-)

---

### Post by coffeecat on 2010-12-15
> **hc803 said:**
> I guess I'm just looking for a "Yes, this is how you fix the problem" thread.

Have a look here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

The 4318 is specifically mentioned in that.

---

### Post by Hippytaff on 2010-12-15
> There is a Broadcom B43 wireless driver available via system>administration>additional drivers.
is it sorted now or does it still not work?

---

### Post by Bluenoser81 on 2010-12-15
> **Hippytaff said:**
> I think Broadcom have only recently opened up the drivers for us open source types, so I would imagine better support for broadcom wireless devices is on the way...in the mean time there are the standard fixes that you are aware of? :-)

I could not get my Broadcom wireless card to work in 10.04LTS using various means and drivers, until I tried out 10.10 and it worked fine out of the box with Broadcom's new open source drivers. So maybe give 10.10 a shot?

---

### Post by degarb on 2010-12-15
> **Bluenoser81 said:**
> I could not get my Broadcom wireless card to work in 10.04LTS using various means and drivers, until I tried out 10.10 and it worked fine out of the box with Broadcom's new open source drivers. So maybe give 10.10 a shot?


I haven't updated my laptop for fear of loosing the wireless card.  It has no ethernet cat port.  I am NOT going out and buying one.   I am glad to hear there may be out of box drivers.   I followed directions as a new ubuntu user for two days with no luck, Until, I tried installing a wireless windows driver thingy from the repo, and in 1 minute installed the windows driver.
  
I also only have a half a gig free on drive.  So, is 10.1 larger than 9.10?

---

### Post by trinitydan on 2010-12-15
> **Hippytaff said:**
> is it sorted now or does it still not work?

For my Gateway MX6455, it works fine.  I am no stranger to Broadcom 43xx driver problems on that machine either.  At one point I remember messing around with ndiswrapper, then a Broadcom patch (.deb package) came out that I used for a while, but in 10.10 it works fine, just select the additional restricted driver and it works.

---

### Post by hc803 on 2010-12-15
just an update, i've installed 10.10 on the computer (which I'm using as I type via wired connection) and updating drivers and the card does not work. 

guess i'll be working on fixing it tomorrow.

edit:  computer needed to be restarted.  wifi now working.  will keep updated.

---

