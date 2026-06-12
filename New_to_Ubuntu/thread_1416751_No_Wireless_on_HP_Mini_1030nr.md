---
title: "No Wireless on HP Mini 1030nr"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by Ryasaurus on 2010-02-26
I have finally installed UNR on my flash drive to learn that I can't use wireless. I searched for proprietary drivers, whatever that is and nothing came up. (You can tell I'm not very smart at this stuff haha) 

What should I do?

---

### Post by Apollo87 on 2010-02-26
I believe the HP Mini's need the bcmwl driver. Try opening a terminal and installing this:

```
sudo apt-get install bcmwl-kernel-source 
```

Then restart your computer.

---

### Post by Ryasaurus on 2010-02-26
I tried that, but it says there is no such package. D: Do you think maybe it's because it's on a flash drive?

---

### Post by Apollo87 on 2010-02-26
Try doing a

```
sudo apt-get update
```

and then try installing that package again, it definitely exists.

---

### Post by Ryasaurus on 2010-02-26
I can't do the update, because it can't connect to the internet. And the HP Mini doesn't have an ethernet port. And my other computers won't boot from a usb drive.

---

### Post by Apollo87 on 2010-02-26
You can go to this site and download the deb package then:

[http://packages.ubuntu.com/karmic/i386/bcmwl-kernel-source/download](http://packages.ubuntu.com/karmic/i386/bcmwl-kernel-source/download)

Plus the HP mini does have an ethernet port, its on the left side towards the front. You have to remove the plug to it.

---

### Post by Stillmatic on 2010-03-04
If you can get it connected hardwire for just an update you should be fine.

I had ubuntu on my 1030nr and wireless started working after an update. If it doesn't then run ndiswrapper using the windows drive from hp.com

Hope that helps!

---

### Post by Stillmatic on 2010-03-04
test

---

### Post by Michaelchen on 2010-05-05
For the record, I'm encountering this exact same issue on an out-of-the-box installation of Lucid on my 1030nr as well. Fortunately, the same fix provided above is still valid!

---

### Post by 3L33T on 2010-05-24
Solution posted by Apollo87 worked for me too.

I did a fresh install of Ubuntu 10.04 LTS on my HP 1030NR (scrapped old Ubuntu 9.10 that was on it).  After all updates were downloaded, the wifi still did not work.  In fact, I could not even power on (thru the slider switch on the front right) the wifi at all!!!

Thanks Apollo87 for posting the solution :)

---

### Post by BlackSpiral on 2010-08-30
I solved this way

```

sudo mkdir -p /etc/Wireless/RT2860STA/
sudo touch /etc/Wireless/RT2860STA/RT2860STA.dat
sudo service network-manager restart 

```

my netbook is hp mini 1030la
:D

---

### Post by CGW on 2010-09-23
> **Apollo87 said:**
> I believe the HP Mini's need the bcmwl driver. Try opening a terminal and installing this:

```
sudo apt-get install bcmwl-kernel-source 
```

Then restart your computer.

How do I go about getting these packages without an internet connection?  For some reason neither my LAN or WiFi connections are working.  Is there a way to load these packages on to a thumbdrive?

EDIT: I've got the deb package..but it asks for the Lucid cdrom when trying to install the package.  I have no cdrom drive.  Lucid was installed via a usb thumbdrive which is plugged in.  I cannot connect via Synaptic as I have no internet connections at all.  The installer is claiming there are 10 packages also needed.  It's those packages it can't connect to the repo's to find.


Thanks

---

### Post by SIsensee on 2010-10-22
Awesome fix! Thank you so much worked for my 1030nr right as I was at wits end!

---

### Post by nathanmcneil on 2011-04-27
hi, im fixing my friends hp mini and i have installed ubuntu 10.10 in replacement to windows xp. everything seems to run fine except the wireless. when i try and turn the wireless on it says firmware missing... also i've followed all the tips and tricks listed above and none work. any solutions?

---

