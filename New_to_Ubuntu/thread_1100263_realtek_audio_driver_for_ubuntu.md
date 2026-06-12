---
title: "realtek audio driver for ubuntu"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Yogz1 on 2009-03-19
hello guys.I am very new to ubuntu.just got ubuntu 8.10 CD. i just wanna know if the realtek audio driver works for ubuntu.If not may i know the audio drivers that works for ubuntu.I will be very happy to get response.:)

---

### Post by dajasc on 2009-03-21
Have integrated Realtek sound and it works fine.

---

### Post by SunnyRabbiera on 2009-03-21
My realtek also works, if it works on the live CD it will work on a installed system

---

### Post by Yogz1 on 2009-03-22
> **dajasc said:**
> Have integrated Realtek sound and it works fine.

cud u help me out on this issue? Like how wud u integrate it ?much awaiting ur response :)

---

### Post by Yogz1 on 2009-03-23
well i just integrated the realtek.but i dont hear anything.my chipset is intel 915GV.wanna know if i cud do something.please help

---

### Post by Julius1988 on 2009-03-23
Your CPU specs please?

---

### Post by Yogz1 on 2009-03-24
i use intel 915/915GV chip

---

### Post by kansasnoob on 2009-03-24
Start by installing gnome-alsamixer either from Synaptic Package Manager or you can go to terminal and run this command:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in the menu under Sound & Video:

[ATTACH]107480[/ATTACH]

[ATTACH]107481[/ATTACH]

Take special note of the first three toggles and the last four (VIA) toggles.

If that doesn't help post the output from terminal of:

```
aplay -l
```

NOTE: those are lower case L's.

---

### Post by Yogz1 on 2009-03-29
> **kansasnoob said:**
> Start by installing gnome-alsamixer either from Synaptic Package Manager or you can go to terminal and run this command:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in the menu under Sound & Video:

[ATTACH]107480[/ATTACH]

[ATTACH]107481[/ATTACH]

Take special note of the first three toggles and the last four (VIA) toggles.

If that doesn't help post the output from terminal of:

```
aplay -l
```

NOTE: those are lower case L's.
i tried the sudo apt-get install gnome-alsamixer command. and the output i received is 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-alsamixer
  


and then i tried the aplay -l command and the output is 


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Yogz1 on 2009-03-29
> **SunnyRabbiera said:**
> My realtek also works, if it works on the live CD it will work on a installed system

it didnt work on live CD :(

---

