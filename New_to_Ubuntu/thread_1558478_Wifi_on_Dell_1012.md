---
title: "Wifi on Dell 1012"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by Thorger on 2010-08-22
Hello Community ):P,

i installed ubunto 10.40 i386 on my dell 1012 netbook using usb drive (dual boot with windows 7). I needed to know if everything works and if i get access to the internet!
installation abd everything worked fine. But i can't get wifi to work and i do not
have access to a wired internet connection at the moment. so what can I do?

Already looked up here [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

Tried the drivers for i386 from here [http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source)

but ubuntu gives me some message that i can't install them? I am looking for a easy solution as i am a windows user till now.

thank you in advance

---

### Post by jonnywombat on 2010-08-22
A possible solution is in this thread [here]("http://ubuntuforums.org/showthread.php?t=1556912")... post #5

---

### Post by Thorger on 2010-08-22
> **jonnywombat said:**
> A possible solution is in this thread [here]("http://ubuntuforums.org/showthread.php?t=1556912")... post #5

Hey thanks. But there is not such an option i only have internal WLAN enabled or diabled as an option. I got it enabled. And it is working on windows 7 so it won't be a bios issue i guess.

---

### Post by Thorger on 2010-08-22
anyone?

---

### Post by mamut0o1 on 2010-08-22
if you have the driver from windowsXP version; you could copy the driver files to ubuntu then use ndiswrapper tool to extract the driver.
using command ndiswrapper -i (locate .inf file name)
then you can issue command: 
ifconfig wlan0 up
iwlist wlan0 scan    ## to scan network

---

### Post by Thorger on 2010-08-22
sorry is there no possibility to get a damn driver for my wifi card? :sad:

---

### Post by Thorger on 2010-08-24
up... :KS

---

### Post by bkratz on 2010-08-24
> **Thorger said:**
> sorry is there no possibility to get a damn driver for my wifi card? :sad:

See post 2 of this thread

[http://ubuntuforums.org/showthread.php?t=1532288](http://ubuntuforums.org/showthread.php?t=1532288)

---

### Post by GaryTheCat on 2010-08-24
very curious 

what's your output from running

```
lspci
```

in a terminal window?

---

