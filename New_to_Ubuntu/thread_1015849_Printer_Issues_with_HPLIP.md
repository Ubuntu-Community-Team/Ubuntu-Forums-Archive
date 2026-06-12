---
title: "Printer Issues with HPLIP"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Greg Linscott on 2008-12-19
Hi all.

I am trying to help an older neighbor keep her older computer alive and functioning (it was originally a Win98 machine). I helped her install Ubuntu on it almost a year ago now. She recently bought a new HP F4235 to replace the previous printer she had, and though it has been detected and installed by the system, I have not been successful in getting anything to actually print from it (test pages, Open Office documents...). I have tried the CUPS interface, manually installing it with HPLIP (that interface does not automatically detect it when I uninstall the machine), and nothing I am trying is successful. I have confirmed that the printer itself functions (it copies and prints via the scanner, and also prints a test page from a Windows machine), so I have ruled out any kind of mechanical issue.

Any other ideas?

---

### Post by boof1988 on 2008-12-19
> **Greg Linscott said:**
> Hi all.

I am trying to help an older neighbor keep her older computer alive and functioning (it was originally a Win98 machine). I helped her install Ubuntu on it almost a year ago now. She recently bought a new HP F4235 to replace the previous printer she had, and though it has been detected and installed by the system, I have not been successful in getting anything to actually print from it (test pages, Open Office documents...). I have tried the CUPS interface, manually installing it with HPLIP (that interface does not automatically detect it when I uninstall the machine), and nothing I am trying is successful. I have confirmed that the printer itself functions (it copies and prints via the scanner, and also prints a test page from a Windows machine), so I have ruled out any kind of mechanical issue.

Any other ideas?

Which version of hplip are you using?  There is a 2.8.12 version available at HP.

Check out this thread [here](http://ubuntuforums.org/showthread.php?p=6080728#1).

HP has a page that links to the current downloads for your printer [here](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&dlc=en&cc=us&lang=en&product=3571316&).

The download from HP has an automatic installer that worked pretty well for me.  I assume the computer is connected to the Internet.

Download the file -> CLI input "sh hplip-2.8.12.run" -> follow terminal prompts.

Maybe this helps.

---

### Post by vikigal on 2008-12-19
I just installed an hp 4480. I had to use the download because of cd issues. The printer would not install correctly until I uninstalled hpoj (?) which was on my system from my old printer. If the previous printer was hp you might want to check that.

---

### Post by Greg Linscott on 2008-12-19
Thank you. I am not exactly sure which of the answers was most effective, but I downloaded the HPLIP from the HP website, uninstalled a file that may have been from the previous printer, abnd then, after the machine wa detected and still wouldn't print, changed the driver from F4200 to F4213 Success at last!

---

### Post by Jonathan_of_Cincinnati on 2010-03-15
> **vikigal said:**
> I just installed an hp 4480. I had to use the download because of cd issues. The printer would not install correctly until I uninstalled hpoj (?) which was on my system from my old printer. If the previous printer was hp you might want to check that.

I have the same printer.  For me, it showed the description of a 4480 but the driver was a 24xx something printer.  As soon as I changed it to a 42xx printer, which is the closest one to the 4480.  It started printing.  I have not figured out how to get the scanner to work yet.

---

