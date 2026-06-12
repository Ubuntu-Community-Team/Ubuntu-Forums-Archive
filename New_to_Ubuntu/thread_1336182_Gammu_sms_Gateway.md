---
title: "Gammu sms Gateway"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by jmwalloh on 2009-11-24
Hi, i've just downloaded gammu sms gateway and intend to use it with Huawei E160 modem. Any one out there having a configuration file that i can use as a guide for this 2 combination. I'm using Ubuntu Karmic. Any help will be appreciated!!  :)

---

### Post by Sven6210 on 2010-03-27
I have exactly the same issue - did you find any solution yet? If so could you please post what mad it work for you?

---

### Post by Sven6210 on 2010-03-27
I found the solution how gammu works with the Huawei E160

1. use synatics to install gammu

2. in the terminal window run:

gammu-config

Make the following settings:
Port: (/dev/ttyUSB1)
Connection: (at115200)
Model: ()
Synchronize time: (yes)
Log file: ()
Log format: (nothing)
Gammu localisation: ()

Save the file

3, in the terminal window run:

gammu --identify

This should show that gammu found the Huawei E160

Now you can use gammu to receive and send SMS.


**Sending an SMS**
In order to send an SMS enter the following command in the terminal window:

echo 'Here is the text of your SMS' | gammu sendsms TEXT +1234567890

where +1234567890 is the telephone number


**Reading SMS**
In order to read all SMS on your E160 and the SIM card enter in the terminal window:

gammu --getallsms


For further details of how to use gammu see:
[http://www.gammu.org/wiki/index.php?title=Gammu:Reference_manual](http://www.gammu.org/wiki/index.php?title=Gammu:Reference_manual)

---

