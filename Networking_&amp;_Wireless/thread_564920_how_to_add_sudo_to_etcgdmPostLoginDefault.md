---
title: "how to add sudo to /etc/gdm/PostLogin/Default"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by derkaie on 2007-10-01
Hello

I am really new to linux but I am happy with Ubuntu so far.
Got my Dell Inspiron1300's WiFi Card working. 
It turns out that I have to run
```
sudo iwconfig wlan0 mode auto
``` (thanks to jbaerbock) 
before/ while connecting.

He recommends to add the mentioned sudo to /etc/gdm/PostLogin/Default 

When I open the file via sudo gedit I get this message 

> 
# Note: this is a sample and will not be run as is.  Change the name of this
# file to <gdmconfdir>/PostLogin/Default for this script to be run.

So how do I change the name and get this script working automatically to perform an action as root after login? And what is meant by "<gdmconfdir>"?

Thanks for your help

Cheers 

the new Ubuntu user derkai from Berlin

---

