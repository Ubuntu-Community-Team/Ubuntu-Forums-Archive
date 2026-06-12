---
title: "Distorted screen after video driver installation"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by Nikhil Kenvetil on 2011-08-19
hi.. so i installed 11.04 on my HP tx1004 laptop, and also installed the video driver from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx) 
 
now, after the Ubuntu logon screen, there is a distorted screen of some sort, n i can't see anything.. it was working fine until i installed de driver.. any help is greatly appreciated.. 
 
FYI: my computer has a 6470M STI Radeon video card(1 GB)

---

### Post by realzippy on 2011-08-19
try
```
sudo ati-driver-installer-xxxxxxxx.run --uninstall
```

---

### Post by Nikhil Kenvetil on 2011-08-20
> **realzippy said:**
> try
```
sudo ati-driver-installer-xxxxxxxx.run --uninstall
```
thanks for that friend.. but i reinstalled 10.04 as a workaround, as 11.04 wasn't coping up with the graphic card.. now, there is another problem.. i went into the Update Manager and updated 10.04 to 10.10, but when i go to About Ubuntu,it still shows 10.04.. did i go wrong somewhere??

thanks in advance

moreover i see two options at the bootscreen, Ubuntu 2.6 and 2.6. They differ, however, by some points at the end.. like some .33 and .26.. i hope i am makin sense..

---

### Post by Mark Phelps on 2011-08-20
The different numbers are different kernel versions -- and if you're having different problems now (NOT a distorted screen anymore) then close out this thread and start a new one.

Don't just keep tacking new problems onto the same thread.  That gets real confusing and will dilute the attention the thread will get.

---

