---
title: "[SOLVED] GPRS Modem works in win according to telecom's settings, what am i missing o"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by ninotsmindelivar on 2008-07-04
Hi there, this is I believe my first time posting for help, but I've been using ubuntu since dapper off and on; I love it :)

Help me do a little detective work? Here's the background.

I'm a Peace Corps volunteer serving in a small town in the Republic of Georgia. The Georgian ministry of education through a great program called "Deer Leap" has supplied computers to *every* school in the country, from the capital to the smallest village, and (here's the great part) they're all running Kubuntu :).

I've been running trainings on Linux and Ubuntu basics for local computer teachers and IT operators in the region, and I want to hit the internet issue here. We have yet to have internet in these schools, and as you know it makes updates tricky on *ubuntu. BUT, everyone has a glitzy phone, and I'm trying to get them working as GPRS modems so we can connect these computers out here in the meantime to the net.

I've done the research, and the closest I've come to getting it to work is taking the local telecom's gprs modem settings listed [here]("http://www.magticom.ge/index.php?section=80&lang=eng") and the gprs modem tutorial [here]("http://atunu.blogspot.com/2008/02/linux-redux-use-your-gprs-phone-as.html") to get it up, and I hit an error, which I'll get to.

The rub is, it's surely not my phone or my Magticom account, as on windows, following the instructions works, no problems. 

On linux, using the below copied configs, it will connect as far as the "G" indicator on my phone's display appearing as if it were about to connect, then refusing, the phone reporting the error message "Please subscribe to packet data first." I clearly AM subscribed, and the phone's settings are right, as with no changes the same phone will connect to Magti's gprs without a hitch on Windows.

On ubuntu gutsy, I have followed the aforementioned tutorial, which came up with the following ppp config file, and chatscript, all attached.

What I'm wondering is what is happening in windows with that dialup modem file by default that enables the connection, that isn't happening on the linux side. This seems so simple, but "doesn't work" still means "doesn't work."

I am also attaching the windows modem log file in case it helps you figure out what the modem is doing in windows that it isn't in linux, and what commands/code/etc I need to add to get it working on the linux side. I'll also add the log from the linux side, in case that helps show what ISN'T happening. All the attached linux text files are opening without line breaks in notepad on windows, from which I am posting, but hopefully they'll open fine in gedit/kate.

For the record, I'm doing this all on a Nokia 6133 (T-mobile variant of a Nokia 6126) phone of my own, which again is 100% capable of accessing Magti's net via gprs in windows.

Help me wire a village to the net!!!!! Thanks in advance

--
Ryder Cobean
Peace Corps Volunteer
Ninotsminda, Georgia

---

### Post by adewale on 2008-07-04
I use gprs on ubuntu and use nokia 5300.Follow the simple guide below and you should get online.

Launch a terminal from Applications -> Accessories -> Terminal

A terminal comes up connet your phone through a usb serial cable and then type sudo wvdialconf and press enter. This command searches your computer for any modem attached to it. If it finds it would tell you modem found. If its a phone it would say new device found /dev/ttyACM0

Then now type in this command also sudo gedit /etc/wvdial.conf Now you&#8217;ll have to edit it removing the unnecessary semicolons and then when yours look like mine then press save

[Dialer Defaults]

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = AT+cgdcont=1,"IP","3g.ge

Modem Type = USB Modem

Baud = 460800

New PPPD = yes

Modem = /dev/ttyACM0

ISDN = 0

Phone = *99#

Password = 

Username = 

Don't forget to enter your username and password (it seems ur isp didn't give u one just enter something).Then you return to the terminal and type sudo wvdial and press enter and it starts to connect once it does, don&#8217;t close that terminal because if you do that you go offline.

The Init 3 takes care of the subscribe to packet data, its actually your apn
You can take a look at [www.ubuntunigeria.wordpress.com](www.ubuntunigeria.wordpress.com) for other simpler ways of connecting through a gprs connection

---

### Post by ninotsmindelivar on 2008-07-26
> **adewale said:**
> I use gprs on ubuntu and use nokia 5300.Follow the simple guide below and you should get online.

Launch a terminal from Applications -> Accessories -> Terminal

A terminal comes up connet your phone through a usb serial cable and then type sudo wvdialconf and press enter. This command searches your computer for any modem attached to it. If it finds it would tell you modem found. If its a phone it would say new device found /dev/ttyACM0

Then now type in this command also sudo gedit /etc/wvdial.conf Now you&#8217;ll have to edit it removing the unnecessary semicolons and then when yours look like mine then press save

[Dialer Defaults]

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = AT+cgdcont=1,"IP","3g.ge

Modem Type = USB Modem

Baud = 460800

New PPPD = yes

Modem = /dev/ttyACM0

ISDN = 0

Phone = *99#

Password = 

Username = 

Don't forget to enter your username and password (it seems ur isp didn't give u one just enter something).Then you return to the terminal and type sudo wvdial and press enter and it starts to connect once it does, don&#8217;t close that terminal because if you do that you go offline.

The Init 3 takes care of the subscribe to packet data, its actually your apn
You can take a look at [www.ubuntunigeria.wordpress.com](www.ubuntunigeria.wordpress.com) for other simpler ways of connecting through a gprs connection
Thank you so much!!!!

I've been occupied by other stuff and generally flaky, so I really apologize for waiting this long to tell you how grateful I am. 

No more windows!

Thanks again.

PS: is there any way to make wvdial a non admin app -- just doubleclick and I'm off to the net, or any other way to make it not require more input on my side than kicking it off?

---

