---
title: "Help with networking"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by zjagannatha on 2007-07-30
I am trying to have my laptop connect to the internet. Unfortunantely, the wireless is not detecting the network. I have been to the help sections in the Ubuntu OS and the online help sections on the ubuntu website. Both say the same exact thing. The two main problems I am having are:

1) I do not know how to view the system components that are installed in my computer (mainly the wireless card).

2) I cannot download any drivers directly to my computer because the computer will not connect to the internet.

I did however look up my computer's model on the help.ubuntu website and it said that the drivers for the wireless card do not come with the ubuntu OS. As I have stated, I am unable to download any drivers because my computer will not go online.

How do I get a driver from the internet to my laptop.

By the way, I am using a library computer so downloading the driver and writing it to a CD is out of the question.

---

### Post by figgles on 2007-07-31
Its a catch 22. Get thee to a wired ethernet port with internet connection and then download what you need. However, confirm that your card can use either ndiswrapper or madwifi for your wifi setup I've had better experiences with ndiswrapper than madwifi but madwifi is easier to set up.

---

### Post by ugm6hr on 2007-07-31
> **zjagannatha said:**
> 1) I do not know how to view the system components that are installed in my computer (mainly the wireless card).
2) I cannot download any drivers directly to my computer because the computer will not connect to the internet.


1) Look for Ethernet / Network Controller from the following:
```
lspci -nn
```

2) If you cannot download anything from anywhere, then I can't think of a solution.  Can you use a USB-stick at the library?  Or borrow someone else's internet / computer?  Where were you planning on connecting your laptop to wifi?  I think internet cafe's allow you to save files onto USB, don't they?

---

### Post by zjagannatha on 2007-08-07
I cannot use a wired port because my ethernet port is broken. I cannot use a sticky because I don't own one.

In addition to all the original computer trouble, the power source on my laptop stopped working. This is my primary concern at the moment.

Thanks for the help anyway

---

