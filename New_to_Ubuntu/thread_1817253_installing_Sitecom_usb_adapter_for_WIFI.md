---
title: "installing Sitecom usb adapter for WIFI"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by Ruthi on 2011-08-03
Hi all,
I try to install this wifi-adaper.
I have this ubuntu system but i really know nothing about it.
I put the cd-rom with drivers in the DVD drive, then i go to
 > system >> add new software >> get soft ware from (other places)

probem starts here:
but Comp message: can not mount drive (it says it's drive E - but in windows, on the same comp (ex-boy friend had made 3 different compartments - windows, ubuntu and OSX, I usually use ubuntu)
says the drive is Drive D.

What's next?

thanks everybody!

---

### Post by gandaran on 2011-08-03
the adapter may already work out of the box on ubuntu, check first on the panel network icon if it detects networks and connects, if it doesn't then type this command on terminal to find out the wireless chipset and post the output so we can tell you the best way to install the driver.
```
lsusb
```

---

### Post by Ruthi on 2011-08-04
Hi Gandaran,
thanx for ur reaction.
Here are the results:
the net work does not recognize the adapter.
I enterd: lsusb in terminal (by the way - what does this command mean ?)
I got (when concerning the adapter):
Bus 001 Device 003 ID 0df60058 Sitecom Europe BV

whats next ?
thanx again
Ruthi

---

### Post by gandaran on 2011-08-04
> Bus 001 Device 003 ID 0df60058 Sitecom Europe BV
well, Ubuntu failed to identify the wireless chipset so I don't know what driver you will need.
one question, which ubuntu release do you have? 11.04?
now about the drivers in the cd, can you check if there's any folder or archive with linux drivers in the cd, if there is copy them to ubuntu desktop then extract the package, inside should be a readme file with install instructions, if you don't understand the instructions paste them here.

---

