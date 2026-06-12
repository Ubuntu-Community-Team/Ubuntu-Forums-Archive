---
title: "Thinkpad T470p Intel 8265 Dual-band Wireless Dropping"
date: 2017-10-30
forum: Networking &amp; Wireless
---

### Post by red72 on 2017-10-30
I have a brand new Thinkpad T470p with Intel 8265 with a fresh install of 17.10.  The wifi continually drops and reconnects.  I see no indication the wifi is not working and am not sure how long it it is out, just web pages will not load.  Then after some time, and with my not doing anything, the pages will load.  I found [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1720532") which looks like the issue but not sure when it will be solved.  And since my new computer is practically unusable now I am hoping the community can help me figure out if there might be another solutions.
Thank you!
Patrick

---

### Post by ajgreeny on 2017-10-30
See **Wireless-info** in my signature, download it and run the script, then report back the output here or using [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) if the output is too large to add direct.

---

### Post by red72 on 2017-10-30
Hi, here you go - [http://pastebin.ubuntu.com/25852154/](http://pastebin.ubuntu.com/25852154/)
Thank you!
Patrick

---

### Post by jeremy31 on 2017-10-31
Moved to networking
See the first command on [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
Reboot

---

### Post by red72 on 2017-11-01
Hi,  I tried the first command but still have the same issue.  Just confirm, my default-wifi-powersave-on.conf file now looks like this:

[FONT=Courier New][connection]
wifi.powersave = 2
[/FONT]
Any other ideas?
Thank you,
Patrick

---

### Post by red72 on 2017-11-08
Hi, I am learned a few more things about my problem.  It only happens at work using a dlink DIR 600 router.  At home the connection is fine.  At work if I use a portable ravpower wd03 travel router to bridge the wifi then my wifi is fine -- this device is assigning the IP for my computer.  There are 30 devises on my work wifi and no other complaints.  Even a few Ubuntu machines and one 17.04.  The dlink router firmware is up to date.  Any suggestions how to trouble shoot this issue?

Thank you!
Patrick

---

### Post by jeremy31 on 2017-11-08
At work try ```
sudo modprobe -r iwlwifi && sleep 10 && sudo modprobe iwlwifi 11n_disable=8
```
See if makes an improvement

---

### Post by red72 on 2017-11-10
Hi  jeremy31, Thank you!  This seems to have worked.  I have only had one day in the office after running this command and I did not notice any wifi issues.  Let me give it one more day and then I will considered solved!
Best,
Patrick

---

### Post by jeremy31 on 2017-11-10
To make it use the setting automatically
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```

---

