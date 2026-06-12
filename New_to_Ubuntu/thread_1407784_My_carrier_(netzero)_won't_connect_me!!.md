---
title: "My carrier (netzero) won't connect me!!"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by one_nz on 2010-02-15
my dial up carrier (netzero) wont connect me...
i am currently using wvdial and i get the following:

```

jacob@jacob-desktop:~$ sudo wvdial
[sudo] password for jacob: 
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT6831245
--> Waiting for carrier.
ATDT6831245
CONNECT 460800 
--> Carrier detected.  Waiting for prompt.
GlobalPOPS
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: (erased 4 privacy)@netzero.com
(erased 4 privacy)@netzero.com
Password: 
--> Looks like a password prompt.
--> Sending: (password)
Request Denied
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: (erased 4 privacy)@netzero.com
(erased 4 privacy)@netzero.com
Password: 
--> Looks like a password prompt.
--> Sending: (password)
Request Denied
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: (erased 4 privacy)@netzero.com
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Mon Feb 15 15:58:08 2010
--> Pid of pppd: 3851
--> Using interface ppp0
--> pppd: ï¿½ï¿½ï¿½ Hï¿½ï¿½ 
--> pppd: ï¿½ï¿½ï¿½ Hï¿½ï¿½ 
--> pppd: ï¿½ï¿½ï¿½ Hï¿½ï¿½ 
--> pppd: ï¿½ï¿½ï¿½ Hï¿½ï¿½ 
--> pppd: ï¿½ï¿½ï¿½ Hï¿½ï¿½ 
--> Disconnecting at Mon Feb 15 15:58:12 2010
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)
jacob@jacob-desktop:~$

```

What do i need to do to get this to work!?
(I TRIPLE CHECKED THE PASSWORD, it is correct)
I have Ubuntu jaunty (9.04)
my kernel version is 2.6.28-11 Generic

any help would b appreciated :)
-Jacob

---

### Post by Crafty Kisses on 2010-02-15
Have you tried editing the wvdial.conf file? If you haven't tried, run the following in the terminal:
```
gedit /etc/wvdial.conf
```
You should then see something like this:
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0

[Dialer netconnect]
Username = **( Add your # Number here)**
Password = **( Add your # number here)**
Phone = ###
Stupid Mode = 1
Inherits = Modem0
```
Then once you have edited the configuration file accordingly, you can try to connect again by running:
```
wvdial netconnect
```

---

### Post by one_nz on 2010-02-15
ok i will try that

---

### Post by one_nz on 2010-02-15
it didn't work....

---

### Post by GeorgeVita on 2010-02-16
Hi **one_nz**, some ideas:

**>** Ask your provider for the proper username/password. Searching I found the [following]("http://help.netzero.net/support/errors/error691.html#A"):> A. Are you entering your Member ID and Password correctly?
Ensure that you are entering your NetZero Member ID and Password correctly. **Note that your Member ID is everything to the left of the @** symbol in your email address. For example, the **Member ID** for **bobjones**@netzero.com is **bobjones**. Remember that passwords are case-sensitive, so please ensure that your Caps Lock key is not active.
Be sure to enter your password all in lower case. If your password is not working, please ensure that your Caps Lock key is not active.
Note: If you forgot your password, remember that there is a Forgot my Password button on the Welcome screen.

**>** Add a line to your /etc/wvdial.conf file: ```
Stupid Mode = Yes
``` This will skip 'old fashioned' login and proceed to ppp.

If you still have problems, post your /etc/wvdial.conf file to check.

Regards,
George

---

### Post by walt.smith1960 on 2010-02-16
but doesn't NetZero (and Juno) require the use of their software which requires Internet Explorer, e.g. windows?  It seems like only dial-up ISP's that don't require "their" software will work with Linux. One national ISP that is reputed to work is copper.net.  There are others, the trick is to find an ISP with a local phone #. If you choose to switch ISP's you can still use your NetZero Email via their web based interface.

---

### Post by lavinog on 2010-02-16
> **walt.smith1960 said:**
> but doesn't NetZero (and Juno) require the use of their software which requires Internet Explorer, e.g. windows?  It seems like only dial-up ISP's that don't require "their" software will work with Linux. One national ISP that is reputed to work is copper.net.  There are others, the trick is to find an ISP with a local phone #. If you choose to switch ISP's you can still use your NetZero Email via their web based interface.

I have seen many posts in the past about netzero not supporting linux.

---

### Post by lkraemer on 2010-02-16
Try:
```

man pppconfig
man pppd

```

then try:
```

sudo pppconfig

```
and follow the menu items to add your username and password information for PAP/CHAP.

This might help too!
[http://www.linuxquestions.org/questions/slackware-14/netzero-628659/](http://www.linuxquestions.org/questions/slackware-14/netzero-628659/)

lk

---

### Post by one_nz on 2010-02-18
my apologies for not replying right away, but after the only person that replied (during the 1st day) i decided to switch my carrier. thanks 2 all those who tried to resolve this issue.:popcorn:

---

### Post by Bartender on 2010-02-19
Juno lost my business a coupla years ago because of their proprietary software and the requirement to connect via IE.

United Online (parent co. of Juno and Netzero) will continue to lose dial-up customers unless they pull their heads out.  Their business model appears to be unchanged from 15 years ago, when dial-up providers were competing to lock customers in and force them to accept advertising.  DSL and cable made their strategies obsolete and they still don't get it.

---

### Post by lavinog on 2010-02-19
The internet isn't really dial-up friendly anymore anyway.  In some cases it is cheaper to get DSL than have a dedicated phone line.  Some ISPs offer DSL without requiring phone service.  I have seen DSL for $19-$30  where a phone line usually costs $30 alone, plus $10 for dial-up.

---

