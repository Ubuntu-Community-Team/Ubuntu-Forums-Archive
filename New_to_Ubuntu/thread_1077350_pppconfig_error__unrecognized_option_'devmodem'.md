---
title: "pppconfig error  unrecognized option '/dev/modem'"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Bob Appleby on 2009-02-22
Having a great time learning ubuntu but having no success at connecting to my modem. (no broad band here yet) Tried lots of suggestions from this forum, but with no success. The most promising appeared to be pppconfig. Everything seemed to go well but pon resulted in the following message. 

/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'

Does anyone know what it means and how to correct it.

Bob

---

### Post by spiderbatdad on 2009-02-22
check synaptic make sure you have pppoeconf...whcich you should. The solution may be linking /etc/ppp/ppp_on_boot to your pppoeconf. See this old bug. The package should have been patched so IDk really:
[https://bugs.launchpad.net/ubuntu/+source/pppoeconf/+bug/7911](https://bugs.launchpad.net/ubuntu/+source/pppoeconf/+bug/7911)

---

### Post by lswb on 2009-02-22
What kind of device are you using? Usually only a real telephone line dial-up modem will show up as /dev/modem. When you run pppconfig, you may have to change the line where it asks for the device from "modem" to something else. I sometimes use ppp over a cell phone for instance, and it is recognized as /dev/ttyACM0. So when first running pppconfig for a connection over this device, I substituted "/dev/ttyACM0" for "/dev/modem" when it asked for the device.

---

### Post by Bob Appleby on 2009-02-22
I'm using a normal house telephone line. However I reran pppconfig a number of times and never got the above error message again. Now when I run pon nothing happens. poff results in the message "no pppd running". The provider text files seem normal (etc/chatscripts/provider  and ppp/peer/provider). Any ideas as to what to do at this point?

---

### Post by lswb on 2009-02-22
> **Bob Appleby said:**
> I'm using a normal house telephone line. However I reran pppconfig a number of times and never got the above error message again. Now when I run pon nothing happens. poff results in the message "no pppd running". The provider text files seem normal (etc/chatscripts/provider  and ppp/peer/provider). Any ideas as to what to do at this point?

The error message from poff indicates just what it says in this case, no ppp connection is running. Try opening a terminal and running "pon -d" The -d option is for debug mode and error messages will be printed to the opened terminal. 

What kind of modem are you using? a true hardware modem will normally "just work" but many internal modems require drivers or software. My laptop for instance has a built-in intel modem that requires both a driver and a daemon for linux to use it successfully. Try the command 

lspci|grep -i modem

and see what comes up.

---

### Post by Bob Appleby on 2009-02-22
There is a check box in the quick reply mode that says "Quote message in reply?" What does it mean? (I feel as dumb as I did back in the early 80's on teaching myself 8080 machine code!)

I'm using an internal Conexant 56k modem in an HP laptop. The results from your suggestions follow:

rappleby@ubuntu:~$ pon -d
Usage: pon [OPTIONS] [provider] [arguments]
  -q|--quick           pppd hangs up after all ip-up scripts are run

If pon is invoked without arguments, /etc/ppp/ppp_on_boot file will be
run, presuming it exists and is executable. Otherwise, a PPP connection
will be started using settings from /etc/ppp/peers/provider.
If you specify one argument, a PPP connection will be started using
settings from the appropriate file in the /etc/ppp/peers/ directory, and
any additional arguments supplied will be passed as extra arguments to
pppd.

rappleby@ubuntu:~$ lspcilgrep -i modem
bash: lspcilgrep: command not found
rappleby@ubuntu:~$

---

### Post by lswb on 2009-02-22
Sorry, I was wrong about that -d option; should have checked the man page first. You could try this instead: open a terminal, run the command "tail -f /var/log/syslog" Then open another terminal and run the pon command. See what errors are being logged in the first terminal window as the pon command tries to run.

The conexant is a "softmodem" sometimes called a winmodem, meaning it does not do all the modem functions itself, but through its driver, uses the system processor for some part of its operation. In the past I have gotten agere/lucent and intel softmodems working with linux but I don't have direct experience with the conexant. 

First, you may be lucky, maybe the driver is already present on your system. From what I have seen by googling, a conexant may be given a device name something like /dev/ttySHCF0 or something similar. Try "ls /dev/ttySH*" from a terminal and see if anything similar is present. If so, run pppconfig again and use that device name when prompted.

If not, take a look at [https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)
which will refer you the [http://linmodems.org](http://linmodems.org) website. The scanmodem tool available there will help identify which chipset your modem uses and hopefully how to install a driver for it (Not all conexant models are supported) It can be a hassle getting one of these modems working. Try slogging through the procedure given on the linmodem site. If you need help post again and include whatver progress you have made. Good luck.

---

### Post by Bob Appleby on 2009-02-26
After a blizzard last weekend that made the phone go dead, turned off commercial power and required me to shovel a ton or more of snow, it is good to be back on line. The plow company couldn't plow the 500 foot driveway because of the amount of snow. They had to use a front end loader. $$$!

I tried the first two of your suggestions with no success, but the linmodems site looks very promising! The scanmodem tool gave me a pile of text files about my modem and they came with the offer to email the critical text file for expert analysis if I can't understand how to use it. I'll be very surprised if the modem is not working in a few days. 

Many, many thanks for your help.

Bob

---

### Post by Francis60 on 2009-03-25
I don,t know much about all of this as mine is still not working right. It was but as usual I had to fool around with it and now it is not working. Anyway for my laptop I sent it to Business Staples and the put a card in for a new Modem. You are mentioning something about PPPO, but Staples installed GNOME PPP on mine and it worked on my laptop. But like I said I fooled around with it and it not working right now. When I dial it goes for a few seconds and then shuts off, so maybe when I re configured it I did some thing wrong. Anyway maybe if you can install GNOME PPP it will work for you too.
Allan

---

### Post by lkraemer on 2009-03-25
Bob,
Will you try the following:

You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppdconfig

```

You will need to setup the pap-secrets file by running the following in
a Terminal Window:
```

sudo pppconfig

```

Your pap-secrets file should contain something like this when you are done
answering the questions:
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

Now after ppp is setup, you will need to set up wvdial.  wvdial should
locate your modem and tell you the /dev/idformodem
In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```

You should get a configuration file something like this at
/etc/wvdial.conf (you may need to add a few things...)

wvdial.conf contains:
(NOTE: your will be slightly different because of /dev/ttyACM0....etc..)
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 12345678
Password = yourpassword
Username = yourusername@yourisp.net


```

You might want to double check the following settings:
Checking settings of: /etc/ppp/options
edit in a terminal with:
```

sudo gedit /etc/ppp/options

```

My options file has:
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

lkraemer

---

