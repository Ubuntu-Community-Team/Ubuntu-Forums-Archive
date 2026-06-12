---
title: "Scanner Woes"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by eyeofreason on 2010-08-08
Anybody have a suggestion. I have a Brother MFC-290C printer,scanner,fax. I dl the printer driver from Brother, it works. I dl the scanner driver , no luck. The deb seems to have installed fine . The scanner says it can't connect to pc. XSane says "no device available." I'm using Karmic.It's a usb type new scanner. Thank you for taking the time to help me!

---

### Post by dwbsr on 2010-08-09
> **eyeofreason said:**
> Anybody have a suggestion. I have a Brother MFC-290C printer,scanner,fax. I dl the printer driver from Brother, it works. I dl the scanner driver , no luck. The deb seems to have installed fine . The scanner says it can't connect to pc. XSane says "no device available." I'm using Karmic.It's a usb type new scanner. Thank you for taking the time to help me!

Did you do the "Before the installation" "Pre-required procedures"
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#prereq](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#prereq)

Pre-required Procedure (8)
Related distributions
Debian, Ubuntu
Related products/drivers
brscan, brscan2, brscan3
Requirement
sane-utils is required to be installed.

Then do the Scanner Setting for normal user

Ubuntu 9.10, 10.04

```
Ubuntu 9.10, 10.04
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 
```

---

### Post by eyeofreason on 2010-08-09
Thank You VERY much ! That worked like a charm. I like your signature. My wife will be very pleased to use her scanner again.

---

### Post by QQi on 2010-12-15
thank you :D:D That worked here

---

### Post by detourwest on 2012-01-18
does this work with 11? i will try to understand these directions if it should...

---

### Post by kurt18947 on 2012-01-19
> **detourwest said:**
> does this work with 11? i will try to understand these directions if it should...

That is required in 11.10 for normal users. In addition there is an install glitch in 11.10 where files are installed to an incorrect location.  Here is a link:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

---

