---
title: "GPRS modem connection?"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by steven43126 on 2006-08-29
Hi,
Anyone got a GPRS modem working with ubuntu? I have the motorola L7 mobile phone whiich connects via usb cable if anyone has any configs they could post it would be greatly appricieated! Alternativley as i just need a connection while im in spain (man i love remote working) Is there a site that lists free WAP's in spain ?

Many thanks steve.

---

### Post by Uncle Che on 2006-09-01
I am using an L6 with complete success using this way I outlined in this thread:
[http://www.ubuntuforums.org/showthread.php?t=211322&highlight=motorola+gprs](http://www.ubuntuforums.org/showthread.php?t=211322&highlight=motorola+gprs)

You may have to set APN or something but I am in Thailand and haven't had to worry about it. I have used it with two different providers here. 

1. Plug in the motorola phone. It should be recognized as ttyACM0.

2. Open a terminal window and type:
sudo wvdialconfig /etc/wvdial.conf

You get a long list of checks that it runs. Basically it checks for a modem and the location.

3. next type:
sudo vi /etc/wvdial.conf

In the file, you need to edit a few entries, like edit out the semicolons at the start of the line for phone number, password and username. For user name and password, you can enter anything for those values. For phone number, I used *99#.

Next, add a line:
Stupid Mode = 1

You might want to change the baud rate, I used 230400 even though it detected that it could do 460800. GPRS is slow so I can't personally think of a good reason to send data to and from the modem 10 times faster than it can deal with it.

4. Save the file.

5. Next open another terminal window and type
sudo wvdial

You are now connected to the internet and you can surf. I don't know if you can close the window and keep the connection or not. I am just happy to be connected. I can deal with any quirks.

I hope this can serve as a little bit of help to any searching the forums for how to use a gprs modem with Ubuntu/Kubuntu. It seems really simple, but I have been searching on and off for 6 months for a way to connect through Ubuntu like this.

---

