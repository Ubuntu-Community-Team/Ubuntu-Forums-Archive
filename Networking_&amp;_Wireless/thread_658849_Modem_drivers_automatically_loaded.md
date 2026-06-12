---
title: "Modem drivers automatically loaded"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by mickeyWD on 2008-01-05
Hi all,
I'm using restricted driver to an Intel internal modem as suggested by Ubuntu  Gutsy system tray icon.
Now at startup tree modem driver are loaded: atiixp, via and intel8x0m.
Only the latest is needed reading the lspci output.

I don't know if drivers get resourse when loaded but 
wvdial can't access the modem through the serial port 
and
slmodemd can't access the alsa hw:1,0 device for "resource or device busy"

I've tried blacklisting in /etc/modules/blacklist-modem the unneeded voices but at startup all the modules are listed.

However, ati and via modules can manually removed but rmmod intel8x0m, obviously, result in a busy module that can't be removed alsa after /etc/init.c/alsa-utils has been stopped.

How to get rid? :mad:

---

### Post by mickeyWD on 2008-01-05
```
laj@little:~$ sudo /etc/init.d/alsa-utils stop
laj@little:~$ sudo rmmod snd_intel8x0m
ERROR: Module snd_intel8x0m is in use

```

How I can see who is using this module?

---

### Post by mickeyWD on 2008-01-05
Ok, now I've been cleared somethings.
slmodem**d** is always running and the init script automatically loaded the ati, intel and via drivers. Now only the intel needed by my own hardware.

This daemone create the virtual port without problems.
So I think the message ```
WvModem<*1>: Cannot get information for serial port.
``` is not relevant for slmodem.


So I have to found the right inizialization string:
without the X3 command results in NO DIALTONE ( I know is an Italian requirement )
Is  ```
ATQ0 X3 V1 E1 S0=0 &C1 &D2 +FCLASS=0
``` good?

I understand that the modem uses the phone line but not in the right way.
If I compose my mobile number, can I expect to ear it ring? but not at this stage.

I hope someone can confirm this and explain me how to connect without wvdial but simply accessing the Network Administration tools.

---

### Post by mickeyWD on 2008-01-05
What's funny connetction: the 56K!!! WOW :guitar:

I'm connected with wvdial also with gnome-ppp interface but still waiting for autentication .:confused:

:)

```
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 X3 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 X3 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATM1L3DT0825480000
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATM1L3DT0825480000
WvDial Modem<*1>: CONNECT 34667
WvDial Modem<*1>: User Access Verification
WvDial Modem<*1>: Username: 
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: Username: 
WvDial<*1>: Looks like a login prompt.

```

furthermore gnome-ppp add M1L3 calling the provider and I don't know where is its configuration files.

Most important,
I don't ear nothing about the communication. Is it normal?

---

