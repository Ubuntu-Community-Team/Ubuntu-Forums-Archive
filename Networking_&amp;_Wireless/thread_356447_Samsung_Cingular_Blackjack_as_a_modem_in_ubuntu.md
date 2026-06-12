---
title: "Samsung Cingular Blackjack as a modem in ubuntu"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by gedeyenite on 2007-02-08
In windows I am able to connect to the internet by using my Cingular Samsung Blackjack smartphone as a modem.

I have gotten as far as making ubuntu see my phone, but I am having difficulty actually connecting to the cingular network.

Has anyone had success with this?

I am not on my ubuntu lappy at the moment, but when I am I will copy down the messages I get in the terminal windows when I try to connect.

Hopefully we can collaborate to a solution and then post a kick @ss "how to" for us beginner types out there.

Murph

---

### Post by jdfreshwater on 2007-03-07
Finally got it working via the USB cable that is provided. I did it by using the Gnome PPP Program.

After you install the program and open it.
Then put in the username of [email]ISP@CINGULARGPRS.COM[/email] and Password of CINGULAR1 that has been provided to you.
You also need to tell it to dial the number of *99#.
Go into setup and Detect modem it should bring up somthing like /dev/ttyACM0 for you.
Uncheck the box that says wait for dial tone.
Click on Init Strings and put in at+cgdcont=1,"IP","isp.cingular".
This should be in the first box, there may be something already there.
Go to the Options tab and only have the box checked that says check default route.
At this point you can close and connect.
Note you will have to ifdown any other connections that you may have going and possibly retry to connect again, but it should dial out and let you connect. Happy interneting.

---

