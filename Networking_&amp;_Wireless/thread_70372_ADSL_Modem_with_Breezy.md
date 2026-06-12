---
title: "ADSL Modem with Breezy"
date: 2005-09-29
forum: Networking &amp; Wireless
---

### Post by ~J~ on 2005-09-29
Hi,

I've just downloaded Breezy Live Preview and wanted to know if (and how) I can connect to the net with my ADSL Voyager 100 USB Modem.

The network connections has a wireless, ethernet and modem (dialup) but I can't see any option to add the ADSL modem.

Checking the hardware settings, it does clearly show that I have a USB ADSL modem attached and lists all the technical specs, so it's picked it up fine (I think/hope).

Are they any simple stages/tips I can use to connect?

I'll be installed Breezy on Saturday but obviously need net-access for work, etc.

Any help I'd really appreciate it.

---

### Post by adwait on 2005-09-29
Try this if your provider uses PPPoE:
```

sudo pppoeconf

```

If your router automatically connects, then just enter the private ip of your router in the /etc/resolv.conf file
[code
sudo vi /etc/resolv.conf
[/code]

Add the line:
```

nameserver <private ip of router>

```

---

### Post by ~J~ on 2005-09-30
Hi,

Thanks for that.  I've tried what you suggested, but no joy I'm affraid.

I did however try the instructions regarding the RP-PPPoE3.6 file that is on the Ubuntu FAQ, and whilst everything went well, when I actually came to run the shortcut from the Internet menu nothing happened.

I did tried the gksudo from a terminal and got this message...

Running ./configure...
checking for gcc... no
checking for cc... no
checking for cc... no
checking fo cl... no
configure: error: no acceptable c compiler found in $PATH
see 'config.log' for more details.
Oops! It looks like ./configure failed.

Any ideas what that means (apart from the obvious - :p )

---

