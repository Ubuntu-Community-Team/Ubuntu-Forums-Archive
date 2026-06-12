---
title: "Dialup on Fiesty 7.04"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by fortfox on 2007-06-20
Got dialup to work with Gnome ppp, using CenDyne External modem. This works thru serial port 9 pin. Hope this helps someone. The price was about $50. Gave up on finding a driver for Lucent WinModem.

---

### Post by Bartender on 2007-06-22
fortfox -
Got any links to that modem?

---

### Post by fortfox on 2007-06-22
Look it up on Google, Manufacturer is out of business still some on selves, any external serial modem should work.

---

### Post by kevdog on 2007-06-23
Lucent WinModem does work -- I have one in my laptop.  I set it up a long time ago, and forgot a lot of the details by the driver you need to use is the martian_modem driver.  

Some general details are found here:
[https://help.ubuntu.com/community/DialupModemHowto/Lucent](https://help.ubuntu.com/community/DialupModemHowto/Lucent)

Please use the scanmodem tool to verify.  Get ready to screw around with to make it work.  But I can tell you everything works great.

---

### Post by zorkerz on 2007-06-24
Hey all im trying to get this modem to work on my computer. 

scanmodem tool says i have this modem.

Class 0780: 11c1:0452 Communication controller: Agere Systems LT WinModem

Im running xubuntu 7.04.

Does anyone know how to get this to work. Im worried that supprok might have been dropped with the 2.6.15 kernel and im not sure how to go about making this work.

Any help or ideas would be much appreciated

---

### Post by kevdog on 2007-06-24
I think this is the same modem as mine.  I used the martian modem driver.  Go to the following page and then scroll down to "Martian, an alternive to ltmodem": [https://help.ubuntu.com/community/DialupModemHowto/Lucent](https://help.ubuntu.com/community/DialupModemHowto/Lucent)

Martian works for me, although the documentation is a little scant.

The martian modem page is here:
[http://martian.barrelsoutofbond.org/](http://martian.barrelsoutofbond.org/)

Write back if you need help compiling the drivers

---

### Post by zorkerz on 2007-06-24
i wondered that also but i do not get the error they refer to. 

> FATAL: Error inserting ltserial (...): Invalid argumentThe only error I get is the one refered to above > FATAL: module not found and the note for that only refers to hoary users. I think i will give it a try anyways but i don't have much hope.

Thanks

Update: unfortunately the wiki has not been updated since last year and i think there could be trouble with the feisty kernel now.

---

### Post by kevdog on 2007-06-24
The wiki for ubuntu is definitely a little outdated, but between the martian modem site, the INSTALL file found in the download, and the scripts found in the scripts directory, that should be enough to get you up and running.

---

### Post by zorkerz on 2007-06-25
Well I guess I had lo faith.

I did martian driver and now i can dial up with wvdial!

However Im having the same problem I did with the other modem in that it does not stay connected for long.

I have edited the /etc/ppp/options file as the wiki instructs but still cannot maintain a connection.

Update: 
in /etc/ppp/options adding the line "replacedefaultroute" does not prevent the modem from diconnecting when I try to visit a site or appear to create any different behaviour. 

Any ideas on how to get the modem not to disconnect so i can actually use the internet

---

### Post by kevdog on 2007-06-25
Cant really help you on this one -- who is dropping the call - you or the server.  Possibly something in the log file that could help you.

---

### Post by zorkerz on 2007-06-25
If i just leave it be without trying to use the internet it does not seem to kick me off. As soon as I try and access the internet it cuts out with saying:
> The PPP daemon has died: A modem hung up the phone (exit code = 16) exit code 16 according to the manual refers to a modem hang up
so it looks like the problem is on my end.

Also as soon as i try and connect it says > Cannot get information for serial port but then it continues on with the process.

Know where the log file goes to?

---

### Post by fortfox on 2007-06-25
Found other external modem,s by Google 20 to 50 dollar price range that use serial port some usb. I have not tried the USB ones however.

---

