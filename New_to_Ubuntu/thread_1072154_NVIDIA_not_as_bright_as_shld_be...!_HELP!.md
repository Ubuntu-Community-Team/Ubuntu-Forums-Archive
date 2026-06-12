---
title: "NVIDIA not as bright as shld be...! HELP!"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by jkd18 on 2009-02-17
Hi, I just moved from Windows to Ubuntu on my Acer Aspire 4520 and can barely see thcreen!! Where is the brightness? Have downlaoded and installed the software have changed the appearances to Extra- but NO GO.. Please help!!! 

Thanks.

---

### Post by Cresho on 2009-02-17
"sudo apt-get install nvidia-settings" or just nvidia-settings in terminal because it may be installed already.

usually this isnt the case.  look at your media player gamma, brightness or contrast settings first before messing with nvidia.

---

### Post by jkd18 on 2009-02-17
Ok, will chk that thanks...

---

### Post by jkd18 on 2009-02-17
Nope- no luck:(

---

### Post by Elfy on 2009-02-17
No luck with what - installing it , using it?

You need to run it with root rights for any changes to survive a reboot

```
gksu nvidia-settings
```

You should find brightness in the colour correction tab.

---

### Post by alexandari on 2009-02-17
have you tried ENVY? It`s a software that installs your latest video drivers. You can find it in your package manager :)

---

### Post by Elfy on 2009-02-17
> **alexandari said:**
> have you tried ENVY? It`s a software that installs your latest video drivers. You can find it in your package manager :)

Good point - the OP doesn't actually state whether the graphics driver has been installed.

I would go with the Hardware Drivers before Envy though

---

### Post by jkd18 on 2009-02-17
Thanks people for ur advice. will try getting ENVY as well as chking hardware settings. The thing is that my windows OS also looks dim after the Ubuntu load, so am pretty flummoxed. Will keep u all posted. My Ubuntu detects NVIDIA but not applying it i think... no clue... :(

---

### Post by RomeReactor on 2009-02-17
Hi. Try running this in the terminal:
```
lshw -c display
```
and post back the complete output. It should show which driver the card is currently using. Have you tried resetting your monitor's options/settings?

---

### Post by jkd18 on 2009-02-17
:-) Hey all. Got it. Just right clicked the panel and clicked Add to Panel which has the brightness button...! WHEW! 

Thanks! :popcorn:

---

