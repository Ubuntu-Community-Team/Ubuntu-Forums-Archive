---
title: "how to find out the name of the exact graphic card model  i have installed?"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by werty2010 on 2011-07-22
i tried "lshw" but that just gave me,among others,this: Radeon HD 5600 Series
i've already knew that i just want to know if there is a way to know the exact model of the card through ubuntu(11.04) and not from a manual.
So if you know how, please let me know.

---

### Post by howefield on 2011-07-22
Try

```
lspci | grep VGA
```

---

### Post by haqking on 2011-07-22
> **werty2010 said:**
> i tried "lshw" but that just gave me,among others,this: Radeon HD 5600 Series
i've already knew that i just want to know if there is a way to know the exact model of the card through ubuntu(11.04) and not from a manual.
So if you know how, please let me know.


sudo apt-get hardinfo

if you cant find your card info already

---

### Post by matt_symes on 2011-07-22
Hi

```
lspci -nn | grep -i vga
```

Mine is

```
matthew@matthew-laptop:/etc/apparmor.d$ lspci -nn | grep -i vga
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]

```

Make 1002, model9712 (IIRC)

For extra information use 

```
lspci -nnk
``` 

(kernel modules)

```
lspci -nnv
```

For verbose information.

Kind regards

---

### Post by howefield on 2011-07-22
> **haqking said:**
> sudo apt-get hardinfo

if you cant find your card info already

Do you mean

```
sudo apt-get install hardinfo
```

---

### Post by techfighterminal on 2011-07-22
I'm fairly new to Linux so I don't have commands. but you could always search your PC on google. 

they usually have some type of id on the casing. through some searching i found my model was an HP-s3100 slim. also gave me info on ram, and other internals.

---

### Post by pqwoerituytrueiwoq on 2011-07-22
ATI Technologies Inc M880G [Mobility Radeon HD 4200]
that is your card

for extra info on your card
```
sudo apt-get install hwinfo
sudo hwinfo --gfxcard
```

---

### Post by werty2010 on 2011-07-22
tried both and gave me the same thing:Radeon HD 5600 Series
although i got what i wanted through googling the corresponding to mine example("Make 1002, model9712 (IIRC)") [matt_symes]("http://ubuntuforums.org/member.php?u=1067998") gave.

thank you all

---

### Post by haqking on 2011-07-22
> **howefield said:**
> Do you mean

```
sudo apt-get install hardinfo
```

DOH, my bad, not enough coffee yet i guess ;-)

---

### Post by pqwoerituytrueiwoq on 2011-07-22
if you are trying to get a driver run this
```
/usr/bin/jockey-gtk
```

if you are trying to get a newer driver version do this first (i don't think this is needed for 11.04)
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;
```

---

