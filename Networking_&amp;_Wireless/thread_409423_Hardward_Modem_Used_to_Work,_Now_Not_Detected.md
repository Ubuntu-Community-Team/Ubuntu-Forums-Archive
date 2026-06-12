---
title: "Hardward Modem Used to Work, Now Not Detected"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by klytu on 2007-04-14
Really frustrating problem, but not a critical one. I have a hardware modem (not a winmodem) connected at /dev/ttyS1. Used to work with no problems in Breezy and Dapper; in fact I used to connect to the internet with it before I got DSL a little over a year ago. I used the modem to fax from Ubuntu within the last 6 months. While trying to help a friend with a modem issue, I noticed that my modem was not being detected:

```
sudo wvdialconf /etc/wvdial.conf
Password:
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S3   S4   S5   S6   S7   S8   S9   S10
Modem Port Scan<*1>: S11  S12  S13  S14  S15  S16  S17  S18
Modem Port Scan<*1>: S19  S20  S21  S22  S23  S24  S25  S26
Modem Port Scan<*1>: S27  S28  S29  S30  S31  S32  S33  S34
Modem Port Scan<*1>: S35  S36  S37  S38  S39  S40  S41  S42
Modem Port Scan<*1>: S43  S44  S45  S46  S47


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?
```


Still works perfectly under Windows, every time. I thought it was just an Ubuntu issue, but my modem is also no longer detected by an older semi-permanent installation of Knoppix - where it used to work as well. I kept thinking this was a hardware issue, but then why does the modem always work with Windows? Only thing I have updated in the last year that would affect all OS's I use is that I updated my BIOS. But I am pretty sure I used the modem under Linux since then.  This really has me stumped. Any one have any ideas?

---

### Post by klytu on 2007-04-14
After 3 hours of frustration I found that ...

The modem wasn't being detected because it shared the same IRQ as my ethernet card. I had changed the IRQ of the modem in the BIOS because of a conflict with a UPS device. I did this months ago and totally forgot about it; and the setting was in an obscure area of the AWARD BIOS under power management.  Windows XP must have automagically resolved the conflict. (Now I wonder why Linux didn't do the same or if there is a kernel option to do something similar ...) Anyway, this information might help someone who can't figure out why a hardware modem isn't being detected.

---

