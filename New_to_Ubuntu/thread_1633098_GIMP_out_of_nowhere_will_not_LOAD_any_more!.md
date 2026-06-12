---
title: "GIMP out of nowhere will not LOAD any more!"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by expressdiv on 2010-11-28
I am running Ubuntu 10.10 on a Toshiba Satellite Laptop. I have been running it for sometime with no problems. 

I have been using Gimp 2.6 for quite sometime now, and with no problems. I went in to open it today, and All I get is the Mouse loading Icon, and a Task Bar window that says "Starting GIMP Image..." Upon waiting, it stays on the taskbar for 10 secs and then disappears.

**What I have done to try and fix it**

Uninstall-Reinstall GIMP - UNSUCCESSFUL, SAME PROBLEM
Check Synaptic Package Manager Green Boxes Checked - NO LUCK

I would greatly appreciate some help. Maybe there is another method other than Ubuntu Software Center to COMPLETELY UNINSTALL??

Thanks A MILLION!

---

### Post by drs305 on 2010-11-28
expressdiv,

Welcome to the Ubuntu forums.

If your start it from the terminal (Applications, Accessories, Terminal)  with "gimp" do you get any error messages?

---

### Post by asmoore82 on 2010-11-28
Try moving your personal GIMP config to a backup location: ```
cd $HOME
mv .gimp-2.6 .gimp-2.6.backup
```

---

### Post by expressdiv on 2010-11-28
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:5582): LibGimpBase-WARNING **: gimp: wire_read(): error



But then it goes on to load Gimp 2.2 I did this earlier and installed something it called 'Gimp Shop' and now I can access Gimp 2.2. However, I cannot find anywhere how to uninstall 2.2

---

### Post by Perfect Storm on 2010-11-28
> **expressdiv said:**
> /usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:5582): LibGimpBase-WARNING **: gimp: wire_read(): error



But then it goes on to load Gimp 2.2 I did this earlier and installed something it called 'Gimp Shop' and now I can access Gimp 2.2. However, I cannot find anywhere how to uninstall 2.2

It might be that mess up Gimp. How did you install Gimp Shop (file type)?

---

### Post by thinhhanh on 2011-01-04
> **Artificial Intelligence said:**
> It might be that mess up Gimp. How did you install Gimp Shop (file type)?

Good hint! I removed Gimp Shop and it fixed my problem (same error message with Gimp 2.6.7.  Re-installing Gimp doesn't help btw.
Thank you!

---

