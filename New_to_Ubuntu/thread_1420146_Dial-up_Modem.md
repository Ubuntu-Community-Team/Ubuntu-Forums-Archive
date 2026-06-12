---
title: "Dial-up Modem"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by LeRoyCountryboy on 2010-03-02
I've just received my Ubuntu 9.10 CD and intstalled on another laptop, completely replacing MS Windows, so it's a Ubuntu-only machine. I don't have Broadband so I'm trying to connect via a dial-up modem. Doesn't look like the standard installation of Ubuntu 9.10 supports dial-up as I can't find anywhere to specify my ISP dial-up telephone details. I saw something in Ubuntu instructions about downloading a Gnome-Network-App but I'm lost. Is Ubuntu any good for someone who has only dial up internet? And how can I get Ubuntu to get me connected?

---

### Post by Temposs on 2010-03-02
Can you run this command in the terminal:

```
sudo pppconfig
```

Go through the steps as well as you can. When it's done, type:

```
pon
```

and see if it will connect.

---

### Post by Temposs on 2010-03-02
For help with how to do pppconfig, go here:

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-0769b0061bf81bfba710118540bd86223e815761](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-0769b0061bf81bfba710118540bd86223e815761)

Scroll down to "Alternative Way 2 (using pppconfig & pon/poff)" and follow the instructions.

---

### Post by lkraemer on 2010-03-02
You will need to download wvdial, and the four dependencies.
libc6, libuniconf4.6, libwvstreams4.6-base, libwvstreams4.6-extras
if they are not installed.

If you don't use a US Robotics External Serial Hardware Modem,
you can try the WinModem, but it will be lots of work.

For a WinModem:
You need to go to the [http://www.linmodems.org/](http://www.linmodems.org/) site, then download
the ScanModem.tool and execute that script to get the information
on the modem. Then subscribe to the Linmodems discussion list.
Then send Marvin an email (in plain text..ONLY) to the discussion
list. He will analyze your results and get back to you on what to
do to get the correct drivers to get the WinModem working.

You can also search the archives posted there for your modem and read
those messages about how others have tried to get theirs working.
Use EDIT then FIND for your modem and search each month for responses
to keep from pouring over each months' ton of postings.

Once that is done you're 80% done.........or you can use an External
USR Modem with your serial port or USB to serial Adapter and forget the extra
multiple days' hassel of the Winmodem.....

If you don't have a serial port, or want to use a USB port check out
the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a
N82E16812156008 SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin)
Converter Model SBT-USC1M - Retail @ $10.99.

These work wonderful with wvdial, etc.

For an External US Robotics Hardware Modem:
Once that decision is made, you will need to set up the pap-secrets and/or
chap-secrets file by running the following in a Terminal Window:
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppconfig

```
pap-secrets file contains:
(NOTE: File Format has changed for versions later than 8.04)
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"yourusername@yourisp.net" provider "yourpassword"

```
Now after ppp is setup, you will need to set up wvdial. Power up the modem,
and connect it to your serial port.
In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file like this at
/etc/wvdial.conf (you may need to add a few things...)

wvdial.conf contains:
```


[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```
You might want to double check the following settings:
Checking settings of: /etc/ppp/options
```

asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

```

Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```
You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN...) You may have to uncheck the box
marked OFFLINE when you open your browser to make it online. Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

wvdial.conf info:
[http://linux.die.net/man/5/wvdial.conf](http://linux.die.net/man/5/wvdial.conf)

PPP HOWTO:
[http://tldp.org/HOWTO/PPP-HOWTO/index.html](http://tldp.org/HOWTO/PPP-HOWTO/index.html)

PAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1034.html](http://tldp.org/HOWTO/PPP-HOWTO/x1034.html)

CHAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1053.html](http://tldp.org/HOWTO/PPP-HOWTO/x1053.html)

Setting up PPP Manually
[http://tldp.org/HOWTO/PPP-HOWTO/manual.html](http://tldp.org/HOWTO/PPP-HOWTO/manual.html)

MORE REF's:
[http://www.ubuntugeek.com/setting-up...in-ubuntu.html](http://www.ubuntugeek.com/setting-up...in-ubuntu.html)
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
[https://help.ubuntu.com/community/Di...to/SetUpDialer](https://help.ubuntu.com/community/Di...to/SetUpDialer)
osdir.com/ml/ubuntu.doc/2005-04/pdfuHGgEItwtF.pdf

[https://wiki.edubuntu.org/DialupModemHowtoOld](https://wiki.edubuntu.org/DialupModemHowtoOld)

wvdial info:
[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)
[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)
[http://tldp.org/HOWTO/PPP-HOWTO/x314.html](http://tldp.org/HOWTO/PPP-HOWTO/x314.html)
[http://www.squarebox.co.uk/cgi-squar.../wvdial.conf.5](http://www.squarebox.co.uk/cgi-squar.../wvdial.conf.5)

Finally, when wvdial is working you can configure/set up Gnome-PPP.

When you get everything working, I'd suggest backing up the pap-secrets,
chap-secrets, and wvdial.conf files....just in case.
You can use:
```

cd /
cd /etc/ppp
sudo cp pap-secrets pap-secrets.sav
sudo cp chap-secrets chap-secrets.sav
cd ..
cp wvdial.conf wvdial.sav

```
to save the backup files.

lk

---

### Post by Bartender on 2010-03-02
Aren't we putting the cart before the horse?  It's highly unlikely that his laptop modem will work in Ubuntu.

Puppy, maybe, but not Ubuntu.

---

### Post by lkraemer on 2010-03-03
That is why there were two choices posted, along with a
warning that it might take days.......:

1. For a WinModem:
2. For an External US Robotics Hardware Modem:

lk

---

### Post by maraldi on 2010-03-03
You could make it much easier for yourself by just installing the KDE desktop and using the KPPP program.

KPPP has a menu for setting up the modem and after that when you start the program it presents you a login screen.

The only thing is if you use it in XFCE or Gnome you have to start a terminal as root and then type KPPP to start up the program.

I wouldn't even mess around with the Winmodems.

Buy a serial modem or a USB modem, you can get one for around $30 USD.

---

### Post by Bartender on 2010-03-03
Using KDE instead of Gnome simply to bypass a bit of extra setup hassle seems the wrong way to go.  Unless you want to use KDE, or don't really care.

#1 You must have a compatible ISP.  NOT PeoplePC, Juno, AOL..
#2 You must have a modem that works.
#3 Set things up with pppconfig, then get online and have Synaptic update, then ...wait a minute, I explained all this in Dial-up Redux thread, link below.

---

### Post by maraldi on 2010-03-03
> **Bartender said:**
> Using KDE instead of Gnome simply to bypass a bit of extra setup hassle seems the wrong way to go.  Unless you want to use KDE, or don't really care.



ok I wouldn't suggest just switching for that reason alone, but I have KDE, XFCE and Gnone all installed on the same machine without any problems.

---

### Post by lkraemer on 2010-03-03
GNOME PPP will also work fine, but most likely won't work without
setting up pppconfig and then wvdial before trying GNOME PPP.

lk

---

### Post by Paul-2 on 2010-03-09
Thanks much to everyone.  After days of trying I was about to give up; but found this thread..

tnx again,Paul

---

