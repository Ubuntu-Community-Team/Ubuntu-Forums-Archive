---
title: "[SOLVED] How to re-start network manager"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by Pixtu on 2008-11-07
I have been trying for months (yes months!) to get my wireless to work.

I've tried and re-tried various bits from various posts, but todate to no avail.

I'm currently on 8.10 (Intrepid), having previously tried with Feisty and more recently with Hardy.

I did have some success with ndiswrapper with Hardy but it didn't appear to work this time, so I uninstalled it.

Now network manager doesn't appear to see any routers in the area (normally between 2 and 5). It did prior to installing ndiswrapper so I'm assuming something has been 'turned off'.

Basically, I want to get back to where I was when I first installed Intrepid.

What do I need to do please?
What can I check?

---

### Post by yt_l9 on 2008-11-07
Have you tried reinstalling via synaptic?  also what chipset are you using for wireless?  you can use ls pci in the terminal.

---

### Post by Pixtu on 2008-11-07
Have you tried reinstalling via synaptic?
> Yes, but told I need an INternet connection which I am trying to get.

 also what chipset are you using for wireless?
> Belkin USB adapter - F5D6050

you can use ls pci in the terminal.
> In my case its lsusb. This shows the adapter.

lshw indicates that the wlan0 interface as DISABLED.

I think I need to re-enable it but can't find how.

---

### Post by Pixtu on 2008-11-07
This is too simple a problem to wait around for no answer. I've re-installed and will start again from that position.

---

### Post by yt_l9 on 2008-11-07
have you tried:

sudo ifconfig wlan0 up

---

### Post by yt_l9 on 2008-11-07
looks like I wasn't quick enough... sorry and good luck!

---

