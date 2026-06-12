---
title: "Help installing windows driver with Ndiswrapper"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by jonkanon on 2007-08-29
Hello, this is a somewhat n00b question but although I've spent hours I'm lost.
I'd really like some help installing my GPLUS driver using Ndiswrapper. My card is DWL-G650+ and this is said to work.

[I]jon@jon-laptop:~$ sudo ndiswrapper -i ~/DWL/gplus.inf
Password:
driver gplus is already installed
jon@jon-laptop:~$ ndiswrapper -l
gplus : invalid driver!
[/I]

I read about deactivating the current linux driver, but how is this done?

Another message I had in terminal:

*jon@jon-laptop:~$ sudo ndiswrapper -i GPLUS.inf*
[I]installing gplus ...
couldn't open GPLUS.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.[/I]

I tried to uninstall ndiswrapper and install again, now I don't know... I'm lost. 
It's probably quite simple. Anyone?

EDIT: I could also add that I tried the interface "Windows Wireless Drivers" but nothing ever appears in the "Currently Installed Windows Driver" box. I get no error message, but installation seems to fail.

---

### Post by mahasmb on 2007-08-29
Here's a long shot. I'm no expert, I had the same problem and so far I've at least been able to install my driver properly. Try this:

[http://ubuntuforums.org/showthread.php?p=3272634#post3272634](http://ubuntuforums.org/showthread.php?p=3272634#post3272634)

---

### Post by Steve1961 on 2007-08-29
Uninstall the driver by typing ndiswrapper -e name-of-driver

Then try a driver from one of these links for your card:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/)

---

### Post by jw5801 on 2007-08-29
[Please try not to double post](http://ubuntuforums.org/showthread.php?t=537578) :p
This post looked surprisingly familiar when I had a look in, I've answered your question in your first post so look there.

---

