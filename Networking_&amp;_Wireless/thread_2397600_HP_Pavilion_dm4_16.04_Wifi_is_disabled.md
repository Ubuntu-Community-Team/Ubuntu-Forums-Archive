---
title: "HP Pavilion dm4 16.04 Wifi is disabled"
date: 2018-07-31
forum: Networking &amp; Wireless
---

### Post by smuthdev on 2018-07-31
Hello! Thanks in advance for any help. New to Ubuntu and just installed 16.04 on a spare laptop to start to learn it. It is a HP Pavilion dm4. I followed the steps for the wireless-info script and posted a link below.

My wifi is disabled, the wireless button (shared with f12) is not functioning, but I'm able to connect via wired connection.

wireless-info on pastebin: [http://paste.ubuntu.com/p/KS4WQGj4F6/](http://paste.ubuntu.com/p/KS4WQGj4F6/)

---

### Post by Autodave on 2018-08-01
This is probably not goin g to help, but this is the first thing that I do when something on a laptop won't work.  Power off and disconnect every cable. Remove battery. Wait 10 minutes. Reinstall b attery and power cable and power up. Does it work now?

---

### Post by chili555 on 2018-08-01
The issue of HP wireless being inoperable because of a hard block and therefore the usual wireless key not toggling wireless on and off is long-standing. There are only a few things you can try.

First, try removing the helper module hp_wmi and then try to switch the wireless on with the key combination. 

You could also try:

    ```
sudo modprobe -r hp_wmi
sudo rfkill unblock all
rfkill list all
```

Second, check the user guide for your HP laptop and be certain that the wireless key combination you are using is correct. Be certain that you are not using Fn+F12, for example, if the user guide says it is simply F12. On the other hand, if you are certain you are using the correct sequence, try the wrong sequence as an experiment; i.e., use Fn+F12 (or whatever your sequence is) if the user guide says it’s F12 and vice versa.

Next, you can remove the card, tape off pin 20 and re-insert it: [https://ubuntuforums.org/showthread.php?t=2150597](https://ubuntuforums.org/showthread.php?t=2150597)

You can, if all these steps fail, file a bug report against the module hp_wmi: [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Finally, in many, but not every case, a USB wireless will also be hard blocked for the same reasons. If you want to try one, be certain to try it within a return period.

I regret that there isn’t a better answer for HP laptops.

---

### Post by smuthdev on 2018-08-02
Autodave: I tried this, as well as pressing the power button a couple times when battery and ac cable were disconnected.

chili555
```
~$ sudo modprobe -r hp_wmi
~$ sudo rfkill unblock all
~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: i2400m-usb:1-1.4:1.0: WiMAX
    Soft blocked: yes
    Hard blocked: no

```

Will work on further steps and post results. Thanks.

---

### Post by gobbie2 on 2018-09-14
Did you find a resolution?  I am having the same issue.

---

