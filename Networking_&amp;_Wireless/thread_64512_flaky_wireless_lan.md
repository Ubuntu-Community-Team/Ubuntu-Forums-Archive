---
title: "flaky wireless lan"
date: 2005-09-11
forum: Networking &amp; Wireless
---

### Post by linuxgrrl on 2005-09-11
I have a wireless lan using a usb interface with a  prism2_usb driver.
I got it to connect using the instructions in the linux-ng-wlan package.  However, it disconnects after a few minutes. dmesg gives the following:

usb 1-1: new full speed USB device using ohci_hcd and address 4
ident: nic h/w: id=0x8010 1.0.0
ident: pri f/w: id=0x15 1.1.3
ident: sta f/w: id=0x1f 1.7.1
MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/12
PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00
p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
linkstatus=CONNECTED
wlan0: no IPv6 routers present
linkstatus=DISCONNECTED (unhandled)
hfa384x_dowrid: ctlx failure=REQ_TIMEOUT
hfa384x_dowrid: ctlx failure=REQ_TIMEOUT
hfa384x_docmd: ctlx failure=REQ_TIMEOUT
p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.

how can  fix this? 
thx.

---

### Post by mlomker on 2005-09-11
That message can indicate that you have a typo in one of your configuration files.  How are you assigning your ESSID?  Are you using iwconfig from a command line or a network configuration applet?

If you are using gnome then you should download a copy of [GTK wifi.](http://ubuntuforums.org/showthread.php?t=34645)

---

### Post by linuxgrrl on 2005-09-13
Thanks for your reply.

I'm not sure if any of this is right or wrong, but here's what I'm doing to connect:
1.  when I plug in the wlan USB device, or at boot time, the prism2_usb module seems to load automaticaly (shows up in dmesg and lsmod)

2. per the instructions that came with linux-wlan-ng, I created a file called /etc/hotplug/usb/prism2_usb that contains the commands necessary to load the linux-wlan-ng drivers:

wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

wlanctl-ng wlan0 lnxreq_autojoin ssid="MY_SSID" authtype=opensystem 

dhclient wlan0

3. through experimentation, it seems that if I unplug the USB device, do "modprobe prism2_usb doreset=1",  then manually run the above script, the connection is reliable.  [The connection sometimes works automatically at boot time, sometimes not, but is never reliable in that case (even with the "modprobe" line added to the beginning of the script)]

4. so my question: is there a way to have Ubuntu NOT try to configure the interface on its own at boot time, but just to have this script run at the very end after everything else (even GDM) starts?  Would that even work (since it seems happiest if I first unplug, then replug the USB device)?  Or is there a better way entirely (I suspect so :)

FWIW, I tried inputting the SSID into the graphical network configuration widget in gnome but it did not seem to help (i.e., wlan0 did not exist after reboot).

thanks for any suggestions,

Mary

---

### Post by linuxgrrl on 2005-09-13
[QUOTE=mlomker]
If you are using gnome then you should download a copy of [GTK wifi.](http://ubuntuforums.org/showthread.php?t=34645)[/QUOTE]

OK, now I see that this is a different thing from the Gnome network tool so I will try it at home tonight.   Thanks for the suggestion.

---

### Post by mlomker on 2005-09-14
[QUOTE=linuxgrrl]3. through experimentation, it seems that if I unplug the USB device, do "modprobe prism2_usb doreset=1",  then manually run the above script, the connection is reliable.  [The connection sometimes works automatically at boot time, sometimes not, but is never reliable in that case (even with the "modprobe" line added to the beginning of the script)][/QUOTE]

The hotplug subsystem is what loads the files.  You could add the prism2_usb command to the /etc/hotplug/blacklist file and the system will not automatically load it--you will have to modprobe it yourself or create a script to do that.

FWIW, I hear that the USB wireless adapters are a real pain so it isn't just you.

---

