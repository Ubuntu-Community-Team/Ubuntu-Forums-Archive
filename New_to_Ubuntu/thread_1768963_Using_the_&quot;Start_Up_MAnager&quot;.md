---
title: "Using the &quot;Start Up MAnager&quot;"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-27
Hello again, I have tried to use the start up manager to select which operating system to boot to, and it does not select it by default, I still have to choose which operating system to boot to.  Any ideas?  (See Pic)

---

### Post by Prince Valiant on 2011-05-27
A workaround would be to set the timeout to 0 seconds.

-Val

---

### Post by wildmanne39 on 2011-05-27
> **TAspr said:**
> Hello again, I have tried to use the start up manager to select which operating system to boot to, and it does not select it by default, I still have to choose which operating system to boot to.  Any ideas?  (See Pic)
Hi, setting a time out to 0 does not sound like a good idea, then you would not get the option to choose which system you want to boot into.):P

---

### Post by audiomick on 2011-05-27
+1 that. 3 or 5 or something, but not 0.

> and it does not select it by default, I still have to choose which operating system to boot to

does the machine boot to something other than the install that you have selected, or are you just expecting it to boot to that immediately? According to the settings in your screenshot, the machine should boot to the selected default after 10 seconds.

---

### Post by TAspr on 2011-05-27
> **audiomick said:**
> +1 that. 3 or 5 or something, but not 0.



does the machine boot to something other than the install that you have selected, or are you just expecting it to boot to that immediately? According to the settings in your screenshot, the machine should boot to the selected default after 10 seconds.

It is bootiing to Ubuntu, but I wanted it to boot to Windows7 as my wife is not totally comfortable with Ubuntu yet.

---

### Post by webofunni on 2011-05-27
The default in the screen shot is ubuntu. Did you change that to windows ?

---

### Post by drs305 on 2011-05-27
Startup Manager should be able to do what you wish. An app which integrates better with Grub 2 is Grub Customizer. Here is a link that explains how to install and run it:
[http://ubuntuforums.org/showthread.php?p=10340183]("http://ubuntuforums.org/showthread.php?p=10340183")

---

### Post by TAspr on 2011-05-28
I figured it out.  After using the legacy version of Grub, and uninstalling both the legacy version and the "Grub Customizer", then reinstalling the customize, it then worked.  Thanks a bunch again for all your help.

---

