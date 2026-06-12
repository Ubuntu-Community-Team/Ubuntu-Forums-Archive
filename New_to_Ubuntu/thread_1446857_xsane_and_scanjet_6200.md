---
title: "xsane and scanjet 6200"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by squrl on 2010-04-04
I have a scanjet 6200 (USB) connected and Xsane loaded When xsane comes up it says (xsane 0,995 scanjet 62x0c)

When I press for a scan an error box comes up and says it couldn't start the scanner then the program hangs. 

Any suggestions or help appreciated

Thanks  
 running 8.04

---

### Post by s_ø on 2010-04-04
Try to go to **System > Users And Groups**. Click on the little key symbol. Click **Properties** then **User Privileges**. Check the box **Use Scanner**.

---

### Post by squrl on 2010-04-05
I did just like you suggested. I checked the boxes and rebooted. It didn't seem to make any difference.

Thanks anyway

---

### Post by agnes on 2010-04-05
If you check [this page]("http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD"), the Scanjet 6200C should be supported with sane-backends-1.0.20.
The version in the repos (Ubuntu Lucid default at least) is 1.0.14.
So you could try to download & compile the newest sane version from the sane website.

edit: but first make sure the packages sane-utils and libsane-extras are installed

---

### Post by squrl on 2010-04-05
Thanks Agnes. Your take on the numbers is right on. I guess I'm out of luck. I don't have a clue how to compile much more than the time of day

Thanks again.

---

### Post by squrl on 2010-04-06
bump

---

