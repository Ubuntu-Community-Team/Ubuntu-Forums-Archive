---
title: "lets discuss about temperature !!"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by xieu90 on 2009-01-16
hi everyone, i have just bought a brand new laptop from lenovo
i installed linux mint 6 (a copy and modified ubuntu intrepid ) there and xp

in xp i installed speedfan 
in mint i installed  lm-sensors and sensors-applet (also hot babe)

and in both i tried to open a lot of programs

somehow in xp the temperature of my cpu is stabil and stay at around 25-26 Celsius

in mint the temperature start at 37 (normally*, but now my room is so cold, and it is around 34 right now) and it might go up to 50 in some second with only firefox (when i open 7 tabs at the same time)


why is the temperature in linux hotter then in xp ? because of the driver?
are there any way to keep my cpu as cool as xp ?

---

### Post by SteveDee on 2009-01-16
I suggest you start by checking that lm-sensors is giving you correct readings.

If your BIOS can display cpu temperatures, you can run Linux for a while with no apps running until the temperature seems stable. Then reboot into BIOS and see if you get more or less the same reading.

---

### Post by redseventyseven on 2009-01-16
If there really is a 9-10 degree centigrade (about 16-18 fahrenheit) difference then you should be able to detect it by touch.

Work with your laptop on your lap for about 15 mins in XP, then 15 mins in Linux. Does it feel hotter?

---

### Post by xieu90 on 2009-01-16
unfortunately my bios doesnt display anything about temperature or fanspeed.

somewhen i booted into xp and opened fanspeed. the temperature of cpu was around 30-31. but i am not so sure about this event.


are there any other way to check if lm-sensors gives me the correct reading ?

---

### Post by SteveDee on 2009-01-17
> **xieu90 said:**
> unfortunately my bios doesnt display anything about temperature or fanspeed.

somewhen i booted into xp and opened fanspeed. the temperature of cpu was around 30-31. but i am not so sure about this event.


are there any other way to check if lm-sensors gives me the correct reading ?

Well, I'd do something similar to redseventyseven's suggestion. Run the computer in XP for 15mins but without any apps running. Note the temperature. Then reboot into Linux and see if you get a similar reading.

You can also then let it run (without any other apps running in Linux) and see if the temperature climbs or falls from its starting value.

---

