---
title: "Broadcom BCM need help with wireless"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by FNGtyler on 2007-03-22
OK

Newbie needs help again

I started reading the wifidocs and found a tutorial
I followed it
started by downloading all the headers, by going to synaptic and searching build essential, installed that then searched linux headers, i checked every box and installed all of those.

next i went to terminal typed apt.get install gcc-3.4 gcc-3.4-base cpp-3.4
next i searched ndiswrapper version 1.1
the i attempted to follow the link for my card driver and link is invalid i went to acer's website and download the appropriate driver.
I then unzipped it went to terminal and typed
ndiswrapper -i bcmwl5.inf

then i typed ndiswrapper -l
it says:
Installed ndis drivers:
bcmw15  invalid driver!
bcmwl5  driver present, hardware present 
bcmwl5.ing      invalid driver!
root@laptop:~/wire# 

what did I do wrong, i cant get this damn thing to work
please help.
very new to linux so please be detailed

---

### Post by Floppyjoe on 2007-03-22
> **FNGtyler said:**
> OK

Newbie needs help again

I started reading the wifidocs and found a tutorial
I followed it
started by downloading all the headers, by going to synaptic and searching build essential, installed that then searched linux headers, i checked every box and installed all of those.

next i went to terminal typed apt.get install gcc-3.4 gcc-3.4-base cpp-3.4
next i searched ndiswrapper version 1.1
the i attempted to follow the link for my card driver and link is invalid i went to acer's website and download the appropriate driver.
I then unzipped it went to terminal and typed
ndiswrapper -i bcmwl5.inf

then i typed ndiswrapper -l
it says:
Installed ndis drivers:
bcmw15  invalid driver!
bcmwl5  driver present, hardware present 
bcmwl5.ing      invalid driver!
root@laptop:~/wire# 

what did I do wrong, i cant get this damn thing to work
please help.
very new to linux so please be detailed
You need to delete the two invalid drivers that you have here.
```
sudo ndiswrapper -e bcmw15
```
and 
```
sudo ndiswrapper -e bcmwl5.ing
```

---

