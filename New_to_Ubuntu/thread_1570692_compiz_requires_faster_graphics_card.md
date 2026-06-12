---
title: "compiz requires faster graphics card"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by mucky neighbour on 2010-09-08
I can't run all the compiz effects because I need a faster graphics card.
a) how do I identify what card I currently have and
b) how can I check to see whether there are driver updates I can download?

I'm using ubuntu 10.4.1 (?) on a dell vostro 1700

---

### Post by andrewthomas on 2010-09-08
post the output of 

```
lspci|grep VGA
```

---

### Post by plucky on 2010-09-08
> a) how do I identify what card I currently have


From a terminal ```
lspci
``` or ```
sudo lshw -C display
```


> b) how can I check to see whether there are driver updates I can download?


Open **System > Administration > Hardware Drivers** and see what loads or is loaded.

Good Luck

---

### Post by techningeer on 2010-09-08
> **mucky neighbour said:**
> I can't run all the compiz effects because I need a faster graphics card.
a) how do I identify what card I currently have and
b) how can I check to see whether there are driver updates I can download?

I'm using ubuntu 10.4.1 (?) on a dell vostro 1700

Run```
sudo lshw -c display
``` and post the output here.

---

### Post by halitech on 2010-09-08
maybe I'm missing something but if you need a faster video card, I don't see how updating the drivers (which Ubuntu is usually pretty good at doing) will make much of a difference. Now, if you mean you need to see if there are proprietary drivers that give 3d support so you can run compiz, thats another story completely.

According to what I found on google, you either have an Intel GM965 chipset or an Nvidia  GeForce 8400m. I hope if you really "need" to have compiz running that you have the Nvidia card and not the intel card.

---

### Post by mucky neighbour on 2010-09-08
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by mucky neighbour on 2010-09-08
given that it's a laptop, I don't fancy replacing the card. Someone mentioned that installing later drivers *may* help so that was my first port of call. If all else fails, I'll just put up with having no fancy effects :-)

---

### Post by halitech on 2010-09-08
chances are with it being a laptop, you probably can't replace the video card. I'm not sure if there are updated drivers for Intel video cards other then the opensource drivers you are using now.

---

### Post by silverglade00 on 2010-09-08
Ok, I have a netbook with an Intel Mobile GM945 Express that can run compiz smooth as silk with the default drivers. I also have a Dell Latitude laptop with the same GM965/GL960 that runs it insanely well. I don't think the video card is the issue. They use the default drivers that Ubuntu installs on its own. Mucky, have you run all your updates?

---

### Post by NightwishFan on 2010-09-08
Can you describe in more detail the exact problem, does compiz just not enable or is it very slow? If it does not enable perhaps your machine is blacklisted or not using the 'intel' driver.

---

