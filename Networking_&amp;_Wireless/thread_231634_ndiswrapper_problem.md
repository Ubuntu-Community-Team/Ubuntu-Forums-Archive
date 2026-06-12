---
title: "ndiswrapper problem"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by grendel38 on 2006-08-07
My wireless quit working.  It worked fine after I upgraded to dapper drake, but quit after a recent upgrade I installed

I've been trying to get it to work again without success.

I use a dlink dwl-650 rev. m wireless card in a Panasonic CF-71 notebook

I've tried using ndiswrapper.  I located the correct driver, and downloaded it.  When I use the graphical windows wireless drivers program with gnome to install the driver nothing happens.  I select the file and hit install, but no installed drivers ever show up.  I tried listing the installed drivers in a terminal with 

ndiswrapper -l

and get "no installed drivers" as output.

I tried installing the driver using the command line, but that doesn't seem to work either.  To install, I enter

ndiswrapper -i "filename"

but that doesn't result in any installed drivers either.

I got the driver from the dlink webpage and am confident I have the correct driver -- the id matches perfectly.

what am I doing wrong?

---

### Post by phansiizwe on 2006-08-07
What exactly is the output of ndiswrapper -i "filename" ?

You might try the following sequence:

```
sudo ndiswrapper -i driver.inf
sudo ndiswrapper -l
sudo depmod -a
```

If, after you get something like: 'driver installed, hardware present' and no errors occurs after 'sudo depmod -a', type:

```
sudo modprobe ndiswrapper
```

This should load the ndiswrapper module, check for any errors with:

```
gedit /var/log/messages
```


I hope this brings you a bit further....

---

