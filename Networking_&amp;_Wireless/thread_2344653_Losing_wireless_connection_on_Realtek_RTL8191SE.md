---
title: "Losing wireless connection on Realtek RTL8191SE"
date: 2016-11-27
forum: Networking &amp; Wireless
---

### Post by inim on 2016-11-27
Hi,

I am using Xubuntu 16.10 on a Toshiba L505 laptop with a Realtek RTL8191SE. My problem seems similar to [https://ubuntuforums.org/showthread.php?t=2230943](https://ubuntuforums.org/showthread.php?t=2230943). My connection drops randomly every few minutes (2-3 times per hour). The same problem is not present on Windows or on Debian 8. I am relatively new to Linux. I googled for my problem, but did not find any solutions, especially for Xubuntu 16.

Thank you

---

### Post by inim on 2016-12-12
In case anyone is interested in this... After much searching online, I managed to solve my problem. I found the answer here: [http://askubuntu.com/a/622681/614845](http://askubuntu.com/a/622681/614845).  I just added the option "powersave=0" to my wifi profile at /etc/NetworkManager/system-connections/NAME_OF_PROFILE. I now have zero problems with my wifi.

There is something that could make my life easier though. Is there a way to make this option the default option for all new wifi profiles that I may add in the future?

---

### Post by Keith_Helms on 2016-12-14
As far as I can tell there's both no way to have that option added automatically and no way to set it using the network manager gui.

It would be easier to just disable power management entirely for your wireless adapter and not on a per network basis.  There are many posts out there with multiple different solutions, some of which no longer work.  Here are the most common suggestions.  For a 16.10 system, I'd probably start with suggestion 3.

1. Add the following to /etc/rc.local (substitute the name of your wireless adapter if not wlp3s0)
```
/sbin/iwconfig wlp3s0 power off
```
Problem: Apparently on newer releases using systemd, rc.local execution is now moved to earlier in the boot process and networking isn't started yet, so this doesn't work.
Workaround: Add a "sleep nn" (10,20,30) in front of the iwconfig command.  I tried this and it *sometimes *worked and sometimes didn't.

2. Create a script called /etc/pm/power.d/wireless and put the following in it:
```
#!/bin/sh
/sbin/iwconfig wlan0 power off
```

Do a chmod +x to mark it executable.
Problem: THAT didn't work for me either.  I stuck in a sleep 20 and it still didn't work.  It appears those directories are no longer used with systemd.

3. Let systemd handle it.  I haven't tried this solution, so I don't know if it works.
Go to /etc/systemd/system/.
  Create a file called root-resume.service and put the following text inside:
  ```
[Unit]
Description=Turn of wlan power management
After=suspend.target

[Service]
Type=simple
ExecStartPre= /bin/sleep 10
ExecStart= /sbin/iwconfig wlan0 power off

[Install]
WantedBy=suspend.target

```  Enable the root-resume service to be started at boot: 
  ```
sudo systemctl enable root-resume


```

4. What ended up working for ME:
I added the following line to my root crontab. I Executed
```
sudo crontab -e

```
And added the following to reuse the script I tried before
```
@reboot /etc/pm/power.d/wireless
```

So, fun times with Linux.  Solutions that used to work no longer do.  Directories that used to have scripts placed in them executed are now ignored.  Scripts that used to execute at a certain phase of startup now execute at a different time.

---

### Post by Bucky Ball on 2016-12-14
Considering your original issue is solved, you should mark this thread solved (see how in my signature) to help others. Good luck.

---

### Post by inim on 2016-12-16
@Keith_Helms: Thank you very much for your detailed answer. I will try your suggestions.

---

### Post by inim on 2016-12-16
@Bucky Ball: I am sorry. I forgot to do that.

---

