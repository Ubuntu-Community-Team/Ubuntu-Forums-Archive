---
title: "Dialup question by newbie"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by crustyasp on 2011-02-06
I have had Ubuntu 10.04.1 installed on a Toshiba Satellite A100 since last October, and have not done a whole lot with it as I lacked the ability to connect to the internet because I am on dial up.

I now have a USRobotics 56K faxmodem model Sportster 00568602 taht is supposed to be Linux friendly and have received a serial to usb adapter that says Linux supported.

The serial to usb adapter driver installation disk gives Redhat 8, 9, and 73 drivers as Linux support.

My question is what Kind of can of worms is this going to cause, with trying to get these to work with Ubuntu. I am a total newb, and still am at the trepidation stage for this New type of OS. 

Just would like to add here, that I have really caught up on a lot of my delinquent paper work using OpenOffice, it for me is a charm to use. 

Thanks for any help and suggestions on where to look.

---

### Post by mike555 on 2011-02-06
I just use a small usb modem from Rosewill model RNX-56usb , it works great and about $25.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16825164005&Tpk=rosewill%20usb%20modem](http://www.newegg.com/Product/Product.aspx?Item=N82E16825164005&Tpk=rosewill%20usb%20modem)

---

### Post by sammiev on 2011-02-06
Read [this]("http://ubuntuforums.org/showthread.php?t=1589966&page=3"), post 22 and 27. Worked for me. GL :)

---

### Post by klytu on 2011-02-06
> **crustyasp said:**
> I have had Ubuntu 10.04.1 installed on a Toshiba Satellite A100 since last October, and have not done a whole lot with it as I lacked the ability to connect to the internet because I am on dial up.

I now have a USRobotics 56K faxmodem model Sportster 00568602 taht is supposed to be Linux friendly and have received a serial to usb adapter that says Linux supported.

The serial to usb adapter driver installation disk gives Redhat 8, 9, and 73 drivers as Linux support.

My question is what Kind of can of worms is this going to cause, with trying to get these to work with Ubuntu. I am a total newb, and still am at the trepidation stage for this New type of OS. 

Just would like to add here, that I have really caught up on a lot of my delinquent paper work using OpenOffice, it for me is a charm to use. 

Thanks for any help and suggestions on where to look.

I suggest that you first try getting the modem to work without installing the Linux drivers that came with it. Try connecting the modem to a USB port on your laptop via the serial to USB adapter you have. 

Then read these pages of the community docs:

[https://help.ubuntu.com/community/DialupModemHowto/Setserial](https://help.ubuntu.com/community/DialupModemHowto/Setserial)

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer?action=show&redirect=wvdial](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer?action=show&redirect=wvdial)

The steps are:

1. See if Ubuntu finds your modem in its list of USB serial devices (that's what the first link above is about); if it's found it will be associated with ttyUSB***x*** where ***x*** is equal to 0,1,2, or 3

2. If it does, configure your dial-up connection (that's detailed in the second link) using /dev/ttyUSB***x*** (substituting 0,1,2 or 3 for ***x*** based on what you found out in step 1.) as the device name of your modem.

If you get confused during the process, post back and we'll try to help.

---

### Post by crustyasp on 2011-02-09
Thanks for the links and suggestion, will give this a try, may be a couple of days before I get back with a success or failure story. thanks to all who have replied.

---

