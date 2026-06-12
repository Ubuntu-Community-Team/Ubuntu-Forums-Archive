---
title: "Weak wifi signal after Ubuntu 14.04 install"
date: 2015-12-01
forum: Networking &amp; Wireless
---

### Post by thinktwice2 on 2015-12-01
I recently installed Ubuntu 14.04 on my Lenovo Z70-80.  The laptop came pre-installed with a Qualcomm Atheros WirelessNIC for which linux drivers have not been written yet and I had no signal at all (wired worked, though). So I replaced it with an Intel 7265AC wireless card and now I have wifi, although I have to be very near whatever WAP I happen to be using or the signal is almost completely lost.  I tried going through many of the workarounds and bugfixes I found in this forum and a few others until I got to a point I wasn't really sure of all the fixes I tried.  So I just reinstalled Ubuntu 14.04 and the problem persists.  If anyone could shed some light or point me in the right direction that would be great, thanks.  I've attached the result of a script I found [here]("http://ubuntuforums.org/showthread.php?t=370108") on the forums that details my connections and hardware and whatnot.  
Please and Thank You.

---

### Post by praseodym on 2015-12-01
Please run
```

echo "options iwlwifi wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
sudo iwconfig wlan0 power off
```

---

### Post by thinktwice2 on 2015-12-01
praseodym,

Thanks for your quick reply.  The results of the second command "sudo modprobe -rfv iwlwifi" are: "```
modprobe: FATAL: Module iwlwifi is in use.
```  I continued with the list of commands you gave me and got no response from the third command.  
But the results of the fourth command are: ```
Error for wireless request "Set Power Management" (8B2C) : SET failed on device wlan ; No such device.
```

Not sure if this helps at all.  Can you also answer this question for me: What is the effect of this sequence of commands?  Is it to disable, remove, and then reload the driver; and then turn off the power management for the wireless card?  I just want to learn about this process.  Thanks again.

---

### Post by praseodym on 2015-12-01
Then reboot

---

