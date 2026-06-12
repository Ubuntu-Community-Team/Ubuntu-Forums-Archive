---
title: "ubuntu 14.04 wifi disabled by hardware"
date: 2014-06-22
forum: Networking &amp; Wireless
---

### Post by jer2291 on 2014-06-22
i have ubuntu 14.04 installed on my asus laptop and ubuntu says wifi is disabled by hardware switch. but under windows 8 it says that its working.


please help.

---

### Post by jeremy31 on 2014-06-23
Try this suggestion if you haven't already

[http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

---

### Post by zemega on 2014-06-23
Asus laptop eh? just like mine. I'm not sure this will help or not. Asus 1225B, Windows 7 and Ubuntu 14.04. If you turn off the wifi inside Windows its a hardware  turn off and wifi will not work inside Ubuntu. If you leave it on inside Windows 7 and turn the laptop off, wifi will work inside Ubuntu. Why don't you try turning on the wifi inside Windows 8 and do a full shutdown (not the hybrid boot) and see if the wifi is working inside Ubuntu? Seems like Asus likes to give full control of the wifi including hardware switch control to Windows with their laptops. Can you tell us the laptop model no? It might help me make some decision later on.

---

### Post by sree15081947 on 2014-06-23
try

[I][B]sudo rfkill unblock all


[/B][/I]

---

### Post by chili555 on 2014-06-23
> **jeremy31 said:**
> Try this suggestion if you haven't already

[http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)Exactly my suggestion. Please let us know if it helped.

---

### Post by jer2291 on 2014-06-23
R510CA.

i have wireless on in win 8 but still off in ubuntu

---

### Post by chili555 on 2014-06-23
> **jer2291 said:**
> R510CA.

i have wireless on in win 8 but still off in ubuntuMay we please see:```
cat /etc/modprobe.d/asus_nb_wmi.conf
lsmod | grep asus
```Thanks.

---

### Post by jer2291 on 2014-06-24
options asus_nb_wmi wapf=1


asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi

---

### Post by jeremy31 on 2014-06-24
> **jer2291 said:**
> options asus_nb_wmi wapf=1


asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi

Have you tried the FN+ combo since using the option?  Depending on the model of your Asus, you might actually need a different setting for wapf

Should run the wireless script to see if something else is causing this ```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script[/FONT][/COLOR]
```

---

### Post by jer2291 on 2014-06-24
FN combo doesnt work


if i put my comp into sleep it changes the hardblock from yes to no

---

### Post by jer2291 on 2014-06-24
i tried the first part of the fix and it didnt work but i tried the hotkey and that worked for an on/off for now

---

