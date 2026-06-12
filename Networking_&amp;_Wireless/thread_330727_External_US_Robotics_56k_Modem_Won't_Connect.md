---
title: "External US Robotics 56k Modem Won't Connect"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by multanihl on 2007-01-03
Hi folks,

I just recently installed Ubuntu 6.10 on an old PIII that I'm trying to get some new life out of, and everything has worked fine except getting this old modem to work (it even gets along with a Win2k install next to it).  

I used wvdial to try and connect after I couldn't get the networking GUI to properly work, and it seems to hit a snag not on detecting the modem, but rather when I try to dial out.

I get back an error message saying that my ISP's phone number, user name, and password are all invalid!

Any idea why it would do that when it has no problem detecting and configuring the modem on ttyS0?  It seems like if I made it that far then I shouldn't have any more problems....

If it helps, our region (North Georgia, US) recently switched from 7- to 10-digit dialing (you have to punch in the area code regardless of where you're calling), although the modem seems to work fine under Win2k even with the new dialing scheme....  I wouldn't much care except that I intended this machine to be a much faster (OS-wise) and safer internet machine for the family, so its primary purpose isn't usable.  Any help is much appreciated.

---

### Post by NeilE888 on 2007-03-21
About setting up a dialup modem on Ubuntu 6.10

I'm new to this, so I'm just learning by trial and error - I hope this helps, but I don't know enough about the underlying system to be sure ... I had the same error messages and found something that worked.

I have installed Ubuntu (on an old machine, Pentium 3 with 256Mb ram) and found that I couldn't connect using an external (serial) dialup modem using the options described in the DialupModemHowto/SetUpDialer page. I am using a 3Com/US Robotics 56k professional message modem (although I tried with another model as well). It was detected OK and I tried both serial ports just in case.

I found that the $ sudo adduser USERNAME dip and dialout settings were already made and that the Networking section didn't work for me, so I tried the default settings in wvdialconf and still no luck. I moved on to the suggestions so that I could pon and poff; still no positive result. 

However, by following the advice to check man wvdial.conf, I used the settings suggested there and I could get the modem to connect satisfactorily using sudo wvdial, nothing else seemed to work.

The suggestion of setting up Modem Lights was attractive, but I couldn't find it amongst the options. When I right clicked on the top bar (as advised) I found that there was a similar offering (Modem Monitor), but that didn't work for me: I could set it in the top panel, but it didn't allow me to click into a connection .... even the one as configured with the man wvdial.conf settings (and now saved to wvdialconf).

So at present I can connect using wvdial (from a terminal window), but only by replacing the default setting found there by those from man wvdial.conf. 

I have subsequently tried the same thing under Ubuntu 6.06, and could use the Networking options to configure the external modem and activate it successfully (but there seemed to be an issue about losing the data on reboot).

---

