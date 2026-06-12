---
title: "Accessing the usb device status info"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by nevinalex1234 on 2009-01-03
I want to get access to the status and the information of the optical mouse i have connected....I am studying this method to get USB data later....


i typed the following in the terminal

tec@tec-laptop:/dev/input$ ls
by-id    event0  event10  event3  event5  event7  event9  mouse0  mouse2
by-path  event1  event2   event4  event6  event8  mice    mouse1
tec@tec-laptop:/dev/input$ sudo vi mouse1

1)but it seems mouse1 is not a file.....infact i cant open any of them ...i tried the CAT command also but it is getting stuck.......??

2) what are the other "mouse" ?? i have connected only 1 usb device the optical mouse and a usb modem..what are the rest?? what do they stand for ??
are they standard system files???
how do i know which is the file concerning the optical mouse ???

3)When i browsed through window ....i got the details of the input...

the event is of the type - character device
the mouse is of the type - character device 

How do i access the information ??? it shows 0 bytes in the properties..

I would be really gratedfull if somebody could help me out on this 

Thanking You:(

---

### Post by nevinalex1234 on 2009-01-03
PLS help me !!!

---

### Post by nevinalex1234 on 2009-01-04
nobody replied ???

---

### Post by namdung on 2009-01-04
```
lsusb
```

---

### Post by MenZa on 2009-01-04
It depends what you mean by "USB data" - if you want to know what USB devices are connected, type the following in a terminal:

```
lsusb
```

---

### Post by anewguy on 2009-01-04
You may need to open them as serial devices, but libusb is going to be the way to really read that information.  The runtime for libusb is installed by default, but you need to install the development package and the docs, then read the docs.  You will also need to know some of the technical specifications for your devices or it will be useless.

Dave :)

---

### Post by nevinalex1234 on 2009-01-04
3)When i browsed through window ....i got the details of the input...

the event is of the type - character device
the mouse is of the type - character device

what is this character device ???

i tried to print the data in the event and the mouse on  terminal using sudo cat .... but it dint respond why ???

The lsbusb gives details of what all devices are connected...i got that working fine....

But what i really want to extract ( " DATA") is the information.....
for example ....
if an application connected from external world with USB interface (configured as MASS STORAGE device) to the Ubuntu.....how can i extract the data that is coming peridically......

Just like in WINDOWS OS where we can extract data coming from RS-232 through serial port monitor/hyperterminal how do we do USB port monitoring in LINUX ???

and how to link this incoming data to a python program so that i can use it for GUI later ???
 
i checked that the files that get added in /dev/input are the event & kybd/mouse (AS IN MY FIRST QUERY ABOVE) in case of plugging a keyboard optical mouse 

what is this event ???

If my assumption is correct ...the data from the mouse and the keyboard are being stored here first and then they are being manipulated by the LINUX ...am i right ?????

PLS DO REPLY...

### 
thanks for replying earlier...i had almost given up hope..since nobody turned up

---

### Post by nevinalex1234 on 2009-01-04
this is the screen shot

---

### Post by nevinalex1234 on 2009-01-04
hullo ?? can anyone hear me..... 
PLSSSSSSSSSSSSSSSSSSSSSSSSS help

---

### Post by nevinalex1234 on 2009-01-04
hullloooooo [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

### Post by anewguy on 2009-01-04
As i mentioned in my first post, there are a couple of things you are going to need:

(1) libusb [not lsusb] development packages and docs installed

(2) the technical specs on your USB device(s)

you will need these if you want to communicate with your device.

In addition, there is a usb trace function you can toggle on/off in the kernel (at least it used to be there) to see the traffic that actually goes across the USB controllers.

Dave :)

---

### Post by dunkar70 on 2009-01-04
Perhaps there is a better way to word your question. Are you looking for information that describes the mouse you have connected (such as model, port, etc.) or are you trying to capture the data that your mouse is sending to your PC?

What is your intention for the data? Are you writing a program that does something with the data your mouse is sending?

---

### Post by anewguy on 2009-01-04
And, if you are planning on capturing and using the data from a USB device, this is where libusb comes in.  It is the programmatic calls to talk to USB devices.  Most USB devices communicate differently than what you might be used to.  Libusb provides the framework for that communication.  You also need to know the tech specs for the device (endpoints, what commands of what length does it recognize, how does it respond, etc.).

Dave :)

---

### Post by nevinalex1234 on 2009-01-05
> **dunkar70 said:**
> Perhaps there is a better way to word your question. Are you looking for information that describes the mouse you have connected (such as model, port, etc.) or are you trying to capture the data that your mouse is sending to your PC?

What is your intention for the data? Are you writing a program that does something with the data your mouse is sending?


Yes dunkar thats rite..... i want to write a program that does something with the data that mouse is sending....i know that the files will be created in the dev/input dir....but i dont know how to use them..nor can i open them...they are the so called event and mouse..OF TYPE :character device (i had told earlier)


CAN ANYONE give weblinks that can aid in this process of data acquisition, OR how to use libusb effectively in a python program ..i have absolutely no idea on LINUX...im just 2 weeks old...

Why isnt the cat command not working for dispalaying the files "event" and "mouse" ????

---

### Post by anewguy on 2009-01-05
Here's the rub - you need to know what to expect the mouse to send - hence the need for the technical docs.  If using libusb, you build up commands that basically do things as such:

find the busses
find the device on the bus
open the device
via endpoints, send commands (via a write) to ask for data
via endpoints, read data
close the device
release the device

There is technical documentation available on the web for using libusb.  It will require a technical knowledge of the device you want to work with.  The syntax for using libusb in Python should also be available on the net.

It's possible you may be able to read the device as some sort of serial device, but again, without the technical documentation for the device, the data will be useless.

Dave

---

### Post by anewguy on 2009-01-05
You should also try doing a Yahoo! or google search using linux read mouse data as the search string.  Lots of things are returned, including this link:

[http://http://www.linux-mag.com/id/330]("http://http://www.linux-mag.com/id/330")

while the titles of things such as the link above may not appear to be of interest to you, they provide the fundamentals for just talking to your mouse.  You still need to know what data to expect.

If you are not familiar with such things, you will want to take quite a bit of time and read through those things returned on a search as per above.  It seems like it should be easy I'm sure, but easy is a relative term when it comes to hardware.

You could also check to see if there are any technical documents available for the mouse driver you are using to see if there are ways to hook into it.

Dave :)

---

### Post by linux6994 on 2009-01-05
Perhaps use tail or tailf for the particular device.  man -k tail
tail is used for looking at the bottom of a file. I have not tried it, just a thought.

usb devices look like they are in  /dev/bus/usb

---

### Post by nevinalex1234 on 2009-01-10
bad luck buddies....failed miserably yet again....

IM DOOMED

---

