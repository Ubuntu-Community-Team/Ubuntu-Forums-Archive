---
title: "Can't get grub to show up at boot even with shift key"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by jerrynewt on 2011-02-06
Running 10.10  on my desktop (2 installs-1 straight 10.10 and 1 Zorin 4.0, a 10.10 customized OS). I installed the Zorin OS last so the system automatically booted to it even with the grub screen showing. I used startup manager and changed the boot to the straight 10.10 OS for my wife's daily use. My problem is I set startup manager to 0 seconds for showing grub and now even holding down the shift key during boot, I can't see the grub menu to get into my Zorin install. Seems whatever I change in etc/default/grub on her OS has no effect on grub. Thinking maybe the startup manager in the Zorin OS may be overriding any changes I make on her 10.10 system. Any ideas on haw to get this mess fixed. I miss my Zorin !! Many thanks....

---

### Post by JOHNNYG713 on 2011-02-06
Try tapping and pressing the Esc key at boot, I have heard that works!To bring up the grub screen, Though I have never had an issue!

---

### Post by jerrynewt on 2011-02-06
Ok tried first tapping esc key during boot and nada, then tried holding esc key during boot and same thing. Also tried tapping first and then holding shift key too, same result, can't get grub to come up. When holding shift key I get a momentary screen saying "Loading Grub" with a blinking cursor, then after about one or two seconds it goes right to my wife's OS.

---

### Post by jonnny_j22 on 2011-02-06
If you installed zorin last, it is it's bootloader being used unless you set otherwise.

If grubs configured from the other distro, you should be able to mount zorin's partition then edit the grub config file on that system to change the timeout
 
sudo gedit /ect/default/grub

and change

GRUB_TIMEOUT=0

to whatever you want. then 

sudo update-grub

to make it take effect.

If still no luck you should just be able to reinstall grub2 on ubuntu either using aptitude, or the live cd, and this will then take control of booting once more and replace zorin's grub in the boot order, with ubuntu as default and zorin as second choice.

---

### Post by techunit on 2011-02-07
reinstalling grub might be your best bet. when you edit the grub files are you updating grub? make sure you updeate it.

```
sudp update-grub
```

good luck

---

