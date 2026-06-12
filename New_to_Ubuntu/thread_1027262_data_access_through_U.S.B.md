---
title: "data access through U.S.B"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by nevinalex1234 on 2009-01-01
I am currently building an application where i collect data from the U.S.B and use the data to form a GUI application.Can anybody help me on how to access the data and from where??The data that is being sent over the U.S.B is temperature of the surroundings...How can i access it??

---

### Post by ken22 on 2009-01-01
Do you have a usb thermometer to collect the data?

You'll need to code something yourself to do this.

---

### Post by nevinalex1234 on 2009-01-01
Since i am quite new to LINUX and UBUNTU..i have very limited knowledge on This...


The actual idea is to collect medical data from a variety of devices namely EKG meter,Pulse OXimeter,Temperature of the body..etc and to send these data through a PIC(microcontroller) in U.S.B format to the LINUX MACHINE..but i dont know where the data from U.S.B is getting stored...how can i access 'that' data ????? so that i can manipulate it for the final output..

---

### Post by ken22 on 2009-01-01
If your usb device is supported under Linux and installed correctly, there should be a file in the /dev directory for it.

In the case of getting information from a mouse invoking the "cat" command is how you would print data to the shell from the mouse. The command would be ```
cat /dev/input/mouse
```

---

### Post by anewguy on 2009-01-01
Chances are you'll need to look into using the libusb calls.  For the GUI there are many things available, but I think you'll find the libusb calls easiest from C or C++ in which case I would use GTK for the GUI.

The libusb development package is in synaptic.  Libusb itself is by default installed, but not the development package.  I think the documentation is there as well - if not, it is available on the web.

Dave :)

---

### Post by nevinalex1234 on 2009-01-01
Does Python 2.5 have libusb & GTK ??

---

### Post by Rhubarb on 2009-01-01
You USB device may present itself as serial USB.
In this case it'll appear as /dev/ttyUSB0
You can grab a nice app to send / receive commands to serial devices:
```
sudo aptitude install gtkterm
```

If you want to see if Ubuntu has detected your usb device, in a terminal, run this:
```
lsusb
```
Or you can have a look in the system log:  System --> Administrator --> System Log
Scroll right down the bottom, then plug in your USB device, it should say what it's found.

Once you've identified if the device is recognized, and how it's recognized, then you can start working out how to talk with it.

I'm not a programmer myself, but I am familiar with communicating with serial, serial over usb, and serial over bluetooth.
Many simple USB devices like data loggers, GPS receivers, and 3G wireless broadband modems all use simple serial ports that are easy to connect to.

Hope this helps you - Rhubarb

---

### Post by nevinalex1234 on 2009-01-01
What is the command that i have to enter in the Terminal so that i can select the current directory as /dev ????

---

### Post by Delever on 2009-01-01
> **nevinalex1234 said:**
> What is the command that i have to enter in the Terminal so that i can select the current directory as /dev ????

cd /dev

---

### Post by nevinalex1234 on 2009-01-01
cat /dev/input/mouse
This command which you gave doesnt seem working ...
i found the folder dev and also the subfolder input but dint find mouse..... there are folders like mouse0,mouse1,mouse2,mice....etc inside it...What shud i do ??

How ca i use the cat command now since it is showing error ??

---

### Post by ken22 on 2009-01-01
I actually think Rhubarb's approach is best suited to this now.

Python has [PyUSB]("http://pyusb.berlios.de/") which is built on top of libusb. Python also has pygtk, which is gtk for python.

---

