---
title: "Poor Wifi on Thinkpad X1 Carbon with &quot;adaptive function keys&quot;"
date: 2015-06-18
forum: Networking &amp; Wireless
---

### Post by jeromecovington on 2015-06-18
My Wifi is great if I sit near the router. But elsewhere (in places that I get a strong signal on my work-issued MacBook Pro) I have very poor signal strength. Almost useless. Which is a shame as I prefer to do my work on Ubuntu on this laptop. I ran the diagnostic script referenced in this forum, and I am attaching the results.

---

### Post by wildmanne39 on 2015-06-18
Hi, welcome to the forum! please do:
```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwldvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Copy and paste for accuracy and watch for errors.

Also check the security encryption settings in both the computer wireless profile and the router. For home use we recommend WPA2-AES and avoid options related to TKIP.

Set IPV6 to ignore in network manager.

Lets also turn power management off:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off 
```
above exit0, then save gedit, close and reboot.
Thanks

---

### Post by jeromecovington on 2015-06-18
~> sudo modprobe -rfv iwlwifi
modprobe: FATAL: Module iwlwifi is in use.

Is this normal?

---

### Post by wildmanne39 on 2015-06-18
Sometimes it happens run the next command then try that one again, then just continue until you have done everything in that post.
Thanks

---

### Post by jeromecovington on 2015-06-18
Ok. Thank you. That may have fixed it. Let me do some work and if things don't seem to have improved, I will respond to this thread again.

---

### Post by wildmanne39 on 2015-06-18
If it works better please mark as solved. You may never get the exact results that you do from the other operating system. But it should be much improved.

---

### Post by jeromecovington on 2015-06-18
No, it doesn't seem to have improved. Down to almost no signal. It tends to vacillate between that and a moderate/weak signal. That seems just as it was before, unfortunately.

---

### Post by wildmanne39 on 2015-06-18
Does it stay connected? does it slow way down?
Thanks

---

### Post by jeromecovington on 2015-06-18
It stays connected and slows way down. That behavior seems unchanged since running the commands you suggested.

---

### Post by wildmanne39 on 2015-06-18
Run the script again and post a new file so we can see if the changes took effect. It may be tomorrow before I take a look it is getting late here.
Thanks

---

### Post by jeromecovington on 2015-06-18
Here you go. Thanks for taking a look. Take your time!

---

### Post by jeromecovington on 2015-06-19
My Wifi slowed to a halt and I ended up submitting that last post several times. Apologies!

---

### Post by wildmanne39 on 2015-06-19
> **jeromecovington said:**
> My Wifi slowed to a halt and I ended up submitting that last post several times. Apologies!
This is an issue with the forum not your computer, it happens from time to time.

---

### Post by wildmanne39 on 2015-06-19
Go back to post 2 and try to set power management to off again, then set IPV6 to ignore like post 2 says, if you have any trouble post back the exact trouble with each one.
Thanks

---

### Post by jeromecovington on 2015-08-05
Upgraded to 14.10 as I had read that the support in the kernel for iwlwifi had improved, which seems to be the case as the wifi seems to have a sustained signal without dropping.

---

