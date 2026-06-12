---
title: "ifconfig eth0 down hangs"
date: 2014-10-06
forum: Networking &amp; Wireless
---

### Post by Ujesh_Mohanan on 2014-10-06
I'm facing a weird issue. I have a device with LINUX kernel 3.10.7 and root file system 14.04.

After booting up, approx. 10 minutes after booting, the system hangs when I execute ifconfig eth0 down. I have made sure that eth0 is up before executing the down command.
The issue occurs even if I execute the ifconfig eth0 down command soon after booting up and waits for 10 minutes without making the interface up.

Any help would be very much appreciated.

---

### Post by varunendra on 2014-10-07
Welcome to the forums Ujesh!

Would be nice if you share with us what you are trying to achieve and what has this eth0 up/down to do with. Does it also freeze if you don't even bother with eth0 at all?

Would be even nicer if you use default fonts that are easier to read :)

---

### Post by Ujesh_Mohanan on 2014-10-07
Thank you Varun!

Basically I have a device with LINUX kernel 3.10.7. Recently I have upgraded its root file system from 12.04 to 14.04. The issue started showing up after this up-gradation. 
It freezes only if I execute ifconfig eth0 down and do not make it up for the next 10 minutes(approximately). If I'm able to make eth0 up before the system freezes, then there wont be any issues.

Sorry about the font in my previous post. That was a copy paste mistake.

---

### Post by varunendra on 2014-10-07
That's really interesting!

Please show us which card and driver you are using. Open a terminal (Ctrl-Alt-T) and post back the ouputs of -
```
uname -mr
sudo lshw -C network
```

Please also do this as an attempt to get some clues on what is happening in the background -

Run "ifconfig eth0 down" that causes the freeze, then check these logs :
```
tail -40 /var/log/syslog
dmesg | tail -40
```
..any hints there? Post back these outputs too.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

**PS:**
You can always edit your posts to make correction as and if required. For example, to correct the fonts, you may click on "Edit Post" below your first post > highlight all the text with your mouse cursor > click on the 2nd icon from left above the edit box (two **AA's** with a [COLOR="#FF0000"]cross[/COLOR] mark on them) to remove the extra formatting from the selected text. :)

---

### Post by Ujesh_Mohanan on 2014-10-08
[COLOR=#000000]Thank you for taking time to look into this Varun.

[/COLOR][FONT=trebuchet ms]Please find the output of the commands below.
[/FONT]
```

root@JESM-010001:~#uname -mr
3.10.17 armv7l

```

```

root@JESM-010001:~# lshw -C network
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: e0:c7:9d:34:90:28
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=wl18xx_driver driverversion=3.10.17 firmware=N/A link=no multicast=yes wireless=IEEE 802.11abgn
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: eth0
       serial: d8:b8:f6:01:00:01
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=fec driverversion=Revision: 1.0 duplex=full ip=128.88.159.139 link=yes multicast=yes port=MII speed=100Mbit/s


```

Regarding logs, once the system freezes, I need to manually reset the device in order to enter any command. When I check there is nothing in my /var/log/syslog and /var/log/messages. 

And thanks for the formatting tip.

---

### Post by varunendra on 2014-10-08
Hmm.. Arm based systems and the functioning of OS on them is mostly beyond my knowledge or experience, so may not offer any significant help with this. But I didn't mean to run the last two commands _after_ the freeze. Run them before the system freezes (since you mentioned it normally takes about 10 minutes before freezing). Any of the last minute messages may give us useful hints.

By the way, the last session's messages, if not found in the current 'syslog' file, can be found in 'syslog.1' file. So take a look in that if the system is freezing immediately and the current syslog doesn't contain last session's messages.

In the meanwhile, please also post the output of -
```
modinfo fec
```

---

