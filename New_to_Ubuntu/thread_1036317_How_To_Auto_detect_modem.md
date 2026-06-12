---
title: "How To Auto detect modem"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by sillyboy on 2009-01-10
Just installed a Cen-Dyne 56K RS232 external modem. I did a search on this topic, and found very little in the way of help. Upon boot... Ubuntu do not see it.  How do I get Ubuntu to auto-detect the modem?  After that, how do I set up everything with the right application(s)to use this modem as a FAX only modem.

Thank You:confused:

---

### Post by gettinoriginal on 2009-01-11
This thread has some great help:  :P
[http://ubuntuforums.org/archive/index.php/t-613433.html](http://ubuntuforums.org/archive/index.php/t-613433.html)

---

### Post by Daveth on 2009-01-11
and this may help as well

[http://dsl.org/cookbook/cookbook_37.html#SEC493](http://dsl.org/cookbook/cookbook_37.html#SEC493)

---

### Post by lkraemer on 2009-01-11
This may also help:
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)
osdir.com/ml/ubuntu.doc/2005-04/pdfuHGgEItwtF.pdf

Look at just the area here under HARDWARE MODEMS.....it is all that
applies to you.
[https://wiki.edubuntu.org/DialupModemHowtoOld](https://wiki.edubuntu.org/DialupModemHowtoOld)

wvdial info:
[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)
[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)
[http://tldp.org/HOWTO/PPP-HOWTO/x314.html](http://tldp.org/HOWTO/PPP-HOWTO/x314.html)
[http://www.squarebox.co.uk/cgi-squarebox/manServer/wvdial.conf.5](http://www.squarebox.co.uk/cgi-squarebox/manServer/wvdial.conf.5)

Since you are using an external modem the hard part is over.
If you don't have a serial port, or want to use a USB port check out
the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $8.99.

These work wonderful with wvdial, etc.

Basically you will need to do the following:
Configure wvdial with:

sudo wvdialconf

the config file will be at /etc/wvdial.conf
to configure your ISP's telephone number, login & password etc.

You can later edit your personal information with:
$ sudo gedit /etc/wvdial.conf

Open a Terminal window (you will leave it open the total time
you will be connected via dialup)

dial out with:
$ wvdial

SURF!!!
You can go back to the open terminal window and do a CNTRL C
to terminate the connection/session, then close the terminal window.

lkraemer

---

