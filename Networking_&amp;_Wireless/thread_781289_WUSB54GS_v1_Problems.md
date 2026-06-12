---
title: "WUSB54GS v1 Problems"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by ahmedh on 2008-05-04
I've done everything I can to try to get my Linksys WUSB54GS (v1) USB adapter to work with Ubuntu 8.04. I've followed many tutorials and none of them seem to be working very well. I've tried to install the proper .inf file with ndiswrapper (invalid driver!). I tried this trick in terminal:  ndiswrapper -d 13b1:000e WUSB54GS.inf 
but got this error:
ls: cannot access /etc/ndiswrapper/WUSB54GS.inf/: No such file or directory
driver 'WUSB54GS.inf' is not installed (properly)!
When I tried to move the .inf to the directory, I couldn't (permission denied). I tried to log into root so that I could move the file, but I couldn't (can't log in to root from the log in screen, apparently). 

In the etc/ndiswrapper folder, I see a wusb54gs folder, and in it is the wusb54gs.inf driver (most likely a leftover from when I used WINE to run the .exe Linksys driver installer I downloaded from the website [didn't work]), but with the adapter plugged in, nothing happens. I remove my ethernet cable, log out and back in, plug in the wireless adapter, nothing. In the network manager, all I see is "Wired Connection" and "Point-to-Point" connection. I can't even try to set up a wireless connection. 

I tried this: [http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gs](http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gs)
Now I can access wireless settings, but it won't connect to any networks (it does recognize our home network...it tries to connect an then an exclamation mark appears over the network icon)

I would really appreciation some help. Thank you.

---

