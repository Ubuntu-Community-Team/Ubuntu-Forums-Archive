---
title: "Instructions needed on Instructions"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by obelixtaiwan on 2010-09-28
HI All

I fairly new to Ubuntu, but have been wanting to run the linux experience for a long time, so I finally made the switch, but i need some help. I have a USB mobile 3g modem, Which come with instructions on how to make it work in Linux, But I dont understand the instructions. Please see below for instructions.
Any help will be appreciated. 

**_Instructions_**
1. For Linux, open a terminal and make sure you have the tools you will need:
sudo apt-get install libusb-dev wget build-essential
2. Get the source code EP0_Switch_Utility.cpp for the program switch
3. Compile it:
g++ EP0_Switch_Utility.cpp -lusb -o switch
4. Copy the binary into your path:
sudo cp switch /sbin/
5. Create a udev rule that makes sure that switch is run every time the modem
is plugged in. First create the file:
sudo gedit /etc/udev/rules.d/50-h21.rules
Then cut and paste this line into the file and save it:
SUBSYSTEM=="usb", SYSFS{idProduct}=="F000",
SYSFS{idVendor}=="1DA5", RUN+="/sbin/switch"
6.Run
ls /dev/ttyUSB*
If you see three devices
/dev/ttyUSB0 /dev/ttyUSB1 /dev/ttyUSB2
It means the modem is communicating properly with your computer
7. Open another terminal and probe the device by using the below command&#65306;
modprobe usbserial product=0x4512 vendor=0x1DA5 maxSize=2048
8. Establish a link to the node for later use.&#65306;
ln -s -f /dev/usb/ttyUSB /dev/modem
9. Add(Modify) /etc/modprobe.conf&#65306;
options usbserial vendor=0x1da5 product=0x4512
10. Please making sure usbserial is in the /etc/modules.

---

### Post by 3rdalbum on 2010-09-28
Go to the Network Manager applet on your top panel. Right-click it. Choose Edit Connections...

Now go to the Mobile Broadband tab and click on the Add button. It should ask you for some basic information and then your device should work.

If/when you have done this, if your device still doesn't work, then post back here.

---

### Post by obelixtaiwan on 2010-09-30
Hi 

I tried the mobile broadband tab, but it doesn't see the device to read form. 

Anybody has any other ideas please. I need to get this working as soon as possible

---

### Post by nothingspecial on 2010-09-30
Those are rubbish instructions. Open a terminal, copy and paste the code into it. 3 times you open a text edit, with the command gksudo gedit.
The lines immediately after each of those are to go in the text editor, not the terminal. Don`t forget to click save before you close it.





**_Instructions_**
1. For Linux, open a terminal and make sure you have the tools you will need:
```
sudo apt-get install libusb-dev wget build-essential
```2. Get the source code EP0_Switch_Utility.cpp for the program switch
3. Compile it:
```
g++ EP0_Switch_Utility.cpp -lusb -o switch
```4. Copy the binary into your path:
```
sudo cp switch /sbin/
```5. Create a udev rule that makes sure that switch is run every time the modem
is plugged in. First create the file:
```
gksudo gedit /etc/udev/rules.d/50-h21.rules
```Then cut and paste this line into the file and save it:
```
SUBSYSTEM=="usb", SYSFS{idProduct}=="F000",
SYSFS{idVendor}=="1DA5", RUN+="/sbin/switch"
```6.Run
```
ls /dev/ttyUSB*
```If you see three devices
/dev/ttyUSB0 /dev/ttyUSB1 /dev/ttyUSB2
It means the modem is communicating properly with your computer
7. Open another terminal and probe the device by using the below command&#65306;
```
modprobe usbserial product=0x4512 vendor=0x1DA5 maxSize=2048
```8. Establish a link to the node for later use.&#65306;
```
ln -s -f /dev/usb/ttyUSB /dev/modem
```9. Add(Modify) /etc/modprobe.conf&#65306;
```
gksudo gedit /etc/modprobe.conf
``````
options usbserial vendor=0x1da5 product=0x4512
```10. Please making sure usbserial is in the /etc/modules.
```
less /etc/modules
```If it`s not in there
```
gksudo gedit /etc/modules
``````
usbserial
```

---

