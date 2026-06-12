---
title: "Scanner Not Working in Ubuntu"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by Andrew Jeyaraj on 2011-06-26
i have an hp Deskjet 1050(printer scanner,copier).I dual boot windows xp along with ubuntu 10.04. while the printing works wonderfully well on ubuntu,Simple Scan and x-sane fail to recognize the scanner.


i get this message: Failed to open device 'hpaio:?usb?Deskjet_1050_J410_series?serial=CN11K3P32V05HW': Device Busy

However it works just fine in windows xp....

whats the problem and how can i get it working again.

Thanks
Andrew

---

### Post by 73ckn797 on 2011-06-26
What version Ubuntu are you using? Did you install Xsane?

I had issues with Xsane in 9.10 after several updates. In 10.04 Xsane was not included in the default install, if I recall correctly. I tried installing Xsane but that broke both Simple Scan and Xsane. I was able to use Simple Scan with no problems after removal of Xsane. With 11.04 Xsane is working flawlessly. There were several posts addressing this. You will need to search around.

---

### Post by Andrew Jeyaraj on 2011-06-26
im running 10.04 but i think the version of xane im using is the latest. unfortunately simple scan doesnt work either.

---

### Post by 73ckn797 on 2011-06-26
> **Andrew Jeyaraj said:**
> im running 10.04 but i think the version of xane im using is the latest. unfortunately simple scan doesnt work either.
My issue was that once I installed Xsane, because I liked a particular feature, it caused both to quit working by not recognizing the scanner. I have the HP 3780. I ended up purging all of Xsane to get Simple Scan to work.

Was Simple Scan not recognizing your scanner prior to Xsane being installed?

---

### Post by Andrew Jeyaraj on 2011-06-27
yeah. Simple Scan didn't pick up the scanner even before i installed x-sane.

Simple scan gives me this error: Failed to Scan,unable to connect to scanner.

However everything works just fine in windows.

---

### Post by 73ckn797 on 2011-06-27
> **Andrew Jeyaraj said:**
> yeah. Simple Scan didn't pick up the scanner even before i installed x-sane.

Simple scan gives me this error: Failed to Scan,unable to connect to scanner.

However everything works just fine in windows.

Try reinstalling (if you have not already done so) Xsane or uninstalling completely and reinstall Simple Scan.

---

### Post by Andrew Jeyaraj on 2011-06-28
ive tried everything.and its still not working...

---

### Post by plucky on 2011-06-28
> **Andrew Jeyaraj said:**
> ive tried everything.and its still not working...

Have you tried from a terminal ```
gksudo xsane
```

If that works,then it is a permission problem with the USB connection.

---

### Post by Andrew Jeyaraj on 2011-06-29
it doesnt work.i get the same error message.

---

### Post by madmax75 on 2011-08-08
Hi!

I solved this same problem with my own HP Deskjet 1050 by updating the **hplip** library.

I use Ubuntu 10.10 and it does not install the latest hplip by default. **You need to get the most recent one (hplip-3.11.7) from HP website**:

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

It has very good instructions on how to update this library. Basically you have to download the new library and then give a command in the terminal and answer yes or no a couple of times. That's pretty much it.

I suggest putting the downloadable .run file into your home directory, not on the desktop. The .run file seems to install the updated library on the same location where it is itself. I run it from the desktop, and now I have this ugly hplip-3-11-7 sitting there as well...

It will also install HP's own printer management GUI.

My scanner is now working just fine after doing this.

---

### Post by jponman on 2011-10-21
Hi!

updating the hplip library worked for me too.

Thanks a lot, madmax75!

---

