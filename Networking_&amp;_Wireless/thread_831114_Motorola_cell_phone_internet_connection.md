---
title: "Motorola cell phone internet connection"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by Arutha on 2008-06-16
I have a Motorola V3xx and in Windows I use the Motorola Phone Tools to connect to the Internet with it. It is a UMTS connection, using drei.at as APN.

Connecting the phone via bluetooth to the PC is no problem in Hardy Heron. But how do I use the phone as a modem?



I have used the following Dialog: System > Administration > Network;
there I have 3 entries: Wireless, Wired and Point to Point Connection.

I edit the Point the Point Connection entry, and I choose GPRS/UMTS and I use "drei.at" as the APN. On the next tab ("Modem"), I need to choose the modem port and the dial type.
I think it is here where I do something wrong. I have 5 options for modem port: /dev/modem and /dev/ttyS0 thru /dev/ttyS3.
None of them seems to work. How do I tell Ubuntu that it should use Bluetooth to connect to my cellphone modem?

---

### Post by lswb on 2008-06-16
Try plugging the phone in and from a terminal, type the command "dmesg" 

Near the end of the output from dmesg you should see something like:

   blah blah blah New USB device blah blah blah ttyACM0

the ttyACM0 part is the device.

In the modem port entry dialog, enter /dev/ttyACM0 (or whatever you read from dmesg)
Generally the phone number will be #777, username and password vary with ISP but with verizon for instance the username will be [email]xxxxxxxxxx@vzw3g.com[/email] where the x characters are replaced with the telephone number and IIRC there is no password (it will only allow a connection if the username phone number actually matches the phone being used) If you google for something like "cell modem YourProviderName linux ppp" you can probably find the details you need.

I recommend that you NOT use NetworkManager to make this ppp connection, however it may work for you. Even if NM DOES connect you will find that when running firefox, evolution, and some other appls that they will start in offline mode. There is a program called gnome-ppp that lets you configure and connect, and will give you a panel icon. Post again if you need more info on actually setting up the connection.

---

### Post by dishguy123 on 2008-06-19
I am trying to do something very similar.  I have a sony vaio VGN-T370P laptop & a Moto Q phone (former Cingular, now AT&T).  I'm using GNOME PPP, but it says can't find modem, no matter what settings I choose.  Any help from anyone would be appreciated...

---

### Post by lswb on 2008-06-19
Are you connecting with a USB cable or with bluetooth?

---

### Post by dishguy123 on 2008-07-03
I'd like to SIMPLY connect!  Either USB or BLUETOOTH way. I've tried both, but for some odd reason, just can not connect.  Any/all your help will be appreciated.

---

