---
title: "Really need some help...cannot shutdown/restart properly"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by billyauhk on 2011-08-28
Hi everyone, I have my 11.04 on a Toshiba Satellite L-series notebook, and it could not shutdown/restart properly for months.

At start I suspected it was a problem of the kernel and so I waited and see whether there are kernel update, but after months I was failed to get any fix.

My notebook just quit X-server, then sit there for hours or so without any activities...this really **** me off (as a quick, trouble-less shutdown is what I am proud of using Linux instead of W**dows.) I was forced to shutdown my computer with the power button for dozens of times.

I can read every message on the virtual terminal, some from The syndrome does not go away even when I use sudo shutdown -h now, or using old kernel (2.6.38-8) in recovery mode or not.

My prime suspects include:
1. The kernel (may be not anymore)
2. ACPI setting (I don't know...but some say this may be the reason...how to figure out it is correct or not?)
3. fglrx driver for ATI Radeon 
(pls tell me if you are pointing the problem to other software...)

Can anyone help guiding me to check them out? I have a camera for capturing virtually any screenshot and I am sure I could read out all characters + error messages, besides, I can provide log file on request...

My uname -a string:
Linux bill-Satellite-L500 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by kartabosh on 2011-08-28
> **billyauhk said:**
> 
I can read every message on the virtual terminal, some from The syndrome does not go away even when I use sudo shutdown -h now, or using old kernel (2.6.38-8) in recovery mode or not.

what happens when you 
shutdown -h now ?

---

### Post by billyauhk on 2011-08-28
Thx for asking. It just stuck at the virtual terminal and dies there...you can read the screenshot.

If I am correct I selected 2.6.38-10 when I was trying to see whether the problem goes away...but it's not.

I will try shutdown -h now again with 2.6.38-11 after posting this and see...

---

### Post by kaldor on 2011-08-28
I can confirm this bug, though for me it's usually only on a reboot. Shut down works 90% of the time, but sometimes also freezes on the Ubuntu logo.

Natty x64 with proprietary AMD drivers for a Radeon HD 6450.

---

### Post by billyauhk on 2011-08-28
I get some reasonable percentage of correct shutdown (5 out of 5) after sudo update-grub. But this is only for short sessions (login and shutdown immediately.)

But I noticed my scim becomes zombie right after my logon (out of scope of this thread through).

I will try a longer session and see...

---

### Post by billyauhk on 2011-08-28
A longer session (close to 10 hours), with 2.6.38-11, the shutdown fails before the first white dot become red (or...orange...I am not used to differentiate the color...)

---

### Post by laidback on 2011-08-29
This probably has nothing to do with your problem but when I ran v11.04 I found that I needed to stop Libre Office Quickstarter, then I could shut down as normal. In the Wordprocessor, Tools>Options>Memory then uncheck the Quickstarter box. This problem only became apparent from v10.x onwards on my machine. Worth trying.

I believe Quickstarter is activated by befault in v11.x.

---

### Post by billyauhk on 2011-08-29
Thx laidback for the advice but my checkbox is not ticked...so it is not the cause...

---

### Post by laidback on 2011-08-29
Worth a try...thanks for letting me know the outcome.

---

