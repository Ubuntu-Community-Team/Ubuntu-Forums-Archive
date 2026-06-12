---
title: "help with wireless"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by kyusan on 2010-11-10
hi all im new to ubuntu i have 10.10 and i cant get my wireless to work when i click on it it gives me a message that says something along the lines of firmware missing

---

### Post by bioterror on 2010-11-10
> **kyusan said:**
> hi all im new to ubuntu i have 10.10 and i cant get my wireless to work when i click on it it gives me a message that says something along the lines of firmware missing

Could you please tell us your laptop's/desktop's brand and model so that we can find out what kind of chipset it has.

---

### Post by Hippytaff on 2010-11-10
Also please post the output of the following commands in a terminal (open a terminal with CTRL+ALT+T)
```

lspci

```
Might as well post these as well, but lspci will give us the chipset to identify the driver, from there we can find out if it is installed etc etc
```

iwconfig

```
```

lshw -C network

```
 
when you post the ouput, wrap the output text in code tags (highlight the text and click the # button
:-)

---

