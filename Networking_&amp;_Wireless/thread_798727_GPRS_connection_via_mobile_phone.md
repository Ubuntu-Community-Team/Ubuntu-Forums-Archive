---
title: "GPRS connection via mobile phone"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by Frila on 2008-05-18
[FONT="Arial"]My computer is connected via bluetooth to a Sony Ericsson P990i cellular phone. Bindings and such things are ok with Modem=/dev/rfcomm0.

/etc/wvdial.conf looks like:

[Dialer Defaults]
Modem=/dev/rfcomm0
Init=ATZ
Phone = *99#
Username = internet
Password = internet
New PPPD = Yes

/etc/bluetooth/rfcomm.conf
rfcomm0
{
bind yes;
device 00:12:EE:B4:04:73;
channel 7;
comment "SE P990i";
}

When I dial with wvdial I get connected but no access to Internet. 
Extract from wvdial connection:

...
--> remote IP address 10.64.64.64
--> primary DNS address 10.0.0.1
...

This seems to be some defaults but not working with my mobile phone Internet. It works fine to brows Internet directly from the phone when not working as a GPRS modem.

 

All tips and trix are welcome. This must be possible to solve.[/FONT]

---

### Post by mishivia on 2008-11-28
Did you ever resolve this? If so can you please explain how. Other people may have run into the same problem. (See how many times this post have been viewed) I am a newbie, but I always try to help out others as much as possible or at least point them in a helpful direction.

Nevermind, I solved my issue and will be posting a nice how to for connecting to att gprs through bluetooth.

---

