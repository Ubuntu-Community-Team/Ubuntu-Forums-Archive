---
title: "won't recognize thinkpad wireless card"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by blenderfish on 2007-02-28
I just installed Edgy on my Thinkpad z61m, and most of the hardware is working out of the box, or with a minor tweak.  I cannot, however, get the system to recognize my wireless card.  I have what IBM refers to as a "Thinkpad" wireless card.  When I run lspci, the card is listed as "Atheros Communications, Inc. Unknown device 0024 (rev 01)"

I have installed network manager, and my understanding is that madwifi is installed with the linux-restricted-modules, which I have. When I go to System -> Administration -> Network Settings I only see "Wired Connection" and "Modem Connection" listed. No Wireless.  

Any ideas?  I have seen other posts that seem related, but nothing seems to show a straightforward answer.

---

### Post by Floppyjoe on 2007-02-28
I think that card works on 32bit machines with ndiswrapper.
You need to install a new version of ndiswrapper from [sourceforge.net]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148")
Download this package and extract it into your home directory. Where I got this info from it said version 1.29 but the newer ones may work too.
then:
```
$ cd to ndiswrapperdirectory
$ sudo make uninstall
$ sudo make
$ sudo make install
```
When ndiswapper is installed download the driver you need from [here]("http://www.dlink.com/products/support.asp?pid=489&sec=0").
I'd go with the Windows XP driver.
Unzip the driver into your home directory and cd to the folder with the driver files in it.
Then:
```
$ sudo ndiswrapper- i net5416.inf
$ sudo ndiswrapper -l
$ sudo depmod -a
$ sudo modprobe ndiswrapper
```
It also mentioned removing the linux-restricted-modules package

---

### Post by blenderfish on 2007-02-28
Thanks a lot for your help.  I'm still having some issues though.  I followed your instructions, and I saw the wireless light turn on, but the last instruction (modprobe ndiswrapper) caused my system to hang.  I did a hard reboot, and Ubuntu then hung when it hit the point in the boot cycle when I saw the wireless light come on.  

I can boot successfully with the wireless switch (I have  hard switch on the case) in the off position, but the wireless light remains on.  At this point I see a wireless connection under Network Settings.  I was able to see Wireless network stuff when I clicked on the network icon in the panel, but it did not list any wireless networks.  When I clicked on "other network" and typed in my router's name, it searched but was unable to connect.  After another reboot, I do not see these wireless options any longer.  I still see Wireless under Network Settings, but nowhere else.

I appreciate your help.  I'm obviously still a bit lost.

---

### Post by Floppyjoe on 2007-02-28
What are the outputs of:
```
ndiswrapper -l
```
and:
```
ndiswrapper -v
```

I'm not sure why that is not working properly for you.
I followed advice from here:
[http://madwifi.org/ticket/1001](http://madwifi.org/ticket/1001)
And here:
[http://ubuntuforums.org/showthread.php?p=1822454#post1822454](http://ubuntuforums.org/showthread.php?p=1822454#post1822454)

---

### Post by noridlo on 2007-02-28
Blenderfish,

I had a similar issue with my Thinkpad T40. I suggest going to the manufacturer website and verifying that your BIOS is up to date (my wasn't). This solved my problem and may solve your problem too.

---

### Post by blenderfish on 2007-02-28
After digging a little deeper at [http://madwifi.org/ticket/1001](http://madwifi.org/ticket/1001) I found that the D-link driver does not work on the Thinkpad version of this card.  I installed the Lenovo driver and it seems to be working, but I'm still having a problem.  

The system recognizes my card, and iwconfig shows my card, but I cannot get network-manager to show the wireless network.  Network Monitor shows that I am connected with a strong signal, and my device has aquired an IP address from my router, but Network Manager only shows the wired network.  If I disconnect the wired network (just pull the plug), I have no access. 

I'm so close I can taste it...  Any help is much appreciated.  It seems like others are having this or similar problems on the forum but I can't find a solution.

---

### Post by blenderfish on 2007-02-28
Ok, all fixed!  I reinstalled all network-manager packages, but before I did that I made sure that I left my Wireless Connection UNCONFIGURED in Network Settings.  This did the trick!  Thanks for your help guys.

---

