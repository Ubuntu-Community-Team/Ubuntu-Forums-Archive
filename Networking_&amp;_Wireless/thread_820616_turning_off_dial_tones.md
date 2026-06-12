---
title: "turning off dial tones"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by King Buttons I on 2008-06-06
I have set up my modem with wvdial and it dials out with a lot of noise. Does anyone know how to turn the dial tones off?

---

### Post by Mark_in_Hollywood on 2008-06-06
Add the following line(s) into /etc/wvdial.conf


 M0L0 (those are zeroes not ohs) to your dial up command string (ie. make it look like ATM0L0DT instead of ATDT), and while you're at it, add a W2 before the DT to get the correct connect speed returned.

Please find the red text THREAD TOOLS at the top of this thread and mark it as SOLVED is this is enough.

---

### Post by King Buttons I on 2008-06-08
Mark_in_Hollywood
I went to add the stuff you suggested into wvdial.conf file and cant figure out where to add them. I have uploaded a copy of the file could you maybe show me where to add them?
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttySM0
ISDN = 0
 Phone = 
 Password = 
 Username = 
 Carrier Check=no
```

---

### Post by Mark_in_Hollywood on 2008-06-08
Glad to help:

Please have a look at:

wvdial.conf(5)
[http://linux.die.net/man/5/wvdial.conf](http://linux.die.net/man/5/wvdial.conf)

which is the manual pages for wvdial.conf

for your ease, I'm posting some of that page:

[Dialer Defaults]
Modem = /dev/ttyS2
Baud = 57600
Init = ATZ
Init2 = AT S11=50
Phone = 555-4242
Username = apenwarr
Password = my-password
**ATM0L0DT**

[Dialer phone2]
Phone = 555-4243

[Dialer shh]
Init3 = ATM0

[Dialer pulse]
Dial Command = ATDP

so, in your case add the line under dialer defaults. I haven't been on dial-up for two years now, and may have forgotten some of this, but it should work. If not, try 

Init3 = ATM0L0DT

Are you using Gnome's Network Manager for Modem/Dial-Up? It has an easier way to turn the modem screech up, down and off, if I remember it rightly.

---

