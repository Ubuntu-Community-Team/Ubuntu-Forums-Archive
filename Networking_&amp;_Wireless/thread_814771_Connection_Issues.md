---
title: "Connection Issues"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by djuta on 2008-06-01
My Internet connection seems to be going off and on at its own will. The network notification thing tells me im still connected, but when i use any application that requires the internet it doesn't connect.Any Ideas?

---

### Post by prshah on 2008-06-01
> **djuta said:**
> My Internet connection seems to be going off and on at its own will. The network notification thing tells me im still connected, but when i use any application that requires the internet it doesn't connect.Any Ideas?

Are you using wireless? In that case, maybe power management is turning off the wireless. You can change this behavior. If you are using wireless, post back here for the commands.

If you are using a wired connection, open a terminal (Applications-Accessories-Terminal), then give the following command and post the output here. ```

dmesg | grep link

``` That will tell us if the link is being interrupted for any reason (bad cable, router power supply, collisions, renegotiation, etc)

---

### Post by djuta on 2008-06-01
yes i am using wireless

---

### Post by arachal on 2008-06-01
Hi. I am new to Ubuntu.  My friends son just installed it for me.  I cannot get my wirless lan to work.  Can anyone help?  I have a Compaq Presario V4000.:confused:

---

### Post by prshah on 2008-06-01
> **djuta said:**
> yes i am using wireless

Try using the following commands to turn off power management for your wireless:```

sudo iwconfig eth0 txpower fixed
sudo iwconfig eth0 power off
sudo iwconfig commit
```

The third command may give an error as "feature not supported" that can be ignored.

Either one of the first two commands should work and will take effect immediately, _until_ your next reboot. 

So give the commands, then surf for an hour or two to check if it is effective. If it is effective, you can add the commands to your "/etc/rc.local" to take effect on every reboot.

Note that in the rc.local file, the last line should not be disturbed (ie, "exit 0")

---

### Post by prshah on 2008-06-01
> **arachal said:**
> Hi. I am new to Ubuntu.  My friends son just installed it for me.  I cannot get my wirless lan to work.  Can anyone help?  I have a Compaq Presario V4000.:confused:

Why not try my step-by-step guide (with expected outputs) ([http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260)) to set up your wireless network card? If you run into any problems, post back which step you are stuck at.

Note that the Presario V4000 carries an Intel 2200 wireless card, which _should_ be detected automatically. So I suggest that you start from step 9.

---

### Post by djuta on 2008-06-01
thank you very much for the help

---

