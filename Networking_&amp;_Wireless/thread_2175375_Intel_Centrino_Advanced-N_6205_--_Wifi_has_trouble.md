---
title: "Intel Centrino Advanced-N 6205 -- Wifi has trouble connecting/constantly disconnects"
date: 2013-09-18
forum: Networking &amp; Wireless
---

### Post by alecbenzer on 2013-09-18
Copying info from askubuntu: [http://askubuntu.com/questions/343446/wifi-has-trouble-connecting-constantly-disconnects-in-ubuntu](http://askubuntu.com/questions/343446/wifi-has-trouble-connecting-constantly-disconnects-in-ubuntu)

I am trying to connect to my uni's public wifi in ubuntu. After an initial attempt that is usually successful, the connection drops after a few minutes (sometimes < 1). After that future attempts to connect may or may not be successful, but after a few initial successes I find myself completely unable to connect.


I had this issue with this laptop before. I ended up buying and installing a new wifi card and (if I remember correctly) installing the proprietary drivers for it, which seemed to fix the issue. However, after reinstalling ubuntu over the summer the problem has re-surfaced, and now I can't seem to find the proprietary drivers I thought I had installed when I last had this issue.


I do not have connectivity issues in windows on this laptop, so I'm pretty sure this is a software/driver issue.


This is my wifi card's lspci entry:

[FONT=courier new]03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
[/FONT]
and my lsmod: [http://paste.ubuntu.com/6041598/](http://paste.ubuntu.com/6041598/)


I tried implementing the solution mentioned here: [Very slow connection on an Intel(R) WiFi Link 5100 AGN]("http://askubuntu.com/questions/66810/very-slow-connection-on-an-intelr-wifi-link-5100-agn/335080#335080"), which did not help my connectivity issues.

Also see the askubuntu thread linked at the top for some other things I've tried that didn't help.

---

### Post by alecbenzer on 2013-09-30
bump -- anyone have any ideas?

---

### Post by varunendra on 2013-10-02
> **alecbenzer said:**
> bump -- anyone have any ideas?

It seems you have already tried almost everything possible. Only a few more things remaining -

1) As per your last pastebin on the askubuntu post, you seem to be using kernel 3.8.0-19. Try doing an update to upgrade it to the latest (3.8.0-31) and see if there's any improvement with the newer driver -
```
sudo apt-get update
sudo apt-get dist-upgrade
```

2) Try [post=12640479]completely disabling IPv6[/post] by editing your /etc/sysctl.conf file.

3) Try adding yet another parameter to your /etc/modprobe.d/iwlwifi.conf file - "bt_coex_active=N"
```
sudo sed -i 's/^options.*/& bt_coex_active=N/' /etc/modpeobe.d/iwlwifi.conf
sudo modprobe -rv iwldvm
sudo modprobe -v iwldvm
```

4) Have you also tried the connection on a Live CD/USB? Sometimes, too much customization also causes negative effects.

5) Was the power-management set to "Off" by default on wlan0 (in iwconfig)? The custom script you have in /etc/pm/power.d/wireless, seems to meant for that purpose, but it also disables the default script in /usr/lib/pm-utils/power.d/ directory. So unless it clearly helped it, you should try moving (or removing) that custom script -
```
sudo mv /etc/pm/power.d/wireless ~/Desktop
```

After trying these, if there is still speed drop, connection freeze issue, please run the wireless script again, and post back the fresh report here. Along with the report, please also post the output of -
```
ifconfig -a
sudo iwpriv wlan0
grep -iR [0-9a-z] /sys/module/iwlwifi/parameters/
```

---

