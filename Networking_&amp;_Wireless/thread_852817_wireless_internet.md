---
title: "wireless internet"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by spur on 2008-07-08
Has any one any experience with a usb modem and/or bigpond broadband?
I'm not talking a LAN or private network but an Internet connection. I have a good IInet connection for my desktop and want a portable one for my laptop so thought a wireless one would do the job nicely, then I find Bigpond are the only supplier for my area :confused:. 
I'm hoping it will work ok, so does any one have any experience with this?
:lolflag:

---

### Post by david0075 on 2008-08-13
i dont know if you got your answer, but i cant get mine to work either. i tried in the beginners forum, but no response. but ill tell you as far as i have gotten.

the first part is adding the device to a file. not sure how it works or why. but you need to type something like this in your terminal:

sudo insmod /lib/modules/2.6.24-16-generic/kernel/drivers/usb/serial/usbserial.ko vendor=0X16d8 product=0X6280

the instructions i read said to use a slightly different path, and filename, but go into nautilus (your file browser) and look though /lib/modules/ and look for 'usb-serial.ko' file, there werent a lot of files for me to look though. when you find it use that path. if you get it wrong, itll say file not found

oh, the vendor=**** product=****** could be different too. im using a blue modem made for home use. you should check this first. type "lsusb" into your terminal. this is what i got:

Bus 003 Device 002: ID 054c:0069 Sony Corp. memorystick MSC-U03 reader
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 16d8:62800
Bus 001 Device 001: ID ID0000:0000

there was only one real choice for me to use here.

then you need to run the setup program, type "PPPconfig" into your terminal. these are the settings i used


number *99#     -->  i read that this is the number to use
ISPLogin ogin:  --> this was the recommended setting, not sure why
User [email]myusername@bigpond.com[/email]    -->replace with your email address
ISPPrompt ssword:     -->   recommended setting again
password: *******     --> replace with your account password
com:  /dev/ttyUSB1   --> The "USB" must be capitals. i have tried USB0 and USB2, both come up with 'in file /ect/ppp/peers/bigpond: unrecognized option '/dev/ttyUSB1'


i used 'bigpond' as the connection name. to start the process, you use

pon bigpond   --> to connect
poff bigpond  --> to disconnect.

and thats as far as i got. i still cant get it to work

i heard a bit about dmesg and dont understand why i need it, but heres some stuff from my file, 

dmesg shows tons of stuff, some stuff that i think is important is:

usb 1-1:new full speed usb device using uhci_hcd and address 2
usb 1-1: configuration #1 chosen from 1 choice
/build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: usb serial support registered for generic
usbserial_generic 1-1:1.0 generic converter detected
usb 1-1:generic converter now attached to ttyUSB0
usbserial_generic 1-1:1.1 generic converter detected
usb 1-1:generic converter now attached to ttyUSB1
usbserial_generic 1-1:1.2 generic converter detected
usb 1-1:generic converter now attached to ttyUSB2
usbcore: registered new interface driver usbserial_generic
/build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: usb serial driver core




i have no idea where to go from here, and its really annoying not being able to connect to the net unless i boot windows.

---

### Post by spur on 2008-08-13
Thanks for your response. I ran out of time to configure it and put xp back on the laptop. I use it only rarely as my main computer is my Ubuntu one and I have an ADSL2 wired connection working well on that. Eventually when I have more time to figure it out I will get the wireless laptop back to Ubuntu too.
I have the same blue home modem you have I think.Its a Sierra wireless AirCard 880u.

---

### Post by david0075 on 2008-08-14
thanks, ill try a few searches targeting the modem

---

### Post by spur on 2008-09-17
Did you find anything more David?

---

