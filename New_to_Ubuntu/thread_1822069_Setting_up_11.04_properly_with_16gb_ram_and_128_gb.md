---
title: "Setting up 11.04 properly with 16gb ram and 128 gb ssd"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by samthedrunk on 2011-08-10
I have recently upgraded my desktop. I brought a 128gb ssd and since ram is cheap I put 16gbs in it. 

So it's a i7 with 128 ssd, 2tb hard drive and 16gb ram. 

I was wondering if someone could help me or point me to a link on setting the installation up properly. I have read that you can place swap file in ram or do I have to worry about stuff like that. 

If I just used the installer and just follow the standard install will it damage or wear it out quicker? 

The way I am doing it now is just saving all the data into the spinning drive.  

I want it to start up fast and stuff like that. So if there is any tipsi should know that would be great.

---

### Post by elliotn on 2011-08-10
I find none wrong with the standard installer

---

### Post by srisharan on 2011-08-10
the standard installation should work fine

---

### Post by Jagoly on 2011-08-10
If your talking about damaging your SSS, then yes, a bit of precautions may help. With 16gbs of ram, you'll only ever use swap to hibernate. If you do use hibernate, then put 17 gigs on the 2tb drive. Alot of writing to an ssd can degrade its performance over time, so yu could mount some non-speed critical locations that are rarely read on the big drive to. Like your apt cache, certain parts of home (not the whole thing as that will drop system performance.

I remember seeing a great guide on the arch Linux forums, maybe you google that.

---

