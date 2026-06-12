---
title: "need help with internet access"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by iwant2learn on 2009-03-28
I have an Ubuntu 8.04 dvd which was included in a book I bought about Ubuntu.  I wanted to test drive Ubuntu and see how I like it before installing it so I ran it from the dvd drive (booted from dvd drive).  It seemed to work, although it was slow, as expected running from the dvd drive, except for internet access.  I have followed the instructions given to me: 

system -> admin -> network
select connection
then click properties
then click enable this connection
set configuration to dhcp
click ok

However, there is no "enable this connection" option that I can find and on the screen where that option supposedly is present, there is no data displayed at all.

I am using Comcast cable, with the cat V cable going directly from the Comcast modem to my computer.  I have tried it on a Windows XP and a Windows Vista computer with the same result.

Thanks in advance,

---

### Post by 123456789123456789123456 on 2009-03-28
If, I am reading this correctly, you are connected using a regular ethernet cat5 cable?

at the top of the screen, there is a symbal of 2 computer screens, simular to that on vista, xp.  this signifies that it is a network connection.  If Ubuntu understands and reconizes your ethernet card,(NIC) and has been able to load the correct drivers, you should be on internet.  I have never had to go through all of those settings to get connected using ubuntu.  If you are not connected it means that your NIC(Network Interface Card) is not known, or is not compatable with Ubuntu.  going through system, and listing hardware could give more information if the card is understood.  I know that I have a wireless usb NIC, Ubuntu 8.04 did not know how to use the device, but 8.10 does.

The only other option, if the card is not reconized on how to be used, use ndiswrapper program, which I think may be included with 8.04 to install the windows driver for the ethernet card.  Or search for a sutable driver for Ubuntu for that device.  you can use the driver, after you install ubuntu on the hard disk.  Use either wubi, or dual boot to see if you can get it to work that way.

Without knowing more about the hardware situation, and the information Ubuntu 8.04 is giving about the hardware, I can not be sure what the spacific problem is.

---

### Post by iwant2learn on 2009-03-28
[QUOTE=123456789123456789123456;6975237]If, I am reading this correctly, you are connected using a regular ethernet cat5 cable?

yes

at the top of the screen, there is a symbal of 2 computer screens, simular to that on vista, xp.  this signifies that it is a network connection.  

They are there.

If Ubuntu understands and reconizes your ethernet card,(NIC) and has been able to load the correct drivers, you should be on internet.  

I'm not, though.

I'll work on your other information tomorrow.  Thanks!

---

