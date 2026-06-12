---
title: "HP mini and Bluetooth"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by stalkier on 2009-11-15
Ok I got a new netbook a few days ago. The first thing I did was get rid of Windows 7 Starter edition. I installed Ubuntu 9.10 (not remix) from a SDcard. Works like a charm. Well all except the bluetooth. I cannot get the bluetooth adapter to enable. Here is the following specs of the system:

Intel Atom N270 (1.60GHrz)
160GB hdd
1GB DDR2
webcam
802.11a/b/g WLAN & Bluetooth
Intel Graphics Media Accelerator 950
5-in-1 Digital Media Reader

I have Cheese installed for the webcam to work. Works perfect. I have Blueman installed from PPA. I am unable to enable the adapter.

---

### Post by pilot4pay on 2009-11-15
> **stalkier said:**
> Ok I got a new netbook a few days ago. The first thing I did was get rid of Windows 7 Starter edition. I installed Ubuntu 9.10 (not remix) from a SDcard. Works like a charm. Well all except the bluetooth. I cannot get the bluetooth adapter to enable. Here is the following specs of the system:
 
Intel Atom N270 (1.60GHrz)
160GB hdd
1GB DDR2
webcam
802.11a/b/g WLAN & Bluetooth
Intel Graphics Media Accelerator 950
5-in-1 Digital Media Reader
 
I have Cheese installed for the webcam to work. Works perfect. I have Blueman installed from PPA. I am unable to enable the adapter.
 
I can't help you answer your question, but what was the process to make a bootable SD? I just won an HP mini 110, and would like to try the ubuntu out on it. Just a linux novice.

---

### Post by stalkier on 2009-11-15
> **pilot4pay said:**
> I can't help you answer your question, but what was the process to make a bootable SD? I just won an HP mini 110, and would like to try the ubuntu out on it. Just a linux novice.

The HP mini does not have a CDrom. I do not have an external drive. I had a SDcard so I just made it a bootable ISO. Work perfect for what I needed it for.

---

### Post by pilot4pay on 2009-11-18
> **stalkier said:**
> The HP mini does not have a CDrom. I do not have an external drive. I had a SDcard so I just made it a bootable ISO. Work perfect for what I needed it for.
Ok, how did you make the SD a bootable ISO? I'm not an expert, so I could use some directions please.

---

### Post by stalkier on 2009-11-18
> **pilot4pay said:**
> Ok, how did you make the SD a bootable ISO? I'm not an expert, so I could use some directions please.

Use LiveCD - goto System - Administration - USB Startup Disc Creator. You can then choose to make the SDcard a bootable ISO.

---

### Post by rustutzman on 2009-11-18
Try installing and use blueman bluetooth manager instead of the default. That's what I had to do for my eee 1000he.

Russ

edit: missed you already had this. What kind of bluetooth device are you trying? Mine works with stereo headphones and my MS 5000 bluetooth mouse. For the mouse I had to run ```
sudo hidd -search
``` to pick it up

---

### Post by pilot4pay on 2009-11-18
> **stalkier said:**
> Use LiveCD - goto System - Administration - USB Startup Disc Creator. You can then choose to make the SDcard a bootable ISO.
 
So I have to be running ubuntu on a machine in order for this to work in the first place?

---

