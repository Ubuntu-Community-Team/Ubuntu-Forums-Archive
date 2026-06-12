---
title: "D-Link DWl G122 Rev. A2"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by braganfamily on 2008-05-30
I am using the windows XP driver installed with ndiswrapper GUI.  The problem is that I keep losing my connectivity.  The usb dongle just goes dead at various times.  The weird thing is that when I installed Ubuntu Hardy H, I had the usb and a wired connection.  The USB worked fine for a couple of days without having to install any driver.  Then couple days later, it went completely dead, so, I installed the windows driver with ndiswrapper.

Is there a way to re-establish the usb antenna without rebooting?

Any ideas on:

1.  Why was it working originally?  I don't think this chipset is supported out-of-the box.

2.  Why does it keep dropping out with the windows driver?

thanks for any help.

bobby

---

### Post by braganfamily on 2008-05-31
a gentle bump...

Not sure why i keep losing my usb wireless.  But it did stay up most of the day!

---

### Post by prshah on 2008-06-02
> **braganfamily said:**
> The problem is that I keep losing my connectivity.  The usb dongle just goes dead at various times.

Try using the following commands to turn off power management for your wireless:```

sudo iwconfig eth0 txpower fixed
sudo iwconfig eth0 power off
sudo iwconfig eth0 commit
```

**Replace eth0 with the actual name of your interface.**

The third command may give an error as "feature not supported" that can be ignored.

Either one of the first two commands should work and will take effect immediately, _until_ your next reboot. 

So give the commands, then surf for an hour or two to check if it is effective. If it is effective, you can add the commands to your "/etc/rc.local" to take effect on every reboot.

Note that in the rc.local file, the last line should not be disturbed (ie, "exit 0")

---

### Post by braganfamily on 2008-06-02
Thanks for the suggestion.  I'll give it a try.

Also, I just discovered that every time my usb wireless drops out, my usb printer does, also.  Seems like all the usb ports go out at the same time.

bobby

---

### Post by braganfamily on 2008-06-02
gave it a try, message 

bobby@bobby-desktop:~$ sudo iwconfig eth0 txpower fixed
[sudo] password for bobby: 
Error for wireless request "Set Tx Power" (8B27) :
    GET failed on device eth0 ; Operation not supported.
bobby@bobby-desktop:~$ sudo iwconfig eth0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth0 ; Operation not supported.


is that odd?

bobby

---

### Post by prshah on 2008-06-02
> **braganfamily said:**
> gave it a try, message 

bobby@bobby-desktop:~$ sudo iwconfig eth0 txpower fixed
Error for wireless request "Set Tx Power" (8B27) :
    GET failed on device eth0 ; Operation not supported.
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth0 ; Operation not supported.


Err is eth0 your actual wireless device? If you are not sure, can you post the output of ```
iwconfig
```

Beyond this, I have nothing... sorry!

---

### Post by ivra on 2008-06-14
I have v same problem with d-link g122 C1 on 7.10 Gutsy and I plug out and after plug in to make this usb to work. On hardy i have no problem with this.

---

