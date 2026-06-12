---
title: "Wi-fi driver stops working after hibernation"
date: 2016-12-28
forum: Networking &amp; Wireless
---

### Post by lvrma on 2016-12-28
Hey guys!

So, basically my Alienware 17 laptop's wi-fi card (the **Killer 1535**) has always been problematic, and although Ubuntu "supports" it, it never actually worked out of the box. Still, I've done some tweaking that did the trick. Here's what I've done:

I've found in the manufacturer's website a link to a github repo which contained a couple of files called **board.bin** and** firmware-4.bin** for the model of my card. I've copied both files to** /lib/firmware/ath10k/QCA6174/hw3.0/** and replaced what was previously there.
Then, I created the file **/etc/modprobe.d/ath10k.conf** with this line in it: **options ath10k_core skip_otp=y**

Now, that works just great if the system has just been booted up.
If it goes on suspend though, when it comes back the wifi doesn't work anymore, and what shows up in the wireless tab is the same as it showed before I manually installed the new files as described above (meaning it kinda "goes back" to not recognizing the card). It only works again after I restart the system.

I've found similar threads but all list solutions like in [this one]("http://askubuntu.com/questions/761180/wifi-doesnt-work-after-suspend-after-16-04-upgrade"), and they didn't do the trick at all.

I'm attaching two *wireless-info* files, one called **wireless-info-working.tar.gz,** which was the output of the script with the driver working (before going on suspend), and the other is called **wireless-info-broken.txt**, with the output of the script after it went on suspend.

Thanks in advance for taking the time to read,
Lucas.

---

### Post by lvrma on 2016-12-30
Just edited a vital mistake that I've made: It's not a matter of whether the lid is open or closed, but instead a matter of the system going on suspend.
I had it set for it only go on suspend when the lid is closed so that's why it only happened then LOL my bad.

Anyway, here's the updates:
**lshw -C network** with the wifi working lists two drivers (**alx** for my ethernet and **ath10k_pci **for my wifi).
If I run the same command after suspend, it lists absolutely nothing.

I've tried creating suspend-modules scripts, and manually restarting the drivers through modprobe, but it does absolutely nothing as well.
It's as if the two drivers disappear completely after suspend. Any ideas?

---

### Post by jeremy31 on 2016-12-30
I only have one idea since I haven't seen the devices disappear from lspci results before
```
echo 1 | sudo tee /sys/bus/pci/rescan
```
And see if the wifi and ethernet devices reappear

---

### Post by lvrma on 2016-12-30
> **jeremy31 said:**
> I only have one idea since I haven't seen the devices disappear from lspci results before
```
echo 1 | sudo tee /sys/bus/pci/rescan
```
And see if the wifi and ethernet devices reappear

THAT SOLVED IT!!!!! It came back!!

So to make it permanent, should I just turn that line into a script, or is there another kind of fix now that the source of the problem has been identified?

---

### Post by jeremy31 on 2016-12-30
I wonder if [https://ubuntuforums.org/showthread.php?t=2345886&p=13580461#post13580461](https://ubuntuforums.org/showthread.php?t=2345886&p=13580461#post13580461) can be modified to work
```
sudo -H gedit /etc/systemd/system/wifi-resume.service
```
Enter the following
```
#/etc/systemd/system/wifi-resume.service
#sudo systemctl enable wifi-resume.service
[Unit]
Description=Restart networkmanager at resume
After=suspend.target
After=hibernate.target
After=hybrid-sleep.target

[Service]
Type=oneshot
ExecStart=/bin/echo 1 | tee /sys/bus/pci/rescan

[Install]
WantedBy=suspend.target
WantedBy=hibernate.target
WantedBy=hybrid-sleep.target
```

Save the file and exit gedit.  Then we can enable with
```
systemctl enable  wifi-resume.service
```
This will likely prompt for your password twice and then try it out

---

### Post by lvrma on 2016-12-30
Hmmm that one didn't work, I've also tried creating a script on sleep.d like [here]("http://askubuntu.com/questions/226278/run-script-on-wakeup") but it didn't do anything either...

---

### Post by jeremy31 on 2016-12-30
Could try a small edit
```
#/etc/systemd/system/wifi-resume.service
#sudo systemctl enable wifi-resume.service
[Unit]
Description=Restart networkmanager at resume
After=suspend.target
After=hibernate.target
After=hybrid-sleep.target

[Service]
Type=oneshot
ExexStartPre=sleep 5
ExecStart=/bin/echo 1 | tee /sys/bus/pci/rescan

[Install]
WantedBy=suspend.target
WantedBy=hibernate.target
WantedBy=hybrid-sleep.target
```
See if adding ```
ExexStartPre=sleep 5
```
Under service and see if it was trying to execute to quickly

---

### Post by lvrma on 2016-12-30
ExecStartPre didn't work either. It seems when I take it out of suspend there's not even a Wifi icon. A few seconds after I log in it shows up on the panel saying there's no connection (not recognizing the adapter).
Maybe a script to run [COLOR=#000000][FONT=&quot]echo 1 | tee /sys/bus/pci/rescan[/FONT][/COLOR] after I log in. I've tried adding it to my .profile, but there's a sudo command involved. So instead I've added it to /etc/rc.local, but it didn't work either..

---

### Post by #&amp;thj^% on 2016-12-30
> **lvrma said:**
> ExecStartPre didn't work either. It seems when I take it out of suspend there's not even a Wifi icon. 
Will this work when there is no Network icon visible?
```
killall nm-applet && nm-applet & 
```
And if it dose appear do you now have networking?...if not you could try with the original script as described above with:
```
sudo systemctl enable wifi-resume.service
```
Not sure what is going on with Network Manager as of Late but plenty of posts out there with similar issue's

---

### Post by The Cog on 2016-12-30
Some time ago I got fed up with Network Manager's tendency to go into a sulk, and installed wicd instead.
I like wicd - it Just Works (TM).
You should install package wicd before you remove package network-manager of course.

EDIT: Useful reference:
[https://ubuntuforums.org/showthread.php?t=1568403](https://ubuntuforums.org/showthread.php?t=1568403)

---

### Post by praseodym on 2016-12-30
Hi,

SUSPEND/HIBERNATE has problems since systemd is in use. Try this solution:

```
sudo touch /lib/systemd/system-sleep/wakeon_suspend.sh
```

Add this to this file:
```

#!/bin/sh
 case $1/$2 in
  pre/*)
    echo "activate $2..."
     /bin/systemctl stop network-manager.service
      /sbin/modprobe -rf ath10k_pci
    ;;
  post/*)
    echo "wakeup from $2..."
     /sbin/modprobe ath10k_pci
      /bin/systemctl start network-manager.service
    ;;
esac
```

Set the exec flag:

```
sudo chmod a+x /lib/systemd/system-sleep/wakeon_suspend.sh
```

From here:

[https://forum.ubuntuusers.de/topic/nach-16-10-installation-kein-internet-mehr-nac/2/#post-8652643](https://forum.ubuntuusers.de/topic/nach-16-10-installation-kein-internet-mehr-nac/2/#post-8652643)

---

