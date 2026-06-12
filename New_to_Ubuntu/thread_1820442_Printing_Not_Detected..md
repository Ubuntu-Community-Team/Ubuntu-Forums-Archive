---
title: "Printing Not Detected."
date: 2011-08-07
forum: New to Ubuntu
---

### Post by Snowboi on 2011-08-07
I feel like a complete idiot... But i was unable to get a printer setup on ubuntu. :( 
(its HP-Deskjet-3050-J610-series)

I installed hplip and tried to configure the printer but it could not detect it. Its a wireless printer but i do not have wireless internet so im trying to set it up via usb.

When i ran

```
hp-check
```

In the terminal it gave me the 

```
HP-Deskjet-3050-J610-series
---------------------------
Type: Unknown
Device URI: usb://HP/Deskjet%203050%20J610%20series?serial=CN15A3B6XC05HX
PPD: /etc/cups/ppd/HP-Deskjet-3050-J610-series.ppd
PPD Description: HP Deskjet 3320 hpijs, 3.10.2rc1.9
Printer status: printer HP-Deskjet-3050-J610-series is idle.  enabled since Fri 05 Aug 2011 11:28:25 AM EDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
```

(NOTE : THE ABOVE IS CUPS (I DON'T NEED CUPS AS IT IS FOR WIRELESS)

This is really what troubles me, regardless of the printer being on or off.

```
--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

```

I have all the required dependencies installed.

Seems my printer is not supported...
```
[COLOR="Red"]error: Unsupported model: Deskjet_3050_J610_series[/COLOR]

```

But iv seen other people use the printer i have and it seems to have worked and iv tried reading through other topics but have found none to be an effective solution.

And one more thing...

```
[COLOR="Red"]error: User needs to be member of group 'lp' to enable print, scan & fax.[/COLOR]
[COLOR="Lime"]User member of group 'lpadmin'.[/COLOR]

```

What does the above mean?

(in all i want the printer to function properly it is a printer/scanner/copier.)

---

### Post by fdrake on 2011-08-07
did you try 
```
sudo apt-get install hplip-cups
```

---

### Post by Snowboi on 2011-08-07
> **fdrake said:**
> did you try 
```
sudo apt-get install hplip-cups
```

Yup, i have tried it and its still not found.

---

### Post by jtarin on 2011-08-07
> **Snowboi said:**
> ```
[COLOR="Red"]error: User needs to be member of group 'lp' to enable print, scan & fax.[/COLOR]
[COLOR="Lime"]User member of group 'lpadmin'.[/COLOR]

```

What does the above mean?

(in all i want the printer to function properly it is a printer/scanner/copier.)[Add user to "lp" group..]("https://help.ubuntu.com/community/AddUsersHowto")
Also issue the command ```
lsusb
``` in the terminal and copy and paste the results here. This will allow us to see what USB devices are detected.

---

### Post by xpasaway on 2011-08-07
hi gud morning.

i have the same problem here. my printer is hp laserjet 1020. we also try to install cups for printing support in ubuntu but i observe that every time, for example after office hours, usually the computer will be shut down. then in the next day, the printer is no functioning anymore. its because the driver is gone.

i installed fresh ubutu 11.04 and still the problem is there.

i need help.

thanks.

---

### Post by jtarin on 2011-08-07
> **xpasaway said:**
> hi gud morning.

i have the same problem here. my printer is hp laserjet 1020. we also try to install cups for printing support in ubuntu but i observe that every time, for example after office hours, usually the computer will be shut down. then in the next day, the printer is no functioning anymore. its because the driver is gone.

i installed fresh ubutu 11.04 and still the problem is there.

i need help.

thanks.
Please start your own thread about your particular problem. Do not hi-jack threads as it causes confusion between thos that are helping and those being helped. Thank you.

---

### Post by Snowboi on 2011-08-07
> **jtarin said:**
> [Add user to "lp" group..]("https://help.ubuntu.com/community/AddUsersHowto")
Also issue the command ```
lsusb
``` in the terminal and copy and paste the results here. This will allow us to see what USB devices are detected.

First time running i did not have the printer detected even when it was on. I added lp to my groups then i ran 

```
lsusb
```

and got the printer detected on
```
Bus 001 Device 008: ID 03f0:9311 Hewlett-Packard 

```

Somehow it still cannot detect the printer in hplip but ubuntu detects the printer (it always did) and i cannot print a test page. I tried printing or scanning and it did not work.

I tried to do a manual discovery but it did not detect it?
what would be the proper format to input manual discovery?

---

### Post by jtarin on 2011-08-07
[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

---

### Post by Snowboi on 2011-08-08
> **jtarin said:**
> [https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

Results

```
owner@ubuntu:~$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 3.10.2)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Error: "/var/tmp/kdecache-owner" is owned by uid 1000 instead of uid 0.
(11617) KIconCache::Private::themeDirsChanged: Theme directory has been modified
Searching... (bus=usb, search=(None), desc=0)
[COLOR="Red"]error: No devices found on bus: usb[/COLOR]
Searching... (bus=usb, search=(None), desc=0)
[COLOR="Red"]error: No devices found on bus: usb[/COLOR]

Done.
owner@ubuntu:~$ 

```

*Note : The error is caused by a KDE package installation issue (removed KDE for the most part)

And

```
sudo hp-check -r
```

gave

```
--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.


```

and

```
-----------------
| USB I/O SETUP |
-----------------

Checking for permissions of USB attached printers...

HP Device 0x9311 at 001:010: 
    Device URI: hp:/usb/Deskjet_3050_J610_series?serial=CN15A3B6XC05HX
[COLOR="Red"]error: Unsupported model: Deskjet_3050_J610_series[/COLOR]

---------------
| USER GROUPS |
---------------

root

[COLOR="Red"]error: User needs to be member of group 'lp' to enable print, scan & fax.
error: User needs to be member of group 'lpadmin' to manage printers.[/COLOR]

-----------
| SUMMARY |
-----------

[COLOR="green"]No errors or warnings.[/COLOR]


```

How can i change the root group ?
i was able to change the admin (owner) group but cannot find a way to change the root to add lp and lpadmin ?

---

### Post by jtarin on 2011-08-08
Root is always a member of all groups.

> error: User needs to be member of group 'lp' to enable print, scan & fax.
error: User needs to be member of group 'lpadmin' to manage printers.

This is saying that "user" (you....your username) needs to be a member of both those groups. There is a graphical way to do this in 10.04, 10.10, but I don't use 11.04 so I cant tell you. In my version its in the MainMenu>System>Administration>Users and Groups(something worded as such)

[Which groups do you(username) belong to?]("http://www.cyberciti.biz/faq/which-groups-do-i-belong-to/")

---

### Post by Snowboi on 2011-08-08
> **jtarin said:**
> Root is always a member of all groups.


This is saying that "user" (you....your username) needs to be a member of both those groups. There is a graphical way to do this in 10.04, 10.10, but I don't use 11.04 so I cant tell you. In my version its in the MainMenu>System>Administration>Users and Groups(something worded as such)

[Which groups do you(username) belong to?]("http://www.cyberciti.biz/faq/which-groups-do-i-belong-to/")

I am already in lp and lpadmin

```
owner@ubuntu:~$ groups
owner adm [COLOR="Cyan"]lp[/COLOR] dialout cdrom plugdev [COLOR="Cyan"]lpadmin[/COLOR] admin sambashare printer

```

Why does it give me this error? (i ran in root)

So there is no possibility that the root user cannot be in lp and lpadmin?

---

### Post by jtarin on 2011-08-08
When you get your permissions sorted out I am going to recommend setting up in CUPS.

[Here's a link for the scanner part]("https://help.ubuntu.com/community/ScanningHowTo"), which you might read as it's linked to your printing setup slightly.

---

### Post by jtarin on 2011-08-08
> **Snowboi said:**
> I am already in lp and lpadmin

```
owner@ubuntu:~$ groups
owner adm [COLOR="Cyan"]lp[/COLOR] dialout cdrom plugdev [COLOR="Cyan"]lpadmin[/COLOR] admin sambashare printer

```

Why does it give me this error? (i ran in root)

So there is no possibility that the root user cannot be in lp and lpadmin?
Root is a member of **al**l groups, automatically. 
Run the command as normal user....not root.

---

### Post by fdrake on 2011-08-08
> **jtarin said:**
> Root is a member of **al**l groups, automatically. 
Run the command as normal user....not root.

actually he is running as a normal user . See the $ symbol... his user-name is "Owner".
this may be caused by a conflict of similar programs.
try :
```

sudo apt-get remove hp*
wget http://prdownloads.sourceforge.net/hplip/hplip-3.9.12.run
sh hplip-3.9.12.run
hp-setup

```

---

