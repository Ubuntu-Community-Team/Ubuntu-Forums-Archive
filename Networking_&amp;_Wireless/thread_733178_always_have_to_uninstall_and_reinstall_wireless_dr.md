---
title: "always have to uninstall and reinstall wireless driver"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by Falc7 on 2008-03-23
I am using the ndiswrapper to use my belkin usb wireless adapter. However, every time i restart ubuntu i have to uninstall and reinstall the driver to connect. Otherwise ubuntu dosen't use the device and can't see the wireless network. It dosen't even label wireless as an option under network settings. Is there a way to avoid uninstalling and reinstalling every time?

---

### Post by Sam Lars on 2008-03-23
Have you run
```
ndiswrapper -m
```

---

### Post by coolbrook on 2008-03-23
After invoking the driver, in terminal...

```
gksudo gedit /etc/modules
```

add *ndiswrapper* to a line at the bottom. 
Close the window and choose to save the file.

The next time you restart your computer, Ubuntu will run ndiswrapper and the driver should be working for you.

---

### Post by Sam Lars on 2008-03-23
If I remember my command correctly, it should do the same thing.

---

### Post by Falc7 on 2008-03-24
thanks very much guys

---

### Post by The Crazy Parrot on 2008-03-31
Thanks for the help, this was really a nuisance.

---

