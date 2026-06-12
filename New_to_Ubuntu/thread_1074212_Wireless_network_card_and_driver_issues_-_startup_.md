---
title: "Wireless network card and driver issues - startup problems"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by ReaperManHK on 2009-02-19
Ever since installing Ubuntu, several months or so ago, I have found that the Broadcom driver included in the restricted drivers list to be terribly unreliable - randomly disconnecting, constantly asking me for network passwords and taking ridiculous amounts of time to connect. 

Recently I installed the Windows driver for my card through Ndiswrapper. It worked great up until today when I ran software update.

Now when I restart, I cannot connect to the network, the light indicating the status of my card shows that it's off and when I right click on the network applet in the notification area, there is no option for wireless networks.

I re-installed the Linux drivers, but it too has problems (besides the aforementioned instability). I can then connect to WiFi networks, but when I restart, I'm forced to re-install them, for my network adapter is disabled again!

I've tried re-installing the Ndiswrapper drivers through Ndiswrapper and NdisGTK, and they're detected as being installed, yet there is still no option to enable wireless networking.

If anybody has any solutions to either improve the wireless network drivers included with Linux/alternatives or fix my Ndiswrapper driver problems, it would be greatly appreciated.

I've searched around for solutions before posting this, so I hope I'm not asking something that has already been asked.

---

### Post by adult swim on 2009-02-19
if you are still using ndiswrapper, have you added ndiswrapper to your /etc/modules?  if you do that it shoudl load on every boot.  to add it, go to a terminal and enter in ```
gksudo gedit /etc/modules
``` then go to the bottom of the file and add a line that says ```
ndiswrapper
```

---

### Post by ReaperManHK on 2009-02-19
Yes, I had done that already.

---

