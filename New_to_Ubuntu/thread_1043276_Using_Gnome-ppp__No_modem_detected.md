---
title: "Using Gnome-ppp :: No modem detected?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by ElectroGhandi on 2009-01-18
Hello. I have to use dial up on my computer so I installed Gnome-PPP and went to options and Detect Modem. It says No modem detected. So I found some drivers for Intel 537ep (my modem) and installed them, but Gnome-ppp still says No modem detected. It also hangs on the Connecting little dialogue.

---

### Post by lkraemer on 2009-01-18
Internal Modems are trouble......
But you have to start somewhere......

What Version Ubuntu?
[https://help.ubuntu.com/](https://help.ubuntu.com/)

If you must try the Internal modem you will need to go to:
[http://linmodems.org/](http://linmodems.org/)

Then read and study the information for days.......or try a 
USR External Modem (Serial) and be up and running in short order.


Click on the proper Version of Ubuntu, then down to Networking, then
down to Modems....

Dialup Info:
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

This may also help:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
[https://help.ubuntu.com/community/DialupModemHowto/Modems](https://help.ubuntu.com/community/DialupModemHowto/Modems)

osdir.com/ml/ubuntu.doc/2005-04/pdfuHGgEItwtF.pdf

[https://wiki.edubuntu.org/DialupModemHowtoOld](https://wiki.edubuntu.org/DialupModemHowtoOld)

wvdial info:
[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)
[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)
[http://tldp.org/HOWTO/PPP-HOWTO/x314.html](http://tldp.org/HOWTO/PPP-HOWTO/x314.html)
[http://www.squarebox.co.uk/cgi-squarebox/manServer/wvdial.conf.5](http://www.squarebox.co.uk/cgi-squarebox/manServer/wvdial.conf.5)

If you don't have a serial port, or want to use a USB port check out
the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $8.99.

These work wonderful with wvdial, etc.

Basically you will need to do the following:
In a Terminal Window configure wvdial with:

$ sudo wvdialconf

the config file will be at /etc/wvdial.conf
to configure your ISP's telephone number, login & password etc.

You can later edit your personal information with:
$ sudo gedit /etc/wvdial.conf

Open another Terminal window (you will leave it open the total time
you will be connected via dialup)

dial out with:
$ wvdial

SURF!!!
You can go back to the open terminal window and do a CNTRL C
to terminate the connection/session, then close the terminal window.

Once this is done, you can change Gnome-ppp to do the same.

lkraemer

---

### Post by diablo75 on 2009-01-18
I'd give wvdial a try.

Open a terminal and type:

sudo wvdialconf

This will go out to autodetect modems and if yours is supported you'll see it's data rates scroll across the screen after typing the above command.

Next type:

sudo gedit /etc/wvdial.conf

Edit this text file to add the phone number, username and password you need to access your ISP.  Remove the semi-colons ; from the front of the lines you don't want to omit (like the username, password, phone number).

Save when finished.

Now to connect to the web, type in terminal:

sudo wvdial

Hopefully that works!

---

### Post by jimmy the saint on 2009-01-18
I would highlty recommend following lkraemer's advice and looking into an external serial modem.  I bought a zoom brand modem at OfficeDepot for $60 but there are others out there.  Check out ebay for some good deals.  They are much easier, you just plug it in and go.  Just make sure they are not winmodems or require drivers to be installed that only work with windows.  (I first bought a diamond brand modem that was like that).

---

