---
title: "[SOLVED] ndisgtk Won't Install"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by texasnomad on 2008-12-13
I absolutely cannot get ndiswrapper installed on this machine.  I've read what seems like every post and keep running into a wall of errors.

I tried downloading ndisgtk... but that won't let me install either.  It says "Error: Dependency is not satisfiable ndiswrapper-utils

I've gone through instructions to install the wrapper and get the same response in the terminal when running ndiswrapper.  It always replies ndiswrapper utils not found!

Please help.

---

### Post by unutbu on 2008-12-13
Boot Ubuntu from your hard disk.
Pop in your Ubuntu LiveCD.
Open a terminal (Applications>Accessories>Terminal) and type
```

sudo apt-cdrom add     # This tells Ubuntu that your CD is a repository
sudo apt-get update    # This makes Ubuntu aware of the packages available on the CD
sudo apt-get install ndiswrapper-utils-1.9
```

ndisgtk is not necessary. The following commands should install the driver:
```

sudo depmod -a
sudo modprobe -v ndiswrapper
sudo ndiswrapper -i /path/to/wireless_driver.inf

``` (Change /path/to/wireless_driver.inf to the appropriate path)

However, if you want to try ndisgtk, type
```

sudo apt-get install ndisgtk
```

---

### Post by HotShotDJ on 2008-12-13
You haven't told us HOW you've tried to install it.  Are you using Ubuntu's built in installation system (Synaptic Package Manager) or are you using methods that you are trying to import from the world of Windows (downloading software and then trying to install it)?

If you did NOT use either apt-get from the command line or Synaptic Package Manager, then you should UNDO everything you did and then open System --> Administration --> Synaptic Package Manager.  Then just type ndis in the Quick search box.  Check off ndisgtk, ndiswrapper-utils-1.9 and ndiswrapper-common.

Let Ubuntu's package management system do the work for you.  Manually downloading software and then trying to install it should be the last resort, not your first instinct.

EDIT:  If you don't have Internet connectivity with Ubuntu at all (for example, via the Ethernet port) then you will have to use your Ubuntu CDROM.  However, you do NOT need to use a terminal.  It can be accomplished exclusively using the GUI interface.  After you open Synaptic Package Manager, click on Settings --> Repositories.  Near the bottom of the Ubuntu Software tab, just check off "Cdrom with Ubuntu 8.10 'Intrepid Ibex'"  When you click on close, it will read the CDROM (make sure it is in your CDROM drive first) and then you'll be able to install ndiswrapper.

Of course, using the terminal is available if that is your preference.  Both methods work.

EDIT2: I almost forgot, there is ALSO Add/Remove under the Applications menu. Just make sure the "show" box is set to  All Available Applications, then you can just search for ndis and then select "Windows Wireless Drivers"

---

