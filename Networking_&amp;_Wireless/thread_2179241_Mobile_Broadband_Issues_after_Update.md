---
title: "Mobile Broadband Issues after Update"
date: 2013-10-07
forum: Networking &amp; Wireless
---

### Post by Qadeer_Ahmad_Janjua on 2013-10-07
I have recently switched from Windows to Lubuntu 13.04. My laptop is Dell D620 and I use a Huawei EVDO Mobile Broadband device to connect to internet.
Now after a fresh install of Lubuntu 13.04, my connection of Mobile Broadband connected within seconds. But then I used 'sudo apt-get update' and updated the software. After the update, everything is working great except Broadband connection. It simpley DOES NOT connect to internet. Some times it does connect after several minutes and multiple tries and that when I plug EVDO device into a different USB port.
Also please note that in terminal 'vnstat' shows 'ppp0 disabled'.
I have deleted and re-created the Mobile Broadband connection several times and out of desperation did clean install of Lubuntu 13.04 a couple of times too, but the problem persists; the Mobile Broadband simply won't connect to internet.
Also, everytime I click on the Broadband connection to connect, it's name changes automatically. Sometimes it's just EVDO, some times it's 'label' etc.
I have searched on the internet to find that some other users are facing same problem but without any solution in sight. Please help. Right now I am posting this message from the same Broadband connection which connected after retries which spanned 20 minutes.
Please help.

---

### Post by Qadeer_Ahmad_Janjua on 2013-10-09
[COLOR=#000000]I have recently switched from Windows to Lubuntu 13.04. My laptop is Dell D620 and I use a Huawei EVDO Mobile Broadband device to connect to internet.[/COLOR]
[COLOR=#000000]Now after a fresh install of Lubuntu 13.04, my connection of Mobile Broadband connected within seconds. But then I used 'sudo apt-get update' and updated the software. After the update, everything is working great except Broadband connection. It simpley DOES NOT connect to internet. Some times it does connect after several minutes and multiple tries and that when I plug EVDO device into a different USB port.
[/COLOR]
[COLOR=#000000]Also please note that in terminal 'vnstat' shows 'ppp0 disabled'.[/COLOR]
[COLOR=#000000]
I have deleted and re-created the Mobile Broadband connection several times and out of desperation did clean install of Lubuntu 13.04 a couple of times too, but the problem persists; the Mobile Broadband simply won't connect to internet.[/COLOR]
[COLOR=#000000]
Also, everytime I click on the Broadband connection to connect, it's name changes automatically. Sometimes it's just EVDO, some times it's 'label' etc.[/COLOR]
[COLOR=#000000]I have searched on the internet to find that some other users are facing same problem but without any solution in sight. Please help. Right now I am posting this message from the same Broadband connection which connected after retries which spanned 20 minutes.[/COLOR]
[COLOR=#000000]

A kind person suggested something at [/COLOR][https://plus.google.com/u/0/118161840059705215233/posts/E4kUsKvZ6Ec](https://plus.google.com/u/0/118161840059705215233/posts/E4kUsKvZ6Ec) to which my reply was following

"[COLOR=#404040][FONT=Roboto] I acted upon your suggestion to login with older kernel and I also used current kernel to login with Lubuntu Netbook selected at Login screen: both of these things gave the same result; that Broadband connected to Internet within seconds but only for the first time. If I tried to disconnect and then reconnect, either Network Connections menu would get stuck or it simply won't connect again until after the restart.[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]Secondly; a bizarre thing is that on a normal login (i.e. without old kernel or Lubunt Netbook) I am able to connect Broadband if I put EVDO device into a USB port, then click on connect but it won't. Then I would insert the device into another USB port to connect and it will connect immediately.[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]Another peculiar thing is that if/when Broadband is connected, it's connection name changes. Sometimes it's 'Label, sometimes it's 'EVDO', etc.[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]After the clean install and before update, Broadband used to connect within 5 seconds without any problem.[/FONT][/COLOR]"

So the issues is unresolved. I posted this question on this forum before and at askubunut too, but no one replied. Please help.

---

### Post by varunendra on 2013-10-10
Welcome to the forums Quadeer !

Taking multiple attempts to get recognized is a common issue in GSM/3g modems, but creating multiple names is not. Some of these devices need to be 'Ejected' or reset after changing their 'mode' (and accordingly, PID), which sometimes doesn't happen automatically. In that case, removing > re-inserting does the job.

Please plug in the modem, and post back the outputs of the following -
```
lsusb
dmesg | tail -20
```

---

### Post by cariboo on 2013-10-10
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Qadeer_Ahmad_Janjua on 2013-10-11
Dear varunendra:

Thank you for responding. Well, reinserting the EVDO device and the long wait for connection is quite irritating. But why does the problem occurs AFTER the Update and not BEFORE the Update? Anyway, here is the result of lsusb

> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E169/E620/E800 HSDPA Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


And here is the result of dmesg | tail -20
> [  282.072844] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  282.088214] scsi 12:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
[  282.091202] scsi 12:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[  282.113192] sr1: scsi-1 drive
[  282.114624] sr 12:0:0:0: Attached scsi CD-ROM sr1
[  282.117000] sr 12:0:0:0: Attached scsi generic sg3 type 5
[  282.118372] sd 12:0:0:1: Attached scsi generic sg4 type 0
[  282.131198] sd 12:0:0:1: [sdc] Attached SCSI removable disk
[  282.424064] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  282.505088] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  286.812024] b43-phy0: Radio hardware status changed to DISABLED
[  302.016108] b43-phy0: Radio hardware status changed to ENABLED
[  302.180150] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  302.253507] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  304.099315] PPP BSD Compression module registered
[  304.129160] PPP Deflate Compression module registered
[  602.505688] systemd-hostnamed[3403]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  682.684977] usb 1-7: USB disconnect, device number 4
[ 1169.459095] perf samples too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 1703.970542] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.


I'll be grateful for any help. :)

---

