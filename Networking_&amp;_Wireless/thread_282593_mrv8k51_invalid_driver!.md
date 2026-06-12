---
title: "mrv8k51 invalid driver!"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by johnny9794 on 2006-10-23
I installed the driver for my D-Link DWL-G510 and i get invalid driver...

johnny@linux-box:~$ sudo ndiswrapper -i /Home/johnny/Desktop/WinXP/mrv8k51.inf
Installing mrv8k51
couldn't copy /Home/johnny/Desktop/WinXP/mrv8k51.inf at /usr/sbin/ndiswrapper line 135.
johnny@linux-box:~$ sudo ndiswrapper -l
Installed ndis drivers:
mrv8k51 invalid driver!

I been on this mission for three days. I uninstalled the driver,reinstalled driver, uninstalled ndiswrapper and then reinstalled, uninstalled ubuntu and then reinstalled ubuntu... and all the results come back the same...
could someone please help me. Maybe i am doing something wrong.
Thanx

---

### Post by Malakia on 2006-10-23
Make sure that you are using the right driver. You can check the ndiswrapper website to make sure. If it is the right one try using the driver for Windows 98.

---

### Post by johnny9794 on 2006-10-24
nope no luck i have the right driver I downloaded it from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) and am using the Win98 Driver.

johnny@linux-box:~$ sudo ndiswrapper -i /Home/johnny/Win98/mrv8k51.inf
Installing mrv8k51
couldn't copy /Home/johnny/Win98/mrv8k51.inf at /usr/sbin/ndiswrapper line 135.
johnny@linux-box:~$ sudo ndiswrapper -l
Installed ndis drivers:
mrv8k51 invalid driver!
johnny@linux-box:~$ sudo ndiswrapper -e mrv8k51
johnny@linux-box:~$ sudo ndiswrapper -i /Home/johnny/Win98/mrv8k51
Installing mrv8k51
couldn't copy /Home/johnny/Win98/mrv8k51 at /usr/sbin/ndiswrapper line 135.johnny@linux-box:~$ sudo ndiswrapper -e mrv8k51

:S

---

