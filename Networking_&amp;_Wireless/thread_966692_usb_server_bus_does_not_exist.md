---
title: "usb server bus does not exist"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by gazzatav on 2008-11-01
I have a small usb to ethernet adapter which allows me to connect an external usb drive over my LAN.  I have installed the windows software for it using WINE and it appears to work fine.  When I run the software (Rally Solutions USB Server) I can see the drive as available in the Rally usb server window but when I try to connect it I get the error 'USB server bus does not exist'.  Any suggestions welcome.

---

### Post by gazzatav on 2008-11-08
OK so no suggestions.  Can anyone give me an idea where I can find out about this.  When I search I keep ending up with info about how to share a usb drive over the lan from another computer.  This is a way of making an external usb drive into NAS.

---

### Post by Springers on 2008-11-10
HI Gazzatav
I have the same problem and i unfortunately have no solution either.  I will keep looking and will let you know if i find anything and if you could do the same it would be very much appreciated as i'm getting very p****d off with the whole thing!

Cheers
Springers

---

### Post by Springers on 2008-11-10
Hi again.

Fixed it!!!!!!!:):):):):):)

Go into Device Manager and search for devices that have no drivers installed.  You should find one called EST_SERVER and it will have no driver.  You then need to manually install a driver for this device from the rally directory on the c: drive within the programs folder.  It will find the necessary driver file, install it and Bob is now your uncle!!!!!  You can then connect to your drive etc.

Hope this helps

Springers

---

### Post by gazzatav on 2008-11-11
Thanks for you responses Springers, I was starting to feel lonely there!  I still can't get mine to work.  Are you talking about device manager in Windows or the hal device manager?  How did you manually install the driver?  I have found the driver used by Winxp - GenHC.sys and I've copied it to the WINE windows driver folder with no luck.

---

### Post by Skechy on 2008-11-13
I have the same product running on a windows nework. It has software that comes with it that allows only one PC to link to it at a time...which is pretty useless. I would like to know if I could use it as a shared drive with NAS/samba.  It claims it is a NAS server, but I hardly see the point if only 1 person at a time can connect!

Cheers

Skechy

---

### Post by gazzatav on 2008-11-13
hi Skechy,

yes it's not a fully fledged server but it imitates the action of plugging in the device to any PC on the network and you can't have a usb device plugged into two computers at a time as far as I know.  It's not bad for giving access to external drives across the network as long as everyone behaves and disconnects when they are finished.  OK at home but not practical for a business environment.  They are cheap though!

---

### Post by Springers on 2008-11-14
Hi Gazzatav it was nice to find someone in the same misery as i was in!!!!

I found the drivers in the Rally directory and installed them through device manager by manually selecting the directory. 

I purchased mine to act as a media server for my PS3 as stated on the sales blurb but it certainly isn't made by Ronseal!  It's a shame that you have to have the PC on for it to work with my PS3 as i might as well just have the HD directly connected to my PC as before and spent the money on beer!!

What you can do is have it connected twice - via the sw and also  as a network drive so it will work with my PS3 with my PC on and also as a networked drive so my PC doesn't have to be on.

Hope this helps.

Springers

---

### Post by gazzatav on 2008-11-17
Hi Springers

I'm guessing you're using this with Windows

I've managed to get in touch with someone at EST who says he will email me the latest driver which has just been WHQL certified.  Maybe it will behave better under WINE as well.

---

### Post by gazzatav on 2008-11-22
I'm sure someone out there can direct me to information on how to get this application to use the driver GenHC.sys or where to place it.  I've tried the obvious places like the WINE 'C' drive and system folders and I'm sure there must be a way of getting Ubuntu to use the driver.

Any offers please.

---

### Post by gazzatav on 2008-11-26
Re: usb server bus does not exist
I'm sure someone out there can direct me to information on how to get this application to use the driver GenHC.sys or where to place it. I've tried the obvious places like the WINE 'C' drive and system folders and I'm sure there must be a way of getting Ubuntu to use the driver.

Any offers please.

---

### Post by gazzatav on 2009-01-03
So is there any way of creating a USB Server bus?  I guess there must be but I've got to ask something!

---

### Post by jean47 on 2009-02-13
Hey 
I have the same problem "usb server bus do not exist" when I try to use my Icy Box ib-lan104 with ubuntu 8.04 and 8.10.
Did you find a solution to this problem ?

---

### Post by jean47 on 2009-02-15
Has anyone a solution to fix this problem ?

or an explanation about the USB server bus ?

thanks for your help !

---

### Post by gazzatav on 2009-02-16
No I never got a hint of an answer to this problem.  The Ubuntu forums are so big that new messages disappear off the screen within minutes!  I got in touch with the company that makes the chip and John Tung there was interested in writing a driver for linux.  I got in touch with Greg Kroah at the open driver organisation and he was interested in writing a driver.  I guess the rest is just inertia.

---

### Post by gazzatav on 2009-03-04
Good news.  A Linux driver is being produced.

---

### Post by jean47 on 2009-03-05
I am still hoping a solution : this is a very good new !
:P

---

### Post by jean47 on 2009-05-20
Anything new about the linux driver ?

---

### Post by maidasette on 2009-10-06
Have you try to install the program USB server in client mode?
[http://incentivespro.com/usb-server.html](http://incentivespro.com/usb-server.html)

---

### Post by gazzatav on 2009-11-14
Thanks for the suggestion maidasette but from what I can see that needs the usb device to be plugged into another computer on the network.  The other computer has to be on.
What we have here is a small network device that sits on the LAN with a USB device plugged in allowing the device to be accessed from any machine on the network.  It works fine in Windows but there is a problem getting the USB bus to function under WINE.

---

### Post by gazzatav on 2009-11-14
The guy at EST said the third quarter of this year but that was just before the banks turned the world upside down!  I've done some searching for the driver but couldn't find anything.  Personally I doubt if it's going to happen and I'm looking at buying a Linux compatible USB NAS server.  I saw one recently (500GB) for about £100.

---

### Post by mande01 on 2011-02-08
Anybody with any more information?
I pointed zenmap at it and it thinks that it has Minix 3 installed on it.

Does anyone know how to take advantage of this information and get into it?

I'm a real beginner here, but would love to figure a way into this little thing.

Der

---

