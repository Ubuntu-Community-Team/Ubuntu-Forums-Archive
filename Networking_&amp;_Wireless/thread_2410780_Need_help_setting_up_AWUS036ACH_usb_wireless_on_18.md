---
title: "Need help setting up AWUS036ACH usb wireless on 18.04"
date: 2019-01-20
forum: Networking &amp; Wireless
---

### Post by david_ford3 on 2019-01-20
I just bought an Afta awus036ach usb wireless adapter for my box, based on some recommendations I got online, saying it was well supported by Linux.  No directions for Linux in the box, but they do provide a driver.

Not knowing what to do, and based on details in another thread from last year, I've tried this:
```

sudo apt-get update && sudo apt-get install rtl8812au-dkms
```

then rebooted.  No wireless connectivity.

 If there is more I have to do after that, I've not been able to find any directions.

lsusb gives me this:
> 
Bus 003 Device 002: ID 0bda:8812 Realtek Semiconductor Corp. RTL8812AU 802.11a/b/g/n/ac WLAN Adapter

I've read that the apt-get route only works on Kali, which I might be switching to if I can't get this to work.


I just retried installing again, with the above command (since I didn't save off the original install output), and got the following message:


```

sudo apt-get update && sudo apt-get install rtl8812au-dkms
```
> Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]        
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]                 
Fetched 247 kB in 1s (228 kB/s)    
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rtl8812au-dkms is already the newest version (4.3.8.12175.20140902+dfsg-0ubuntu8).
The following packages were automatically installed and are no longer required:
  app-install-data apt-xapian-index gconf-service gconf-service-backend gconf2 gconf2-common
  libgconf-2-4 libgfortran3 libgtkmm-3.0-1v5 libmodplug1 libnih-dbus1 python-apt python-aptdaemon
  python-aptdaemon.gtk3widgets python-attr python-automat python-click python-colorama
  python-constantly python-cups python-debian python-defer python-dirspec python-hyperlink
  python-incremental python-openssl python-pam python-piston-mini-client python-pyasn1-modules
  python-serial python-service-identity python-twisted-bin python-twisted-core python-twisted-web
  python-xapian python-xdg python3-piston-mini-client python3-xapian software-center-aptdaemon-plugins
Use 'sudo apt autoremove' to remove them.


Anybody have any pointers?

---

### Post by jeremy31 on 2019-01-20
Post results from terminal for ```
mokutil --sb-state; dkms status
```

---

### Post by david_ford3 on 2019-01-20
Hi Jeremy,

```
mokutil --sb-state; dkms status
```
SecureBoot disabled
Platform is in Setup Mode
rtl8812au, 4.3.8.12175.20140902+dfsg, 4.15.0-43-generic, x86_64: installed

---

### Post by jeremy31 on 2019-01-20
Go into BIOS settings and see if there is something there about custom or standard Secure Boot, somehow you must have deleted some keys to get it in setup mode.  That prevents dkms from working and I don't know why

---

### Post by david_ford3 on 2019-01-20
I didn't see anything.  Let me try and research my board.  It's a Gigabyte B85M-DS3H-A, lga-1150.  Older board.  It was old technology when I built it about 3 years ago.

---

### Post by david_ford3 on 2019-01-20
Bios is not an area where I'm savvy, so I doubt I'd have changed much if anything.  There is a spot to choose Windows 8 or Other OS.  And Windows 8 is the option that will even show you the Secure Boot settings. Possible I changed that when trying to set the machine up, since I knew I was installing Ubuntu.   Sure enough, after changing setting to Windows 8,  I see where Secure Boot is set to Disabled, but there is nothing that will let me change it that I can see.  I just read that Other OS is the default setting.

---

### Post by david_ford3 on 2019-01-20
ok, I looked at another thread and found and ran this:

sudo dkms autoinstall

, then unplugged my cable.  I'm able to reach the internet.

SecureBoot is still disabled.

---

### Post by david_ford3 on 2019-01-20
I thought it failed when I moved it and rebooted.  The unit was not plugged in.  All working.

---

