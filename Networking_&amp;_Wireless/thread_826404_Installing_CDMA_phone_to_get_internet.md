---
title: "Installing CDMA phone to get internet"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by hemajith on 2008-06-11
I am trying to install a CDMA telephone via USB cable to setup a dial up connection. When I plug the cable in and list USB devices (lsusb), the cable is listed as 'TUSB3410 Texas Instruments Huwawei FWT wirelss modem'. The Driver CD does not contain any Linux drivers. How do I set up this modem and connection from there?

---

### Post by molotov00 on 2008-06-11
The package ndiswrapper is a 'wrapper' for Windows drivers. Read into it a bit, but basically it takes the drivers off the CD you have. I believe there are three files it needs.

You need ndiswrapper and now there is a GUI to install drivers:

First, there's a step that involves blacklisting the existing drivers that Ubuntu might be trying to use. I forget the exact code :S

Then...

sudo apt-get install ndiswrapper-common ndisgtk
sudo ndisgtk

Then give ndisgtk the drivers it needs from the CD.

---

### Post by lswb on 2008-06-11
The ndis wrappers were designed for wifi drivers. A cell phone will usually be recognized by linux as a serial port and a connection can be established with ppp. Plugging in the cell phone should automatically load the modules you need, usually a device named /dev/ttyACM0 will be created. To confirm the correct device, plug in the phone and in a terminal, type the command "dmesg"

Near the end of the output of dmesg you should see something like 
  cdc-acm blah-blah-blah ttyACM0 usb device blah-blah-blah

Now, in a terminal type the command "pppconfig" (If you get a message like pppconfig not found, install it from synaptic)

You will be prompted for the information to set up a ppp connection. When it asks for the device enter /dev/ttyACM0 or whatever you saw from dmesg. You will also need to enter a phone number, username, password, etc. For most usa cell phone networks, the phone number is #777 (or #ppp, "Point to Point Protocol") For verizon the username will be [email]xxxxxxxxxx@vzw3g.com[/email], where the x characters are replaced with your telephone number. If you happen to be using Verizon, post back and I can help with the settings, if you use some other company, you can probably google the correct settings by entering search terms like "tethered cell modem cdma YourCompanyName" or similar.

Once you've entered all the connection settings and given the connection a name, select the save/write files option from the pppconfig program and exit. Then you start the connection by typing "pon your-connection-name" in a terminal or in the Alt-F2 window, There is also a Gnome-ppp panel applet, I'm not personally familiar with using it, but I know it gives you a panel icon and I believe it can be used to configure the connection also.

---

### Post by knowsath on 2008-06-25
Hi,Im new to ubuntu and this forum.Ihave the same problem.
"TUSB3410 Texas Instruments Huwawei FWT wirelss modem" not working with ubuntu-8.04.
when i type command "dmesg" it shows 
"[ 6710.498665] usb 1-2: USB disconnect, address 5
[ 6713.365033] usb 1-2: new full speed USB device using uhci_hcd and address 6
[ 6713.558210] usb 1-2: configuration #1 chosen from 1 choice
[ 6713.563605] ti_usb_3410_5052: probe of 1-2:1.0 failed with error -5"
like that,
can anybody help me to get cofigure my modem,please.thanks

---

### Post by hemajith on 2008-07-03
I have downloaded a .tar of ndiswrapper. How do I install it in the computer? I can't use apt-get as it doe not have an internet connection. I'm trying to set it up!

---

