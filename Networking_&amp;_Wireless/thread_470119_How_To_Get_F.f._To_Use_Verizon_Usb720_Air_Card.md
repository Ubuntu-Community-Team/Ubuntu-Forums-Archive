---
title: "How To Get F.f. To Use Verizon Usb720 Air Card"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by darth tinknocker on 2007-06-10
Does Any One Know How To Set Up The Verizon Usb720 Air Card For Feisty?

---

### Post by wilberfan on 2007-06-29
Please put me down as wanting to know the answer to this one, too!  :sad:

---

### Post by darth tinknocker on 2007-06-30
i know that this whole site is nuts about ubuntu but , in my 'putertastic opinion ....it's for the birds...or penguins .Xp is just fine for your basic computer needs (internet, games , multimedia), if you have good anti virus/ spyware and your not on skin sites or limewire, you really don't need to lose sleep over security. Anything more than the basics......spend the money and get a mac!  Besides my Aunt is the only person i know who pays for software!

---

### Post by raywjohnson on 2007-09-21
Posting this update to "give back" to the Ubuntu community!

I used the info here: [http://kenkinder.com/evdo-pc5740](http://kenkinder.com/evdo-pc5740) to get my Verizon USB720 to work on Feisty!

There were only two gotchas:

Remove the semi-colons from these two lines of the **ppp chat script**:  (NOTICE: except for the last semi-colon!!!)
```
remove these semi-colons
'' 'ATTEV1&F;&D2;&C1;&C2S0;=0S7=60'
'OK-ATTEV1&F;&D2;&C1;&C2S0;=0S7=60-OK-ATTEV1&F;&D2;&C1;&C2S0;=0S7=60-OK' 

BUT NOT THIS ONE! : 'AT+CSQ;D#777'
```

AND the device is /dev/ttyUSB0 (not /dev/ttyACM0)

That's it! Works great AND I am actually getting the speeds (762+) that I have been paying for. Windoz rarely reached that speed.


--RayJ

---

### Post by Dawayn on 2008-01-09
I am new to Linux and was able to get my USB720 working by doing the following:

(NOTE: I discovered for me I had to turn off my Intel Pro Wireless 3945 wireless card reboot with the card off for my USB720 to work.  I need to figure out how to get the 720 to work with the wireless card turned on.)  Nothing else besides the following.

1) Create a wvdial.conf file:

sudo wvdialconf

2) Edit the wvdial.conf file found in /etc and add the phone number,  password, and user name.  Make sure to remove the # comments markers from the phone, password, and user name lines.

gedit /etc/wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
#Phone = 
#Password = 
#Username = 


Save the wvdial.conf changes.

3) Connect and surf:

sudo wvdial

Wait while the modem dials and connects.  I see the following in my terminal

WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT#777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT#777
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial<Notice>: Don't know what to do!  Starting pppd and hoping for the best.
WvDial<Notice>: Starting pppd at Wed Jan  9 20:23:18 2008
WvDial<Notice>: Pid of pppd: 5966
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: local  IP address 75.216.86.116
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: remote IP address 66.174.26.4
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: primary   DNS address 66.174.92.14
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: secondary DNS address 66.174.95.44
WvDial<*1>: pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]

You should be able to surf now.  To disconnect use ctrl C combo.

Hope this helps someone.

---

