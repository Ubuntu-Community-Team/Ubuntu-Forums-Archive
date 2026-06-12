---
title: "Realtek RTL8188CE WiFi issue on Lubuntu 14.04"
date: 2014-08-08
forum: Networking &amp; Wireless
---

### Post by marcos11 on 2014-08-08
Hello, everyone!

First, sorry for my english... I'll do my best! Also, I'm relatively new to Linux, and I never faced this kind of problem before, so I'm completely ignorant to this matter.

I am using a Lubuntu 14.04 fresh install. During installation, it was asked for internet connection, and I connected to my house's wifi. In fact, until now I am able to connect to my house wifi without any trouble.
The problem is that I cannot use wifi anywhere else. Sometimes the available connections don't even show up and, when they do, it never establishes connection.

Any clue about what can be causing it? I'm not very sure about where to start, once my network adapter showed to work well in one place. I know it is not much, but it suggests that at least my system recognizes it.

This is what I got from my wireless info:

```
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: AzureWave AW-NE139H Half-size Mini PCIe Card [1a3b:1139]
    Kernel driver in use: rtl8192ce
```

Thanks in advance!

---

### Post by ajgreeny on 2014-08-08
Do you mean the panel applet does not show so you are unable to connect to networks?

I'm not using Lubuntu but I think there is a bug where the network applet is not in the startup applications list in all cases but has to be added after installation and once in a user session.  I will find the details for you.

OK, here you are, from the release notes [https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/Lubuntu:-](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/Lubuntu:-)
> Applications

Network  indicator on the panel may not start at login. You can start it  manually by launching "nm-applet" in a terminal. Some others autostarted  applications may also be affected (such as automatic updates). See [1308348]("https://bugs.launchpad.net/bugs/1308348") for the details and the ETA for the fix. To turn on nm-applet in autostart, follow [these instructions]("http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html") It may need two reboots to fully work.
And the bug itself:-
[https://bugs.launchpad.net/bugs/1308348](https://bugs.launchpad.net/bugs/1308348)

---

### Post by marcos11 on 2014-08-09
Thanks for your reply!

But no, that's not my problem... nm-applet is not working, but it doesn't bother me (I'm using Wicd network manager). I am being unable to connect to wifi in all places but my home.

Unless it has something to do with nm-applet not working. When I try to launch nm-applet from terminal I get this:

```
mfcord@philinus:~$ nm-applet
nm-applet-Message: using fallback from indicator to GtkStatusIcon
```

Thanks!

---

### Post by ajgreeny on 2014-08-10
Sorry, I have no knowledge of wicd so can't really help you on this.

---

### Post by praseodym on 2014-08-10
Please check
```

wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
It install an Add-on with a lot of encryption possibilities, too.

---

### Post by marcos11 on 2014-08-11
Thank you very much, **praseodym**! For the first time, WiFi is functional in my workplace. 

And thank you anyway, **ajgreeny** ;)

Changing this to solved.

---

### Post by praseodym on 2014-08-11
Glad its working. You may need to deactivate the network manager in autostart or uninstall it.

---

