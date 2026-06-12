---
title: "Bluetooth???   help plz"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by juiceman on 2008-10-25
Hey guys,
I was curious.  If my system didn't have bluetooth, would Ubuntu still be running the bluetooth service?  I have ubuntu 8.04 with all the most current updates.

The service is running, but I am unsure if my system actually has bluetooth in it or not.  It is a possibility for my system and my friend says he thinks it had bluetooth but isn't sure.  Is there any way for me to definitively check and make sure?

I am trying to scan for bluetooth devices from my cell phone and its not showing up.  I'd like to be able to transfer files and do some things between my laptop and cell phone.

Please help!
Juice

---

### Post by melojo on 2008-10-25
open a terminal and type

```
cat /proc/devices
```

you may have it if rfcomm  is present.

rfcomm is for bluetooth

---

### Post by juiceman on 2008-10-25
> **melojo said:**
> open a terminal and type

```
cat /proc/devices
```

you may have it if rfcomm  is present.

rfcomm is for bluetooth


i see it right here. 
171 ieee1394
180 usb
189 usb_device
216 rfcomm
226 drm
253 pcmcia


thats a segment of the output.  looks legit.   wtf do I do now?

---

### Post by melojo on 2008-10-25
> **melojo said:**
> open a terminal and type

```
cat /proc/devices
```

you may have it if rfcomm  is present.

rfcomm is for bluetooth

I got on a system that does not have bluetooth and it shows rfcomm
so rfcomm does not mean you have bluetooth

sorry

not sure how to find out at the moment maybe someone else has an idea

---

### Post by melojo on 2008-10-25
what is the make and model of your pc?

---

### Post by juiceman on 2008-10-25
> **melojo said:**
> what is the make and model of your pc?

it is an ibm thinkpad R40.  it can come with it, or not.

---

### Post by melojo on 2008-10-25
> **juiceman said:**
> it is an ibm thinkpad R40.  it can come with it, or not.

thinkpad r40 is the family class. There should be a number for type and model.

Out of curiosity what does ```
lsusb
``` give you?

---

