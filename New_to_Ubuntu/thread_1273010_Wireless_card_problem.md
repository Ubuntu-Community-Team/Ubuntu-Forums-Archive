---
title: "Wireless card problem"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by kutluboga on 2009-09-22
I've searched alot for the solution of the problem but here I am now... :D
My wireless seems to not work.
I have an Acer 3020 Laptop with  Broadcom Wireless Card... I got to the point of installing acer_acpi but the problem starts here. I cant download it becuase the site is blocked in my country. I downloaded the file from an alternative site but dont know how to install the files in it.... What should I do now? Whenever I try to install the acer_acpi file somehow I get this:
No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
Help me!!!

---

### Post by tgeer43 on 2009-09-22
What version of Ubuntu are you running? Acer_acpi was deprecated over a year ago and its upstream port, acer_wmi is merged into all kernels starting with 2.6.25. If you are running something older than Hardy and really need this module then rather than try to compile it from source as you are doing now, there are pre-packaged .deb files available. You'll just have to dig a little to find them as acer_acpi is no longer being maintained.

tgeer

---

### Post by kutluboga on 2009-09-23
I am using jaunty 9.04 but I am still experiencing problems using my wireless card...

---

### Post by tgeer43 on 2009-09-23
I have to step out for a few hours but will revisit this when I get home.

tgeer

---

### Post by Bucky Ball on 2009-09-23
Have you plugged in an ethernet cable and gotten all updates? The Broadcom cards (for the most part) should now work 'out of the box'. You have to get online to make it so though so maybe silly question but it has fixed this problem before. :)

---

### Post by HarrisonNapper on 2009-09-23
What Bucky said. If, after updating, it still doesn't work, let us know, but it may be worth searching for "ndiswrapper" online.

---

### Post by Bucky Ball on 2009-09-23
> **HarrisonNapper said:**
> may be worth searching for "ndiswrapper" online.

Avoid ndswrapper at all costs. It basically wraps the Windows driver and that can be problematic. Many Broadcom cards 'should' work with it but only if a fairy sits on your shoulder, therefore it is generally NOT used and has been superseded for most Broadcom cards now days. Most Broadcom cards are now covered by this driver:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

You shouldn't need to worry about downloading the drivers them from there though. If you haven't already, plug in a cable and get updated. If you have go to System->Administration->Hardware Drivers and make sure the restricted driver is not there already and disabled.

I'm fairly sure you have the Broadcom 4318. This page explains (it is headed Hardy but means Hardy and all releases since):

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

If the B43 driver is not there already and is not offered when updating with an ethernet cable that is another issue.

Let us know along with the output of the command below (copy/paste it in a terminal by going to Applications->Accessories->Terminal): 

```
lspci
```Then we can figure out exactly what you have in there.

Again, ndiswrapper is not appropriate for that card. 

What Ubuntu release are you using BTW?

---

### Post by LewRockwell on 2009-09-23
> **Bucky Ball said:**
> Avoid ndswrapper at all costs.

seconded

.

---

