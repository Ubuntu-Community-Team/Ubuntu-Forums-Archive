---
title: "HP printer problem."
date: 2010-02-27
forum: New to Ubuntu
---

### Post by philinux on 2010-02-27
HP 4680 all in one printer works just fine but at switch on starts xsane. 

Then have to close about 3 windows and the hplip monitor shows a failed scan job. Even though a scan was not asked for.

Any way to disable this annoying behaviour.

---

### Post by arochester on 2010-02-27
Have you checked that Xane isn't in the startup/autostart menu?

---

### Post by Spiritof76 on 2010-02-27
I have the same printer but haven't observed the same problems, or that I understand what your issues are.
IS it only a problem when you turn the printer on? You might cosider not shutting it off.  Mine lives in a closet and burns very little electricity when in standby.    
How are you communicating to the printer?  mine is hooked up through WIFI If you are hooked up via USB, you might concider hooking it up through your nework.

Best of Luck

---

### Post by philinux on 2010-02-27
> **arochester said:**
> Have you checked that Xane isn't in the startup/autostart menu?

First thing I checked. ;)

---

### Post by philinux on 2010-02-27
> **Spiritof76 said:**
> I have the same printer but haven't observed the same problems, or that I understand what your issues are.
IS it only a problem when you turn the printer on? You might cosider not shutting it off.  Mine lives in a closet and burns very little electricity when in standby.    
How are you communicating to the printer?  mine is hooked up through WIFI If you are hooked up via USB, you might concider hooking it up through your nework.

Best of Luck


Problem occurs only when switching on. Connected via usb.

---

### Post by JKyleOKC on 2010-02-27
> **philinux said:**
> Then have to close about 3 windows and the hplip monitor shows a failed scan job. Even though a scan was not asked for.Sorry I have no idea how to make it stop, but you can cut the number of windows to close from 3 to 1 by just closing the main xsane window; the other two then close automatically. The one to close is the one with all the option buttons; on my system it's at the top left corner of the screen.

This may help reduce the annoyance level until someone more knowledgeable comes along to tell you how to make it stop.

---

### Post by steveneddy on 2010-02-27
Having not encountered this issue myself while using HP printers, you may try installing [HPLIP from the website]("http://hplipopensource.com/hplip-web/index.html") instead of using the one from the repos. Make sure that you uninstall the repo version before installing the version from the site.

If you are on a network you also might try running the printer through the network instead of the USB port.

---

### Post by philinux on 2010-02-27
> **steveneddy said:**
> Having not encountered this issue myself while using HP printers, you may try installing [HPLIP from the website]("http://hplipopensource.com/hplip-web/index.html") instead of using the one from the repos. Make sure that you uninstall the repo version before installing the version from the site.

If you are on a network you also might try running the printer through the network instead of the USB port.

This particular pc is using 8.04 LTS so I had to install the HP website version.

---

### Post by bumanie on 2010-02-27
Hi Phil, I had a similar (but not the exact same) issue with 9.04 and a HP printer. I went through cups debugging, tried the hplip driver from HP linux site to no avail. In the end, I uninstalled the printer and then went through Administration --> Printing and chose "new" - ubuntu searched for the driver and now all works fine. Hope it is that simple to fix your issue. By the way, this seemed to have happened after an update, the printer had previously worked fine. Try uninstalling and then reinstalling the printer and allow ubuntu to search for the driver.

---

### Post by philinux on 2010-02-28
> **bumanie said:**
> Hi Phil, I had a similar (but not the exact same) issue with 9.04 and a HP printer. I went through cups debugging, tried the hplip driver from HP linux site to no avail. In the end, I uninstalled the printer and then went through Administration --> Printing and chose "new" - ubuntu searched for the driver and now all works fine. Hope it is that simple to fix your issue. By the way, this seemed to have happened after an update, the printer had previously worked fine. Try uninstalling and then reinstalling the printer and allow ubuntu to search for the driver.

Cheers for that but no dice. Screen shot attached. It firesup xsane twice too.

---

