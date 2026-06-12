---
title: "Dial-up not supported"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by 7beauties on 2010-11-30
I set up Ubuntu 10.10 on my friend's computer because he wants a free operating system.  My friend and I are very impressed with Ubuntu and its many features, unfortunately we discovered that Ubuntu doesn't support dial-up modems.  There was the suggestion that a "Debian" driver would provide a solution.  My friend isn't computer literate and I've only intermediate knowledge.  We would be very grateful if someone here who's smart can give us simple, easy to understand and follow directions on how to install a driver to enable his dial-up modem.  Also, if someone could suggest a good, affordable ISP that supports Linux (Ubuntu) it would be greatly appreciated also.  Thank you for any help you can provide.  It would be a blessing.  :confused:

---

### Post by Rex Bouwense on 2010-11-30
Look here:  [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

---

### Post by lkraemer on 2010-12-01
7beauties,
The guide Rex pointed you to is good, but assumes too much for the typical
person to get started.

The first question is do you have a WinModem, or an External Serial USR
Hardware Modem (or USB Hardware Modem)?  You can find some USR External
Serial Hardware Modems on [www.ebay.com](www.ebay.com) that are reasonable.

If so, you need to go to the [http://www.linmodems.org/](http://www.linmodems.org/) site,
then download the ScanModem.tool and execute that script to get the
information on the modem. Then subscribe to the Linmodems discussion list.
Send Marvin an email (in plain text..ONLY) to the discussion list.
He will analyze your results and get back to you on what to do to get
the correct drivers to get the Modem working.

You can also search the archives posted there for your model and read
those messages about how others have tried to get theirs working.
Use EDIT then FIND for your model and search each month for responses
to keep from pouring over each months' ton of postings.

Once that is done you're 80% done.........or you can use an External USR
Hardware Modem with your serial port or USB to serial Adapter and forget
the extra multiple days' hassel of the Winmodem..........

If you don't have a serial port, or want to use a USB port check out
the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a 
N82E16812156008 SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin)
Converter Model SBT-USC1M - Retail @ $10.99.

These work wonderful with wvdial, etc.

**DIALUP ISP's supporting Linux:**
I use Copper.net, but you can search the Forum to find an ISP that 
supports Linux.  Copper.net is Nationwide in the USA, with access numbers
in just about every town.

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
Now that ppp is setup, why don't you install wvdial and it's dependencies and
see if wvdial detects the modem. You might find it works......

You need to download wvdial and the following dependencies for 10.04,
or whatever version you have installed......
```

wvdial & dependencies:
libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

```
Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download these with XP or Ubuntu, then copy the *.deb files to USB Flash Drive,
& then to Ubuntu subdirectory /var/cache/apt/archives & then install using Synaptic Package Manager.....ie.
```

sudo cp ~/Downloads/mydebs/*.deb /var/cache/apt/archives

```
OR you can go to SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
and check the box for installable from CDROM/DVD.........then
insert your LiveCD and install from the CDR.

Power up the modem, and connect it to your serial port.
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

Let us know how it goes.....You should be up and running in less than 45 minutes.....

lk

---

### Post by 7beauties on 2010-12-01
Thank you Rex and IKraemer.  I appreciate your reaching out to help me.  I'm virtually a newbie and am determined to help my friend get online.  We're both amazed and delighted with the features of Ubuntu 10.10 and feel that it's a great alternative to Windows which costs a lot of money.  I love the philosophy of Ubuntu in that an operating system should be free.  My friend's modem is an internal PCI modem.  I shall investigate the external USB modem from Newegg.com.  It's very reasonably priced and I hope that it would work with Ubuntu.  If I were to purchase this external dialup modem from Newegg.com would it work?  Is there an equivalent of Plug and Play with Ubuntu?  I don't know anything about ports and POP3 and IMAP and so forth.

---

### Post by QLee on 2010-12-01
[QUOTE=7beauties]...
If I were to purchase this external dialup modem from Newegg.com would it work?  Is there an equivalent of Plug and Play with Ubuntu? 
...[/QUOTE]

Because Ubuntu has to fit on a single install CD, the developers have to choose what to include. Since in 2010, very few users still use or need a dialup connection for Internet, it isn't supported "out of the box" to use a common phrase.

However, you can be successful following lkraemer's step-by-step, I've see it happen several times in the forum.

By the way, and this probably won't matter much to you, I use  dialup connection with a "hardware" modem, works fine but seems very slow compared to broadband of any kind, your friend might want to not allow their browser to show pictures or flash objects.

---

### Post by lkraemer on 2010-12-01
The best choice is a US Robotics External Serial Hardware Modem
such as [www.ebay.com](www.ebay.com) item #200549696974

You might want to take a chance on the PCI Modem already installed, and see
if wvdial detects it.  Chances are it won't be found.  Then you could get
the Script from Marvin and the fine folks at [www.linmodems.org](www.linmodems.org)
and see what drivers are needed.  Marvin and those folks are a lot of help.

I've heard that the USB US Robotics Modem works also, but I haven't tried
one of those.

lk

---

### Post by mike555 on 2010-12-02
[QUOTE=*********  I shall investigate the external USB modem from Newegg.com.  It's very reasonably priced and I hope that it would work with Ubuntu.  If I were to purchase this external dialup modem from Newegg.com would it work?  Is there an equivalent of Plug and Play with Ubuntu?  I don't know anything about ports and POP3 and IMAP and so forth.[/QUOTE]

-- you can look on Neweggs user reviews and use the keyword Ubuntu , they will say if it works with Ubuntu, I have found serial modems are best ..

---

### Post by dmizer on 2010-12-02
Please keep the discussion to support related answers. Thank you.

---

### Post by lkraemer on 2010-12-04
How is your progress going?  Is it working?

We would Greatly Appreciate a Follow-Up Post!

lk

---

### Post by 7beauties on 2010-12-05
Thank you everyone for your help, especially from IKraemer.  I've been working but now that I'm off I'll look for an external dialup modem for my friend.  I'll check the list of modems supported by Ubuntu and let everyone know what happens.  Thank you again for all your support.  :)

---

### Post by sammiev on 2010-12-05
Hi 7beauties, I found this [thread]("http://ubuntuforums.org/showthread.php?t=1589966") to be very helpful with a USB modem. Worked first try. GL :)

---

