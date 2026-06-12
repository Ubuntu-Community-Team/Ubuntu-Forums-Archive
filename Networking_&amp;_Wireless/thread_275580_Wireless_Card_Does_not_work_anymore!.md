---
title: "Wireless Card Does not work anymore!"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by shuaibe on 2006-10-11
Hi,

I downloaded and compiled the kernel 2.6.17.13 using the following thread
[http://ubuntuforums.org/showthread.php?t=217657&highlight=kernel+source+from+CD](http://ubuntuforums.org/showthread.php?t=217657&highlight=kernel+source+from+CD)
The Ubuntu works fine but my wireless card does not work anymore. So following another thread i used ndiswrapper to install the appropriate driver for built in Intel Wireless 2200BG. The wireless interface does not shows up in the network manager. So i removed the driver installed by ndiswrapper and again installed ipw2200 from scratch but still wireless interface does not work. When i type lsmod, it shows ipw200 loaded but when i type lshw it shows UNCLAIMED (no logical name)for the wireless device. Sorry for the long story ... any suggestions ? Thanks for your time!

---

### Post by encompass on 2006-10-11
I would try going back to your old kernel for the time being...
Didn't look at your link but if it is a costum kernel I don't recommend it.
You would have to reinstall everything all over again everytime there is a kernel change.
To run your old kernel... when you boot up you will see a count down... aobut 3 seconds... press escape and choose an older, and working kernel.  Did it help at all?

---

### Post by shuaibe on 2006-10-12
Thanks for the tip .. yes i can easily use my old kernel but i was curious what could be the reason even after installing the wireless card from scratch ...

---

### Post by encompass on 2006-10-12
It could be something to do with the ndiswrapper... did you ahve to combile anything manually?  Otherwise, I am not smart enough to know.

---

