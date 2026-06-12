---
title: "QNC wireless access from Verizon via LG vx6000"
date: 2005-06-16
forum: Networking &amp; Wireless
---

### Post by cdean on 2005-06-16
I am attempting to get my cellular phone, an LG vx6000, via USB to be used as a modem so that I may connect to Verizon's free QNC data service (okay, it costs minutes, but eh).  

On Windows, one has to install the LG drivers (Qualcomm CDMA phone drivers) and create a dialup connection with the user and pass as 'qnc' and the number as '#777'.  This works fine on every Windows box I've tried.

Under Linux, the cell phone shows up at /dev/ttyACM0.  I have verified this.  I can connect to the phone (gnome-ppp or the Networking applet in the System menu) and send commands to the modem part, but get disconnected immediately after dialing.

Here's the catch that I can't figure out:

When dialing from within Windows, the phone shows a "DATA CALL" banner.
When dialing from within Linux, the phone shows a "3G 1X DATA" banner.

3G 1X DATA is a paid service.  Theoretically, it should be another number and username, but it's not (go Verizon).

Has anyone tried this with a comparable phone?  Google has not been good to me in this regard.  [This write-up](http://www.nuclearelephant.com/papers/t30.html) helped a little, but the writer appears to subscribe to the paid service. Likewise for [this gentleman](http://www.linuxquestions.org/questions/answers/450).  

Any ideas?

---

### Post by cdean on 2005-06-19
Has anyone had a problem like this with another phone or another carrier?  I know I'm not the only one who has a cell phone and uses Linux on a laptop.

What are your experiences using a cell phone on a laptop as a modem?

---

### Post by khermans on 2005-06-21
[QUOTE=cdean]Has anyone had a problem like this with another phone or another carrier?  I know I'm not the only one who has a cell phone and uses Linux on a laptop.

What are your experiences using a cell phone on a laptop as a modem?[/QUOTE]

I am using my Verizon phone just fine.  I don't have a paid service either.  It just uses my minutes.  The qnc service is the low-bandwidth service, and the vzw 3G is the high-bandwidth service,  In my write up on linuxquestions.org I specified that if you really want to use qnc (but it sucks), to specify your user and pass to both be "qnc".  I have not verified this, but it should work according to other sources where I googled m info from anyways.  Try the 3G service first man, because if you are in your local calling area or in a place where digital service is available, you will be able to logon to 3G anytime.  I usually use it on the weekends when I have 100% free calling.  Give the high BW servcie a try first, and let me know if that doesn't work fo you.  If it does not, I may be able to hook up my phone and verify the qnc settings to log on...

Kristian Hermansen

---

