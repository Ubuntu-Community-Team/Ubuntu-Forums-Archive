---
title: "Using Mobile Broadband"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Karen Forrest on 2009-09-02
Hi, I'd like to get a mobile broadband connection working on 8.10. I'm using safaricom in Kenya. They provide a Huawei E220 modem. It's recognised by the network configuration, but doesn't succeed in making a connection. I hunted round and found 2 different sets of instructions for setting up wvdial. 
First I tried: [Dialer bambanet], Init1 = ATZ, Init2 = AT+CPIN=*my pin*, Init3 = AT+CGDCONT=1,"ip","safaricom", Stupid Mode = 1, Modem Type = USB Modem, Baud = 460800, New PPPD = yes, Modem = /dev/ttyUSB0, ISDN = 0, Phone = *99#, Password = knn, Username = saf
Then this: [Dialer Defaults], Phone = *99#, Username = saf, Password = data, Stupid Mode = 1, Dial Command = ATDT, [Dialer safaricom], Modem = /dev/ttyUSB0, Baud = 3600000, Init2 = ATZ, Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0, ISDN = 0, Modem Type = Analog Modem, Init4 = AT+CGDCONT=1,"IP","SAFARICOM"
This second setup requires me to send an extra command with the pin, before dialling, which I did. Buteither way when I try to connect, I get:
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","SAFARICOM"
AT+CGDCONT=1,"IP","SAFARICOM"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER

And it goes on trying and trying...Any ideas?
Thanks,
Karen

---

### Post by LewRockwell on 2009-09-02
[http://ubuntuforums.org/search.php?searchid=63682583](http://ubuntuforums.org/search.php?searchid=63682583)

here are other accounts for your device

.

---

### Post by GeorgeVita on 2009-09-02
Hi **Karen Forrest**,
for your tests I propose to remove SIM PIN lock (using a mobile phone).
Then try again using the following /etc/wvdial.conf file, so edit it:
```
gksudo gedit /etc/wvdial.conf
```Delete any existing line and copy/paste all lines below: ```

[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = web
Password = web
Phone = *99#
Stupid Mode = 1
Dial Attempts = 1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","web.safaricom.com"

```SAVE, Close gedit, try to connect with:
```
sudo wvdial
```  If connected, open Firefox and remove Offline Mode with **ALT-F W**
Disconnects with CTRL-C at the terminal window you made (hope) the connection.

In any error post here the terminal messages to follow up.

Regards,
George

---

### Post by hovzio on 2009-09-02
I have the same modem, I have found several solutions but must say that I found this little app called umtsmon and it made things "dead simple", also I am able to send text messages, and some other things. Its a nice little gui. One thing you have to stop ubuntus NetworkManager for this to work properly.. Heres the site,

```
http://umtsmon.sourceforge.net/downloads.shtml
```

There is only a source tar avaiable here but there are debs out there for download that work fine. I can upload mine (deb) if you wish but its better practice to install things only from an "known" sources. Using alien to convert an rpm to deb will work just fine. Heres the command to disable NetworkManager

```
sudo /etc/init.d/NetworkManager stop


```

Use start to "start" things up again. umtsmon needs to be run with roots privledges, keep in mind your running a gui so use gksudo. Hope this was of some help ;)

---

### Post by Karen Forrest on 2009-09-04
Thanks for replies - sorry about delay responding, we have power rationing here, so no electricity on Thursdays.
I decided to stick with editing wvdial.conf and followed your instructions, George, and that works great. As this doesn't give me access to the ISP's program, I guess I'll be visiting windows every now and then to make top ups. But as I have access via my college's wireless network most days and only use the modem when I'm away or it is down that is OK.
hozvio - I'm still beginning with the whole ubuntu experience and the phrase "Using alien to convert an rpm to deb will work just fine" means nothing to me? But thanks for trying.
Regards,
Karen

---

