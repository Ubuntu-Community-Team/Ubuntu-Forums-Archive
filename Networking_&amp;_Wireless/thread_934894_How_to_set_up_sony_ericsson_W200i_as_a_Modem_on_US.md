---
title: "How to set up sony ericsson W200i as a Modem on USB"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by affran on 2008-10-01
I live in Bangladesh.I pluged in SE W220i using the USB lead supplied with the phone.
Autodetect the modem using WVDial:-
$ sudo wvdialconf
Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyACM1<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

Edit the .conf file:-
$ sudo gedit /etc/wvdial.conf

***_But it says:_***
affran@affran-laptop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","blweb"
AT+CGDCONT=1,"IP","blweb"
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
affran@affran-laptop:~$ 

***_[COLOR="Blue"]How do i edit the phone number,login name or the password?[/COLOR]_***
Please reply asap.

---

### Post by Rayaz on 2008-10-01
Edit wvdial.conf
For phone number use: *99#
For user name: a
For password: b
Should work!

---

### Post by affran on 2008-10-02
Thank you for the reply.But whenever i try to edit the wvdial.conf using text editor [COLOR="Navy"]*_it says:_*[/COLOR]

[COLOR="Navy"][I][B]Could not save the file /etc./wvdial.conf
You do not have the permissions necessary to save the file.
Please check that you typed the location correctly and try again
[/B][/I][/COLOR]:confused:

What's the solution?:(
Please reply asap.

---

### Post by Rayaz on 2008-10-02
You did manage to edit the wvdial.conf file before, didn't you? 
If not then try this:

sudo gedit /etc/wvdial.conf

Type your password, you won't be able to see what you're typing, hit Enter key. Edit the file and save. You should be good to go!

You could follow this link to set up gprs on your mobile phone as well:[http://www.zyxware.com/articles/2008/02/11/setting-airtel-gprs-ubuntu-nokia-communicator-9300-and-data-cable](http://www.zyxware.com/articles/2008/02/11/setting-airtel-gprs-ubuntu-nokia-communicator-9300-and-data-cable). It should work equally well for your mobile too.

Does your SE W220i have USB internet option? You can check it from Menu-->Settings-->Connectivity-->USB. If it does then it is a simple matter to turn it on. The next time you connect your mobile to your computer select phone mode on the mobile and you are connected!

---

### Post by affran on 2008-10-03
Thankssssssssssssssss for the solution!=D> and Eid Mubarak!:)

---

### Post by Rayaz on 2008-10-04
Glad to be of help, and Eid Mubarak to you too. :D

---

### Post by affran on 2008-10-05
I am very sorry:confused: to say that I've edited the wvdial.conf according to your suggestion.
  ***_But it says again:_***
But it says:
[COLOR="Blue"]affran@affran-laptop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","blweb"
AT+CGDCONT=1,"IP","blweb"
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
affran@affran-laptop:~$ [/COLOR]

What will i do know?What's the solution?:-k
Help!

---

### Post by Rayaz on 2008-10-07
Please post your wvdial.conf file. Use Nautilus to browse to the etc folder and from there open the wvdial.conf file with gedit and paste here.


It should look some thing like this, I've used your mobile operator's APN.


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","blweb"
Modem Type = USB Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyACM0
Username = b
Password = a
Baud = 460800

---

### Post by Rayaz on 2008-10-07
You could also try out gprsec. You can download it from:[http://www.darrenalbers.com/gprsec/gprsec_3.0.1-1_i386.deb](http://www.darrenalbers.com/gprsec/gprsec_3.0.1-1_i386.deb). Since it is a debian package you shouldn't have too much trouble installing it. Just double click on it to install.

---

### Post by affran on 2008-10-20
[COLOR="Blue"]:(Sorry for not replying soon
I was busy.

[/COLOR]
[COLOR="DarkGreen"]Here is that wvdial file
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","blweb"
Modem Type = USB Modem
; Phone = <*99#>
ISDN = 0
; Password = <a>
New PPPD = yes
; Username = <b>
Modem = /dev/ttyACM0
Baud = 460800
[/COLOR]

---

### Post by Rayaz on 2008-10-21
please delete the semicolons at the start of the lines


--> ; Phone = <*99#>
    ISDN = 0
--> ; Password = <a>
    New PPPD = yes
--> ; Username = <b>

---

### Post by affran on 2008-10-22
Thanks Problem Solved.It worked!:guitar:
May **Allah** bless u.

---

### Post by Rayaz on 2008-10-22
Glad to hear you got it working. Keep gprsec in mind, if you ever get tired of wvdial.:)

---

