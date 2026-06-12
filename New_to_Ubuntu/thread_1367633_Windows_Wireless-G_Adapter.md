---
title: "Windows Wireless-G Adapter"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by theasian on 2009-12-29
[FONT=Comic Sans MS][SIZE=4]I have tried over and over again to get my Windows Wireless-G Adapter to work on UBUNTU.  However, after installing NDISWRAPPER AND NDISKGK (or whatever it's called, I installed the drivers for the adapter.  After installation, it tells me that the hardware is NOT present.  Can anybody please tell me what is wrong or what I need to do?  Thanks.

Thank you.
[/SIZE][/FONT]

---

### Post by leef on 2009-12-29
sometimes the adapter has lots of different version of windows drivers and some of them don't work, If I were you I would open a terminal and type "lspci -nn" there should be a list of your hardware with numbers in the following format "XXXX:XXXX" do a google search on that number and you should at the very least find people with the same hardware/problems and possibly a solution.

Edit: if it's USB do "lsusb"

---

### Post by theasian on 2009-12-31
I tried what you told me to do but nothing was given to me in the form of "XXXX:XXXX".  What should I do - thanks for helping.

---

### Post by ovid9 on 2009-12-31
You could post the output of "lspci -nn" here.  Someone will probably be able to decipher it for you.  
 
Also, thanks for changing your font.  ;)
 
A final thing, wireless adapters have gotten pretty inexpensive, and if this is getting to be too much of headache spending $20-25 for an adapter that works might be worth it.   That's 100% personal choice though, some people like fiddling trying to get hardware working.  :)

---

### Post by bkratz on 2009-12-31
> **theasian said:**
> **I tried what you told me to do but nothing was given to me in the form of "XXXX:XXXX".  What should I do - thanks for helping.**

Can you either copy\paste the output here, or type it or simply decode it and tell us what it said regarding the network or ethernet statements?


If it is a usb device, use the term   lsusb

---

