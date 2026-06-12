---
title: "No carrier using hsfmodem"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by uganda on 2008-11-08
I am new to Linux/Ubuntu (want to switch from Windows) and have installed 8.10 yesterday and finally set up wvdial and pppconfig, but apart from 2-3 times where I could dial up, I am getting no carrier, even though the Windows laptop next to it can always dial up using the same cable (plug out of the Ubuntu laptop and into the Windows laptop to try).

Yesterday, I got the free hsfmodem driver to work, so I paid $20 for the full, fast version, thinking everything's sorted now and I can finally switch to Linux (I've had a gutsful with Windows, lost some data last week - last straw!).

It worked a few times - here's the wvdial output:

--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L1DT086727234
--> Waiting for carrier.
ATM1L1DT086727234
CONNECT 115200 
--> Carrier detected.  Waiting for prompt.
** Lucent APX Terminal Server **
...and so on, login, etc...


but now I always get

--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT086727234
--> Waiting for carrier.
ATDT086727234
NO CARRIER
--> No Carrier!  Trying again.

...there's a very long wait before the "NO CARRIER".

The other main difference is, when it worked, I could hear the dial tone and the dialing, but now I can't hear it do anything.  I have not changed the config since, here's wvdial.conf:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/modem
ISDN = 0
Phone = 086727234
Password = ***
Username = ***

I have tried several changes: connect speed, "stupid mode", wait/no wait for dial tone, etc. but no change.

Any help much appreciated - even though the Ubuntu install was quick & easy, I've been struggling with getting the modem working for 8 hours now and it's getting very tiring - still committed to getting rid of Windows, but I (obviously ;-) need the internet (dial-up access only).

Many thanks,
Tom

PS: I have emailed Linuxant, but since it's weekend now & besides I'm not sure whether it's their issue, since it did work 2-3 times just fine, I'm posting the request for help here.

---

### Post by uganda on 2008-11-30
Fwiw, I had to give up on the internal Winmodem and bought a PCMCIA modem, which works fine - see [http://ubuntuforums.org/showthread.php?p=6282592#post6282592](http://ubuntuforums.org/showthread.php?p=6282592#post6282592)

---

### Post by magli on 2009-02-25
uganda,

what did linuxant tell you?

I am in the same situation as you: the modem was working fine, and then suddenly stopped working with the exact same symptons as you described.

There has to be a solution to this.

---

### Post by magli on 2009-02-25
The problem appears to be with kernel 2.6.27-11, which was installed with an update. I reverted back to kernel 2.6.27-7, and the modem is working again.

---

