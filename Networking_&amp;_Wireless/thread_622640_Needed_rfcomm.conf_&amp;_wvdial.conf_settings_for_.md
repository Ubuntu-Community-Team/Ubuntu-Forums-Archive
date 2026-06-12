---
title: "Needed: rfcomm.conf &amp; wvdial.conf settings for N95 on UK's Three Network"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by jonqrandom on 2007-11-25
So... I have an N95, Three's 3GB/month data plan, and an ubuntu laptop.  rfcomm creates the /dev/rfcomm0 device which wvdial used *once* to start a PPP connection which looked ok in ifconfig, but didn't do much (i'm guessing route issues).  

Anyway, after a reboot, which I thought might help, I just get "Invalid dial command" when wvdial runs :(  cutecom and minicom fail to get me any response to AT or ATI1.  

About the only thing I can get to work is to change the number in wvdial.conf to my old mobile number and make it ring that, but that's not a great deal of use, just proof something is (vaguely) working :/

I've tried *99***#1 as the number to dial (the one that worked once), I've tried *99#, and *99*111# . Same result, "Invalid Dial Command" :(

And yeah, the N95 can happily use the internet itself.

Please, if you have any experience using a bluetooth connection with a Nokia phone to hook a linux box up to the internet, let me know what you've done, especially if you're on Three!

---

### Post by phillips247n on 2007-12-12
I tried but failed to get my mobile phone to run as a modem on Linux/Ubuntu.
The phone (a LG U890) seems to go through the motions but the phone displays the message 'TE Did not open'.

As I also use VMWare to run windows on the laptop (need it for work), I found that enabling the usb on the virtual windows results in a VM that sees the phone and will install the phone's windows manager software.  From there, I share the internet connection with the linux host machine.

Unfortunatly, I have to re-connect and then re-share the network each time, but with the lg phone still accepting calls, start the link each day/session and leave it connected.

I Would rather use the linux host to drive the modem, but for the times when I am away from my landline, this arrangement does the job.

I found the link to a guide for using the three modem here :-
[http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php](http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php)

but the LG phone wouldn't play.

I have put up a couple of pages re- using a vmware system with windows to get around the windows driver problems I had with the LG phone here :-
[http://www.internet.247n.com/MobileInternet/VistaLinuxInternetAccess.html](http://www.internet.247n.com/MobileInternet/VistaLinuxInternetAccess.html)

Essentially, if you can get the vmware player to run on your system and see usb devices (memory sticks etc) then there is a good chance that it will be able to run the older phone's software and get you connected.

Hope this helps

Phill

---

