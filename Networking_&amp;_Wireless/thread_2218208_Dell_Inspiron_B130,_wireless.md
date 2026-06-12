---
title: "Dell Inspiron B130, wireless"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by jcwhoffman on 2014-04-19
I'm having trouble getting the wireless working on my Dell Inspiron B130 on Lubuntu 14.04.. Attaching my data:

[ATTACH]252263[/ATTACH]

Any assistance with the wireless would be appriciated.

Jason

---

### Post by varunendra on 2014-04-19
Is the problem not being able to automatically detect and connect to wireless networks? If so, were you able to see (and connect to) the available networks after running the wireless_script?

If so, it may be a known bug in this driver+card combination for which there is a simple workaround (adding "iwlist scan" command to /etc/rc.local file). If the problem is something else, please explain the problem in detail. The wireless_script report looks good.

---

### Post by jcwhoffman on 2014-04-20
I wasn't able to connect after the script and I added the "iwlist scan" command to the /etc/rc.local file as suggested... I did see where Chili555 helped resolve the issue on the same model Dell laptop..  [http://ubuntuforums.org/showthread.php?t=1975597](http://ubuntuforums.org/showthread.php?t=1975597)  I did everything suggested but still no luck.. I've only begun in Lubuntu, since I got this older laptop, I figured I'd give it a try. I do have 2 other Ubuntu computers as well. but never had issue with wifi with those...

Jason

---

### Post by varunendra on 2014-04-20
> **jcwhoffman said:**
> I did see where Chili555 helped resolve the issue on the same model Dell laptop..  [http://ubuntuforums.org/showthread.php?t=1975597](http://ubuntuforums.org/showthread.php?t=1975597)  I did everything suggested but still no luck..

Installing the firmware was an essential part, and as per the script report, it has been done properly. But your card is slightly different, and even with the same card + driver, there can be several factors which can make a case significantly different.

Did Network Manager's drop down menu show available networks after running the "sudo iwlist scan" command?

Please note that Network Manager may not attempt wireless connection if the wired connection is being used. So unplug the Ethernet cable > reboot > try the "sudo iwlist scan" command if required > try connecting to your network when (if) it shows up in Network Manager's menu.

If this doesn't help, try this (a wild guess) -
```
sudo modprobe -rv b43 b44 ssb
sudo modprobe -v b43
```
This will remove the wifi and ethernet drivers, then reload only the wireless driver. Try the "sudo iwlist scan" command after this, and see if you can connect now. If still not, I may have to seek help from others.

---

### Post by Hadaka on 2014-04-20
Hi I also have an old B130 14e4:4318

to get it going...i first.
*go into bios ..disable the mini pci card..wireless
* boot back up to the wired connection
* ```
sudo apt-get update
sudo apt-get upgrade
```
once done then..
*back into bios...enable the mini pci wireless
boot back on a wired connection
*```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe -v b43
```

---

### Post by jcwhoffman on 2014-04-20
I have it working now, but I didn't see your msg Hadaka, I ended up doing this 
nm-applet(because Network manager wasn't loaded) then I added it to  add "nm-appet &" to ~/.config/openbox/autostart.sh. I then rebooted and it is working.. Only thing I still don't see the icon for the wireless, so i may try your method anyway to see if it shows up after that.

Varun, Thanks, also because after your last msg, I began to search for Network Manager, then when I found it wasn't running I started it up and connected right away..

---

### Post by jcwhoffman on 2014-04-20
It still didn't load after I made the changes suggested by Hadaka, but the wireless did work..  So I did some more digging and found a article..
[http://http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)  Which says there is a bug regarding NM loading in Lubuntu 14.04...   


To fix the Network Manager not showing up on the panel issue, from the Lubuntu menu select *Preferences > Default applications for LXSession*,  then click on the Autostart tab and under "Manual autostarted  applications" type "nm-applet", then click the "+ Add" button on the  left:

Thanks for all the help!!

Jason

---

### Post by varunendra on 2014-04-21
Great job Jason! Thanks for the feedback and the additional information!

I hope I would remember to check the service network-manager and nm-tool as well from now on. :)

---

