---
title: "Network Manager Notifications"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Jepic Phail on 2009-11-05
My network notifications are.. well... they are just black boxes. Its a very minor issue, but I would like to either fix or remove the connection notification if it is possible.

:popcorn:

---

### Post by Jepic Phail on 2009-11-05
I haven't found the exact solution yet, but I think I am in the [right place]("https://wiki.ubuntu.com/NotifyOSD"). :lolflag:

---

### Post by sldavid on 2009-11-05
Assuming it will work for XUbuntu here's the solution I found for Ubuntu:

If I have visual effects set to none I get black notification bubbles. If I set the visual effects to normal, everything is, well, normal.

Hope that helps

---

### Post by Jepic Phail on 2009-11-06
> **sldavid said:**
> Assuming it will work for XUbuntu here's the solution I found for Ubuntu:

If I have visual effects set to none I get black notification bubbles. If I set the visual effects to normal, everything is, well, normal.

Hope that helps

Thanks. I appreciate your suggestion. 

Actually that was the first thing that came to my mind when I first encountered this problem. Unfortunately, Xubuntu's Appearances menu is vary foreign to that of Ubuntu's gnome menu, and although I could be in the wrong place, as far as I know I cannot make change to the visual effects setting.

Anyways, I think I have confirmed that this is a Notify problem. My /.cache/notify-osd.log shows two network notification entries, which I did not see. I saw just one black box, if I recall correctly.
```

[2009-11-05T20:36:40-00:00, NetworkManager ] Wireless Networks Available
Click on this icon to connect to a wireless network

[2009-11-05T20:37:39-00:00, NetworkManager ] ubuntu
Connection Established

```

Right now I am trying to isolate the problem to determined if this is somehow related to the network manager. I tried to trigger some non-network notifications, such as changing volumes and adjusting display brightness, but I was unsuccessful.

For what it's worth, I will make an update when I learn more.

---

### Post by Jepic Phail on 2009-11-06
Was able to duplicate the "black box" thing by switching from battery to AC power. Rather than actually figuring out the solution, I just disabled the notifications.

```

sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled

```

Logout/login afterwards and notifications should be gone. :)

Source: [http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/](http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/)

---

### Post by louieb on 2009-11-06
Is this an IBM laptop? I had  the same black hole and System Monitor was a blob of nothing. 
Anyway there is a fix. I found it here [http://ubuntuforums.org/showthread.php?p=8247769](http://ubuntuforums.org/showthread.php?p=8247769)

> 
The problem seems to be related to this bug [https://bugs.launchpad.net/ubuntu/+s...ti/+bug/416001]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001") and this one in freedesktop [https://bugs.freedesktop.org/show_bug.cgi?id=23668](https://bugs.freedesktop.org/show_bug.cgi?id=23668).

A potential fix is to edit your xorg.conf as in the Launchpad comment by Grant Bowman. I'm about to try this now.


---

### Post by Jepic Phail on 2009-11-06
:shock: I've seen the light... and.. and its beautiful! 

here is my /etc/X11/xorg.conf
```
Section    "Device"
    Identifier    "ATI"
    Driver        "radeon"
    Option        "AccelMethod" "EXA"
EndSection

```

I wonder if its normal for notifications to appear about 3cm from the top panel...

---

