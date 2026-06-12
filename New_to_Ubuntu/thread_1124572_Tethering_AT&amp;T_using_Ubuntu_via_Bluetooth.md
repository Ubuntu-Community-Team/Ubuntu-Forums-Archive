---
title: "Tethering AT&amp;T using Ubuntu via Bluetooth"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by hsjpatman on 2009-04-13
hi, I am new to Ubuntu.
My friend has been raving about it for a while and when the opportunity to get a Dell mini with Ubuntu arose, I jumped on it.
The only issue is I can't seem to tether the internet connection with my AT&T phone via bluetooth.
This was easy as pie in XP using a dial up networking connection.
I'd hate for this one thing to force me to return the Dell mini and get something with XP on it.
I have done endless searching, endlessly, to no avail.
Tried using wvdial which wouldn't even find the phone via bluetooth.
Tried doing it via usb and it recognized the phone, I edited the wvdial.conf file to change the phone number to *99#, user name to [email]WAP@CINGULARGPRS.COM[/email] and password to CINGULAR1.
Modem initializes but says it does not specify a valid phone number login name or password.
So basically, I can't get it to work even via usb cable and ultimately i'd like for it to work via bluetooth.
If anyone can help it would be greatly appreciated.

I can't believe there isn't a dial up networking equivalent to the one in XP.

---

### Post by Temposs on 2009-04-13
There are other dialup apps in Ubuntu that you can try. Here are a couple tutorials on the various methods of creating a dialup internet connection: 

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f229b8b898575bbd996c4dac3de0772d430f2a02](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f229b8b898575bbd996c4dac3de0772d430f2a02)

FWIW, I'm able to plug in my phone by USB and it appears in the network manager list when you click on the internet icon in the top right of the screen.  Then I select it and I can get an internet connection, without having to deal with dialup apps. I'm not sure if this provides the same kind of connectivity, though. And yes, I'm with AT&T, but no, I don't use my phone to connect to the internet.

---

### Post by Temposs on 2009-04-13
Here, try this(well, I'm using Ubuntu 8.10, so I'm not sure if this exists in your version):

Go to System->Preferences->Network Configuration in the menu. Then click the "Mobile Broadband" tab. Then click Add and work through the wizard.

If this doesn't exist for you, you might want to look into upgrading your Ubuntu version to 8.10(what I'm using) or wait a couple weeks for 9.04 to be released. Dell is still shipping machines with Ubuntu 8.04.

---

### Post by t0p on 2009-04-13
Try the link in my sig.  It's a bit old, but some of it may suit.

---

### Post by hsjpatman on 2009-04-14
Well thanks for trying.
After three days and countless hours of trying different things, I can't get it to work.

---

