---
title: "touchpad not working:-("
date: 2011-01-02
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-01-02
i have a dell inspiron laptop model 1464 with windows 7 n ubuntu 10.10 side by side...4m last few days my touchpad is not working at all on ubuntu but everything is fine in windows..pls anybody help me...thanks a lotttttttt:p:p:p:p

---

### Post by vivek.pandey on 2011-01-03
> **neo_aryan said:**
> i have a dell inspiron laptop model 1464 with windows 7 n ubuntu 10.10 side by side...4m last few days my touchpad is not working at all on ubuntu but everything is fine in windows..pls anybody help me...thanks a lotttttttt:p:p:p:p

somebody pls help me.. its irritating me not to be able to use my touchpad although i have a usb mouse

---

### Post by matt_symes on 2011-01-03
Hi

What kind of touchpad do you have?

Open a terminal and type

```
xinput --list
``` 

Post back the results. Maybe someone will know how to fix it.

Kind regards

---

### Post by vivek.pandey on 2011-01-03
> **matt_symes said:**
> Hi

What kind of touchpad do you have?

Open a terminal and type

```
xinput --list
``` 

Post back the results. Maybe someone will know how to fix it.

Kind regards

 Virtual core pointer                           id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SIGMACH1P U+P Mouse                     	id=14	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=16	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=17	[slave  pointer  (2)]
&#9116;   &#8627; USB USB Keykoard                        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HID 413c:8161                           	id=10	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_1.3M           	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=18	[slave  keyboard (3)]
    &#8627; USB USB Keykoard                        	id=12	[slave  keyboard (3)]

 i got an ouput similar to this ..s o now pls help

---

### Post by matt_symes on 2011-01-03
Hi

Enter this at the terminal. It will enable your touchpad if it is disabled. 

```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

Kind regards

---

### Post by vivek.pandey on 2011-01-03
> **matt_symes said:**
> Hi

Enter this at the terminal. It will enable your touchpad if it is disabled. 

```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

Kind regards

thanx this worked but can u pls tell me how was it automatically sidabled.?. i had thought it was some driver prob

---

### Post by mzakaria on 2011-02-11
Lovely Fix. Many thanks. I wonder if there is a way to know what caused the problem. Some error report maybe?

---

### Post by coabiguy on 2011-02-26
Thanks ... that did the trick for me. I used the Configuration Editor to see if it was already checked. It wasn't.

---

### Post by A4orce84 on 2011-02-26
I do not have a touchpad settings in my mouse

---

