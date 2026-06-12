---
title: "i have a webcam and i wanna use it."
date: 2009-01-02
forum: New to Ubuntu
---

### Post by jsf_pp on 2009-01-02
hola!
im tryin to install (or check if its installed) the drivers for my webcam but i see no program nor tab in system > admin to do so.

so what should i do?

i did a hardware test and all went perfect but no question at all about my webcam.

thanks !

---

### Post by stalkier on 2009-01-02
> **jsf_pp said:**
> hola!
im tryin to install (or check if its installed) the drivers for my webcam but i see no program nor tab in system > admin to do so.

so what should i do?

i did a hardware test and all went perfect but no question at all about my webcam.

thanks !

Not sure about the drivers, but you can install Cheese from the repos. It should work with your webcam. I know it works for my Logitech webcam.

---

### Post by jsf_pp on 2009-01-02
> **stalkier said:**
> Not sure about the drivers, but you can install Cheese from the repos. It should work with your webcam. I know it works for my Logitech webcam.

ok, im doin that right now.

thanks!

---

### Post by jsf_pp on 2009-01-02
no camera found.
damn!
lucky me. 

anyway, how can i do to make ubuntu fing it?

---

### Post by wolfen69 on 2009-01-02
first we need to know what kind of webcam you have. do in terminal: ```
lsusb
``` post output.

---

### Post by jsf_pp on 2009-01-04
> **wolfen69 said:**
> first we need to know what kind of webcam you have. do in terminal: ```
lsusb
``` post output.

```
julio@ubuntu:~$ lsusb
Bus 005 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

thanks

---

### Post by kwacka on 2009-01-04
See: [http://ubuntuforums.org/showpost.php?p=5055135&postcount=6](http://ubuntuforums.org/showpost.php?p=5055135&postcount=6)

Alternatively return it to retailer (not fit for purpose) and get a webcam from a manufacturer that will provide drivers.

---

### Post by Visible Spirit on 2009-01-31
**[[COLOR="Red"]This comment was moved to start a new thread specifically for this camera mdl/brand here.[/COLOR]](http://ubuntuforums.org/showthread.php?p=6657823#post6657823)** <-click


Greetings all,

I'm having no luck with my webcam situation. :(

I have an "Xirlink, Inc. IBM NetCamera" I'd like to use. It's the only webcam I have currently and I'm running Ubuntu Studio v8.04-(Hardy Heron). My webcam isn't recognized at all and I'm completely lost here. I'm learning Linux as we go. Although I can find my way around *somewhat* already, please bear this in mind - thanks. I'm going on two days of digging around with this project for a solution and gotten nowhere yet.

I've installed "Cheese" and "Camera Monitor" just to see if the system would recognize it, but no luck. Otherwise, I haven't installed anything else and I'm sure I need to find a driver to install for it as well. I have the latest Kernel update which is version 2.6.24-23-rt .

The USB list output is as follows: (webcam in red)
```
XXXXXXXXXX@ubuntu:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
[COLOR="Red"]Bus 003 Device 002: ID 0545:8002 Xirlink, Inc. IBM NetCamera[/COLOR]
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 059b:0032 Iomega Corp. Zip 250 (Ver 2)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 001 Device 001: ID 0000:0000  
XXXXXXXXXX@ubuntu:~$
```


If anyone can help me figure this out and get it working, it would be *greatly* appreciated. ;)


Regards,
Visible Spirit

---

