---
title: "Need help installing NDISwrapper utilities"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by hitemhrd on 2008-11-29
My ubuntu system is not hooked up to the internet. But I do have a Windows XP system online. Is there a way to download the NDISwrapper utilities to my xp machine and then install them on my Ubuntu machine? I need this so I can get my wireless card installed on Ubuntu.

Any help would be greatly appreciated.

---

### Post by caljohnsmith on 2008-11-29
> **hitemhrd said:**
> My ubuntu system is not hooked up to the internet. But I do have a Windows XP system online. Is there a way to download the NDISwrapper utilities to my xp machine and then install them on my Ubuntu machine? I need this so I can get my wireless card installed on Ubuntu.

Any help would be greatly appreciated.
Sure, just go to:

[http://packages.ubuntu.com](http://packages.ubuntu.com)

And download the "ndiswrapper-utils-1.9" package and the "ndiswrapper-common" package for your version of Ubuntu, put them on your Ubuntu Desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo dpkg -i ~/Desktop/ndis*.deb
```
And I think that should work. Let me know if you run into problems though.

---

### Post by aysiu on 2008-11-29
I'd also install *ndisgtk* so you have a graphical frontend for *ndiswrapper*. Might make your life a little easier.

---

### Post by hitemhrd on 2008-11-29
You rock. I got the ndiswrapper utilities installed however I had to use version 1.8 because of compatibilities with Ubuntu version 6.06. That being the case, where can I find the previous version of ndisgtk? Version 0.6 needs version 1.9 of ndiwsrapper and I have 1.8 so it won't install.

Thanks for all of your help. I'm very novice with Linux as you can tell.

---

### Post by aysiu on 2008-11-29
[http://packages.ubuntu.com/dapper/ndisgtk](http://packages.ubuntu.com/dapper/ndisgtk)

---

### Post by hitemhrd on 2008-11-29
Got it. Trying to use now. I'll let you know how it works.

---

### Post by hitemhrd on 2008-11-29
Awesome! I'm close. I got the wrapper installed, then got ndisgtk to work. I got the driver installed with the ngdiskgt but it says the usb adaptor is not present. What is the last step to get Ubuntu to see that the hardware is connected and associate the driver with that hardware?

---

