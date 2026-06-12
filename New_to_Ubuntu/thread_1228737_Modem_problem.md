---
title: "Modem problem"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by nene7 on 2009-08-01
Hi, 
I am tried to install my modem but i cant i make one step; download the scanmodem and make the step with the scanmodem and the only thing that i found was this:

nene@ubuntu:~$ gunzip -c scanModem.gz > scanModem

nene@ubuntu:~$ chmod +x scanModem

nene@ubuntu:~$ sudo ./scanModem
[sudo] 
password for nene: 
UPDATE=2009_07_17
 
Continuing as this update is only 1 weeks old,
 but the current Update is always at: [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il)

Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.

Identifying PCI bus slots with candidate modems.
Running PCIbus cases
Analysing card in PCI bus 00:1b.0, writing to scanout.00:1b.0
Using scanout.00:1b.0 data, and writing guidance to ModemData.txt
Writing DOCs/Intel.txt

 Writing residual guidance customized to your System.
   A subfolder Modem/  has been written,  containing these files with more detailed Information: 
 ------------------------------------------------------------------------------------------
 1stRead.txt  Bootup.txt  dmesg.txt  DOCs  ModemData.txt  scanout.00:1b.0  tmp
    and in the DOCs subfolder:
 Agrsm.txt     DriverCompiling.txt  InfoGeneral.txt  Intel.txt
LSI_Agere.txt     Rational.txt          SoftModem.txt    Testing.txt
UNSUBSCRIBE.txt  wvdial.txt          YourSystem.txt
-------------------------------------------------------------------------------------------
       Please read 1stRead.txt first for Guidance.

What i have to do next?

---

### Post by lkraemer on 2009-08-01
I believe you're thinking incorrectly, as the script you downloaded does
not intall your driver, as it only gets information about your computer.
What you want to do is find out if your current computer, running some
Linux Distro, will support and use a Winmodem, so you don't have to purchase another one.

Well, the last line you posted says it all!  READ the text file first as 
this post states.  "Please read 1stRead.txt first for Guidance."  Then,
READ the "ModemData.txt" document.  Now I know you are going to say I
don't understand all that information, so the easy way is to send that
information to Marvin, and the folks at linmodems so they can decipher it for you.  

Basically, you have three options
1. Go to [www.linmodems.org](www.linmodems.org) and get help there with the modem,
if it is a Winmodem. Marvin and those folks are very helpful.  You will
download the ScanModem.tool and execute that script to get the
information on the modem. Then subscribe to the Linmodems discussion
list.  Then send Marvin an email (in plain text..ONLY) to the discussion
list. He will analyze your results and get back to you on what to
do to get the correct drivers to get them working.  You will be working
for several days with lots of emails,......unless you are lucky.

Now let me repeat that so you understand, "Your email MUST BE PLAIN TEXT
not html.  Just change your email format to TEXT! "Only plain text email
is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server, as
HTML can contain viruses."

2. Purchase a USRobotics USB Modem for ~$44.00 (Walmart)
3. Search Ebay for a Serial External USRobotics Hardware modem.

I'd suggest options 2 or 3, but some folks are lucky, and get their
Winmodem working.

Once that is done you're 80% done.........or you can use an External
USR Modem with your serial port or USB to serial Adapter and forget the
extra multiple days' hassel of the Winmodem..... Walmart also is selling
a USB External Modem for around $44.00 that is supposed to work good
without a wallwart or extra serial cables......

If you don't have a serial port, or want to use a USB port check out
the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a 82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $10.99.

These work wonderful with wvdial, etc.

Once that decision is made, you will need to set up the pap-secrets and/or chap-secrets file by running the following in a Terminal Window:
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
man pppdconfig

```
pap-secrets file contains:
(NOTE: File Format may have changed for versions later than 8.04)
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#    *    password
"yourusername@yourisp.net" provider "yourpassword"

```
Now after ppp is setup, you will need to set up wvdial. Power up the modem, and connect it to your serial port.
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
You also need to do this after wvdial is installed and
after pppconfig is executed:
To enable dialout without Root permission do:
$ su - root (not for Ubuntu)
sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
sudo chmod a+x /usr/sbin/pppd

Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:

wvdial /etc/wvdial.conf

You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny
characters) and then you should stay connected. (you will use CNTL C to
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

lkraemer

---

### Post by nene7 on 2009-08-01
thanks

---

