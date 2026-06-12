---
title: "WG111 help!!!!!!!!"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by ir0n_ma1den on 2007-02-15
hi everybody, i just installed Ubuntu 6.10 on my old computer without a problem. Now I come to problem with my internet connection. I assumed that, just like windows, I could just pop in the install cd for my wireless usb thingy and the driver would install. First, the autorun menu didnt pop up. I then double-clicked on the little cd icon and tryed to run the autorun from there. I gave me an error message that said it could not read it. I dont know what to do now!! 
I put the dongle into the usb and it does recognize it when i go to systems->networking, and when i type in iwconfig in terminal. I really need help because i would like to install this on my current computer, but if i cant get the internet to work then i definetly wont install it.
:confused: :confused: :confused: :( :( :confused: :confused: :confused:

---

### Post by Floppyjoe on 2007-02-15
You will not be able to run a windows autorun program on Ubuntu. At least not the way you want to. Installing the drivers works differently on Linux. If your wireless device doesn't have drivers built in with Linux you will need to install them another way, possibly with ndiswrapper. You will probably need to become familiar with the terminal(a command line interface). You will need to do some research here on the forums to see how other people got those cards to work and follow the instructions to do the same.

---

### Post by ltcolfury on 2007-02-16
I used to use the exact same adapter and it worked fine using Ndiswrapper. I have a post on here explaining exactly how to do it.

OR you can go here: Just install it using the Package Manager & then follow the directions for the configuration.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

---

### Post by MikeyP on 2007-02-16
> **ltcolfury said:**
> I used to use the exact same adapter and it worked fine using Ndiswrapper. I have a post on here explaining exactly how to do it.


**Update:** Well, i was having problems with WG111, and as others have said, just re-compile ndiswrapper... then it worked fine for me!

---

### Post by ir0n_ma1den on 2007-02-18
the problem is that i cant connect to the internet using the computer w/ ubuntu on it. So do i have to dl the program from another computer and burn it to a disk?

---

### Post by willz06jw on 2007-03-04
no, ndiswrapper is on the ubuntu CD

---

