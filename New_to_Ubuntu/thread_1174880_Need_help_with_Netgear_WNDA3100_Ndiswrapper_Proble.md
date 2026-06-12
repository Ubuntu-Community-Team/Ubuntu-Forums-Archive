---
title: "Need help with Netgear WNDA3100 Ndiswrapper Problem!"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by sliceofpi on 2009-05-31
Hello all,

I'm a newbie at Ubuntu and I've been having problem with getting my wireless internet to work correctly.  At this point I have successfully opened System/Administration/Windows Wireless Drivers, at which point I click Install New Driver.  I am prompted about what to install, and I select my .inf driver file for the WNDA3100.  It then tells me that it is "Unable to see if hardware is present."  However after I click out of the warning box and look at the list of "Currently Installed Windows Drivers" I see that the hardware is indeed present.  So at this point I tried to click configure network and I received yet another warning box telling me that it "Could not find a network configuration tool." :( 

In conclusion, I can't download anything directly from terminal since my internet doesn't work on the Ubuntu computer.  However I can download things on another computer and just use a USB flash drive.  I hope to find some help pretty soon.  Thanks in advance!:D

-Declan

---

### Post by Kevbert on 2009-05-31
Please go to Applications-Accessories-Terminal and enter
```
lspci > lspci.txt
```
(list pci devices to a file lspci.txt in your home directory).  Post the file back here. It may be that there's a native linux wireless driver.

---

### Post by sliceofpi on 2009-06-03
This should work.
Thanks again I really appreciate all the help.

---

