---
title: "Wifi connects to only one network Ubuntu 16.04lts"
date: 2016-12-02
forum: Networking &amp; Wireless
---

### Post by tia911 on 2016-12-02
Hi, I'm a newbe and I'm having an issue.
I've already looked for a solution in the forum but it seems no one got the same.
I did a clean installation of Ubuntu 16.04 lts and I modified, following the relative guide, some parameters to keep active bluetooth after suspension.
Now I can't connect the wifi to a different network. I can see all of them but if I try to connect to them the sigh keep rotating without ask nether the wpa key.
What can I do??

This is what I see if I try to edit the other connections.

---

### Post by TheFu on 2016-12-02
Welcome to the forums.
Just a guess, but what does **rfkill list** show? Is it locked?  Open a terminal and run it.
```
$ rfkill  list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: hci0: Bluetooth
        Soft blocked: yes
        Hard blocked: no

```
See how my bluetooth is soft blocked?  I did that on purpose because BT is inherently non-secure and I want to manually enable it to be able to use it. Didn't hard block it so a BIOS change isn't needed to enable it.

Don't know if this is the issue, but even if you eliminate it, that would be helpful.

---

### Post by tia911 on 2016-12-05
Hi, thanks for the answer.
On terminal I receive the list without blocked devices.
I've been struggling a lot with the bluetooth because it used to don't work properly on my command. So I ended my nightmare keeping it always on.
I can be connected only on the extended network and It doesn't let me connect neither  to the main router.Tried with completely different one and the result is rotating symbol,no wpa question and no answer.

Terminal :

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
10: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by TheFu on 2016-12-05
I'm unable to help with wifi. I don't do it the normal way. Sorry.  There is a **wifi-info** script referenced in the forums. If you grab that and post the output (please use code tags), someone smarter might be able to help.

---

### Post by tia911 on 2016-12-05
which kind of code?? the whole result??

---

### Post by tia911 on 2016-12-05
Here the zipped txt file

---

### Post by karl96 on 2016-12-05
Hi,

You can run ```
journalctl -u NetworkManager
``` and see if anything looks suspect.

---

### Post by jeremy31 on 2016-12-05
It might be a bug in Network Manager with the list of wifi access points but from your script results only 2 access points are in range, the virginmedia and the virginmedia extender

---

### Post by TheFu on 2016-12-05
A few thoughts ....

* [https://ubuntuforums.org/showthread.php?t=2233283](https://ubuntuforums.org/showthread.php?t=2233283) shows how someone else got wifi working better with the same wifi chip. The modprobe stuff. You'll want to use **sudoedit** to modify the driver settings permanently.  They mention some wifi-router changes were needed to make things better as well. See #6 for router changes.

* The DNS settings don't look correct to me.  They point to a different subnet, but still a private address. That would be unusual in most home environments.  Cannot say how to fix it using a GUI, sorry.  Can you ping the DNS IPs listed in the file?  There are 3.  Wouldn't hurt to ping 8.8.8.8 and report whether that works.

* "code tags" are a forum thing to make console commands line up and much more readable.  Use "Adv Reply" to see that button.

Anyway, that's all that I can see.

---

### Post by tia911 on 2016-12-08
I sorted it out uninstalling the normal network manager and installing wicd. Reinstalling the normal one with a purge unistall it didn't work.

---

### Post by TheFu on 2016-12-08
> **tia911 said:**
> I sorted it out uninstalling the normal network manager and installing wicd. Reinstalling the normal one with a purge unistall it didn't work.

I purge nm-* and install wicd-curses too.  While not perfect, it does work for non-trivial network configurations, at least for the wifi part.
If this is solved, please mark it "SOLVED" using thread tools.

---

