---
title: "Laptop webcam help"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by Brian from Denmark on 2011-06-02
Hi, im new to linux and have installed ubuntu 11.04 64bit on my laptop, and the only thing thats not working is my webcam.

Can anyone help me to get it working?

My laptop is a Medion akoya p6622 and i think the integrated webcam is a 1,3mp cyberlink cam

---

### Post by gordintoronto on 2011-06-02
If you open terminal and enter the command:
lsusb
it will tell you about your USB devices. One will be your webcam. For example:
Bus 003 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

The really useful part follows ID, in my case, 0ac8:303b
You can Google that along with "linux" and see what you get.

Have you installed and tried "Cheese webcam booth"?

---

### Post by no2498 on 2011-06-03
do you need to click any key's to turn the cam on like fn+f10

in a terminal type dmesg click enter
after it stops type lsusb click enter

if it comes up as a rico cam you will need to get a driver for it

after you find out what cam it is

in a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam




















=

---

### Post by Brian from Denmark on 2011-06-04
> **gordintoronto said:**
> If you open terminal and enter the command:
lsusb
it will tell you about your USB devices. One will be your webcam. For example:
Bus 003 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

The really useful part follows ID, in my case, 0ac8:303b
You can Google that along with "linux" and see what you get.

Have you installed and tried "Cheese webcam booth"?

Yes i have cheese webcam booth, it says no device found..

When i type lsusb is says:


brian@brian-P6622:~$ lsusb
Bus 002 Device 003: ID 04fc:05da Sunplus Technology Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Whitch one is the cam?

---

### Post by no2498 on 2011-06-05
can you get the light to come on for the cam
i do not see it in the lsusb

---

### Post by Brian from Denmark on 2011-06-05
> **no2498 said:**
> can you get the light to come on for the cam
i do not see it in the lsusb

i dont think there is a light for the webcam, and nothing happens when i push (fn) + F9 witch is the on button for the webcam..

The laptop comes original with windows 7 64bit and there it works fine

---

### Post by Lateralis on 2011-06-05
Try typing lsusb into the command line twice: once before and once after you hit fn+F9 to turn on/off the webcam.  I *think* lsusb only picks up the integrated webcam on my laptop once I have turned it on using the hot keys.  If that is the case, you will see an entry in lsusb appear/disappear as you turn on/off the webcam.  If that makes sense?  

So: 

1) enter lsusb into the command line
2) hit fn+F9
3) enter lsusb into the command line again. 

Do you notice any differences in the outputs for 1) and 3)?

---

### Post by gordintoronto on 2011-06-05
I think the Sunplus device is a mouse? All the others are obviously not your webcam. So, by default, your webcam is turned off. This is fairly normal with laptops, since turning off the webcam saves a little bit of electricity.

---

### Post by no2498 on 2011-06-06
i have seen that linux/ubuntu has changed some of the keys around
you may need to reset yours

---

