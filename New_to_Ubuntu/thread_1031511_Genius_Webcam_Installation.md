---
title: "Genius Webcam Installation"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by cosimix72 on 2009-01-05
Hi All
I am a very absolute beginner, I have just installed Xubuntu on an old computer and I am absolutely thrilled about it... BUT I would like to install an old Genius Look 110 webcam I have to use with skype and I do not know how to do that... 

This morning I have downloaded the driver for Linux but now I don't know how to install it, it mentions I have to write something in the kernel, I am completely lost... 

and when I say I don't know imagine I have never seen Linux and his derivates before...

Can someone of you give me a step by step procedures?

Thanks in advance and really Xubuntu is a great OS....

---

### Post by halitech on 2009-01-05
what type of connection is on the webcam? if it is a usb connection, open a terminal and type```
lsusb
```
then plug the webcam in, wait a minute and run the same command. post the output here so we can help.

---

### Post by cosimix72 on 2009-01-05
Yea, it has an USB connection...

when you say, "open a terminal"... what do you mean exactly? 

I'm sorry, I really need the ABC with Xubuntu... so far I had only plug and pRay with Windows... now I want to drop the pray part...

Thanks

---

### Post by halitech on 2009-01-05
I'm using Debian with XFCE which is a little different then Xubuntu but I believe if you right click on the desktop you should get a popup menu with terminal listed there. If not, in the upper right, click on your menu there and select either terminal or accessories - terminal

---

### Post by cosimix72 on 2009-01-06
I have opened the terminal with lsusb and this is what I got

cosimix@cosimix-laptop:/$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cosimix@cosimix-laptop:/$ lsusb
Bus 002 Device 004: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cosimix@cosimix-laptop:/$ 


and now.... :-))

---

### Post by halitech on 2009-01-06
the good thing is the cam is being seen

[color="red"]Bus 002 Device 004: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam[/color]

have you tried running cheese to see if it works?

---

### Post by cosimix72 on 2009-01-06
It attivates but the imagine is incosistent, coloros and lines but nothing shaped....

this is what I got from Genius... but I do not know how to use it...

# Load the needed modules for the zc301 driver.
#

# you may need these commented out lines if your insmod is too old.
#IS24=`uname -r | grep -c ^2.2`
#
#if [ $IS24 == "1" ]
#then
#insmod /lib/modules/2.2.14/misc/videodev.o
#else
#insmod /lib/modules/2.4.0-test10/kernel/drivers/media/video/videodev.o
#fi

#
# Load the modules.
#

# Video4Linux Support
/sbin/insmod videodev

# USB Core Module
/sbin/insmod usbcore

# USB UHCI/OHCI Controller Modules (new)
/sbin/insmod usb-ehci
#/sbin/insmod usb-ohci

# USB UHCI Controller Modules (old)
#/sbin/insmod uhci

# that for the sys request key, comment it out if the quickcam works well.
# if you get any erors: use Alt + SysRq + S = Emergency Sync (write everything on HDD)
#		        use Alt + SysRq + U = Unmount all HDD's
#			use Alt + SysRq + B = Reboot system immediatly
#echo "1" > /proc/sys/kernel/sysrq

# zc301.o is in current directory, after copying in /lib/modules/.../usb,
# use insmod zc305.
/sbin/insmod ./usbvm305.ko

/sbin/lsmod

---

### Post by cosimix72 on 2009-01-07
I have installed and ran Cheese and it worked, the image is a little blurred but accepatble, the problem is that skype does not work, it attivates the webcam but the image is only colored bars ....

---

### Post by halitech on 2009-01-07
if it works in cheese then we know the camera is working (albeit blurrily) so I think we are looking more at a skype configuration thing which I don't know much about.

---

### Post by cosimix72 on 2009-01-08
First of all many thanks Halitech,

I had a look at the setting in Skype but nothing helpulf popped out ... anyone knows how to set this webcam to make it work with Skype??

Thanks in advance....

---

### Post by cosimix72 on 2009-01-08
First of all many thanks Halitech,

I had a look at the setting in Skype but nothing helpful popped out ... anyone knows how to set this webcam to make it work with Skype??

Thanks in advance....

---

### Post by cosimix72 on 2009-01-08
First of all many thanks Halitech,

I had a look at the setting in Skype but nothing helpful popped out ... anyone knows how to set this webcam to make it work with Skype??

Thanks in advance....

---

### Post by cosimix72 on 2009-01-11
Anyone?

---

