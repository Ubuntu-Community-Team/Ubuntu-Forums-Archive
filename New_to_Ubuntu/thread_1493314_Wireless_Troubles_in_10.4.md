---
title: "Wireless Troubles in 10.4"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by er6ben on 2010-05-25
Hello all, 

So last night I purchased a new gateway with a built in realtek 8190 wireless card...It does not work, I have tried to use the wrapper method but to no avail and I fear alot of the suggestions are over my head.

My question is, can anybody tell me if I can go to best buy or radio shack and pick up a usb dongle that will plug and play with ubuntu. Thank you

---

### Post by -humanaut- on 2010-05-25
There's a driver available in Synaptic for it open synaptic and search for it should work fine after that.

---

### Post by Gone fishing on 2010-05-25
Well I was surprised as I've never had a problem with a realtek  wireless nic and they've worked out of the box

However, it does seem there is a problem with this nic I found this which might help [http://ubuntuforums.org/showthread.php?t=1433401&highlight=realtek+8190](http://ubuntuforums.org/showthread.php?t=1433401&highlight=realtek+8190)

and some links to windows driver that should work with the ndiswrapper [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E)

It seems that the RTL8192E should work with RTL8190

---

### Post by NUboon2Age on 2010-05-25
> **er6ben said:**
> Hello all, 

So last night I purchased a new gateway with a built in realtek 8190 wireless card...It does not work, I have tried to use the wrapper method but to no avail and I fear alot of the suggestions are over my head.

My question is, can anybody tell me if I can go to best buy or radio shack and pick up a usb dongle that will plug and play with ubuntu. Thank you

without going through the whole troubleshooting procedure  (which you might want to try), There are three GUI tools that worked for me on a problematic wireless adapter (not realtek). Maybe worth a try...

1) Ran Jockey (AKA "**Hardware Drivers**") and if it offers a driver, install it.

2) Ran Synaptic to **install ndisgtk, then ran ndisgtk** (AKA "Windows Wireless..." and installed the ndiswrapper with that.

{the only tricky thing here was I DID need to tell ndisgtk where to find the correct .inf/.sys driver files which  means I had to figure out which ones were correct, make sure they were on my system, and then point to their location.}

3) Ran Synaptic to **install or reinstall modemmanager**.  
[U]
Then, voila!!! up came the local wireless access points.[/U]

---

### Post by Gone fishing on 2010-05-25
Ahh read the question, I've found that most dongles work. However, its probably be best if you go this route, to see what dongles are available and then google them to find out what chipset they use and if this is easy in Ubuntu. Ive found that most Dlink and Gigabyte Dongles just work.

---

