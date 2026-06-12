---
title: "conky is broke"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by sedoyksa on 2011-08-14
hi
i have conkyforecast
and weather on my desktop
but i have only 2 icons although there should be 4
then i start my conky i have message 
> Conky: Unable to load image '/usr'

---

### Post by babakott on 2011-08-14
I read your conkyrc and the two lines that call an image are remarked out, so thats not the issue. Also your forecastconfig doesn't call an image file.

I noticed you said you had conkyforecast AND weather. Is there another weather script?

---

### Post by sedoyksa on 2011-08-14
emm.. how i can find it?
i think that there is no more

---

### Post by sedoyksa on 2011-08-14
maybee this.. but here only coordinates on icons

---

### Post by babakott on 2011-08-14
> **sedoyksa said:**
> maybee this.. but here only coordinates on icons

Yes, here is where you are getting your errors. I knew I read something about this. Check out this [post]("http://crunchbanglinux.org/forums/topic/7765/conky-weather-images-are-not-loading/") over on the crunch bang forums.

---

### Post by sedoyksa on 2011-08-14
i have all icons from 
/usr/share/conkyforecast/images/weathericons /usr/share/conkyforecast/images/moonicons /usr/share/conkyforecast/images/bearingicons

and my inet connection is ok
but i still have only 2 icons

---

### Post by babakott on 2011-08-14
Try this. Open Synaptic and search for libimlib2 and see if it is installed. If not, install it.

---

### Post by sedoyksa on 2011-08-14
when i try to reinstall it i have msg from synaptic 
 	Quote:
 	 	 		 			 				Failed to change! 
You must first correct the errors in the packets. 			 		 	 	 
why? what packedges? how

---

### Post by sedoyksa on 2011-08-14
i reinstall libimlib2 and restart conky but i still have 2 icons

---

