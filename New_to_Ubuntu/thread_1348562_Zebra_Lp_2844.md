---
title: "Zebra Lp 2844"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by zandebar on 2009-12-07
Hi I am having troubles with the zebra lp 2844 in our office.  It was working great, the we upgraded from 8.10 to 9.04, and it won't print.  I tried to reinstall printer, and it won't auto connect.  Tried installing manually using foomatic, but zebra doesn't show up as one of the manufacturers.  Has anyone else had this trouble, or at least know a fix to this?  Thank you.

---

### Post by LunaticHiatus on 2009-12-07
sounds like a driver issue although I do not understand why it would screw up when it upgrades. Sorry I can't be of more help.

---

### Post by JBAlaska on 2009-12-07
What interface are you tring to use, serial or parallel?

Did you try this method for finding the driver (Shamless cut and paste)
```
1. Go to System -> Administration -> Printers
2. That brings up the printer management dialog, where you click the New button.
[B]3. It doesn&#8217;t find the printer automatically, so go with the Unknown device option and click Forward.
4. It searched for a bit and brought up the Choose Driver screen. Scroll all the way down to Zebra and click Forward.[/B]
5. The Zebra LP 2844 uses the EPL2 language, so select EPL2 Label Printer model and the recommended driver.
6. Name it. I called mine ZEBRAR.
```

This [Link](http://blog.makerbot.com/2009/09/22/zebra-thermal-printer-win/) may be of some help, although it refers to using a parallel to USB cable.

---

### Post by zandebar on 2009-12-08
Yes, I think this is how we did it before, however, there is now an option for other, but not unknown device.  When I hit other, it asks me for a Device URI, not sure what that would be.   If i continue saying it's a parallel port, i can choose the right printer and driver, but of course it's not a parallel port, it's usb.  It is possible someone in here messed with the USB settings on the printers and set up the fax, but I also don't see why that would matter unless there is a finite amount of printers you can add through USB.  also I was mistaken, it was upgraded from 9.04 to 9.10.

---

### Post by hfgoulding on 2010-02-15
Get the ppd for the Zebra LP 2844 here: [http://svn.easysw.com/public/cups/branches/branch-1.3/ppd/zebraep2.ppd](http://svn.easysw.com/public/cups/branches/branch-1.3/ppd/zebraep2.ppd)

It took me several hours of searching to finally find where it was stashed.

---

### Post by ubunman on 2012-01-31
Hi,

How to add Zebra tlp 2844 (usb) on ubuntu 11.10 as generic text only ? 

software neeeded.

Thanks.


> **hfgoulding said:**
> Get the ppd for the Zebra LP 2844 here: [http://svn.easysw.com/public/cups/branches/branch-1.3/ppd/zebraep2.ppd](http://svn.easysw.com/public/cups/branches/branch-1.3/ppd/zebraep2.ppd)

It took me several hours of searching to finally find where it was stashed.

---

### Post by overdrank on 2012-01-31
Hi and please start a new thread with your issues. Back to sleep thread. Thread closed.

---

