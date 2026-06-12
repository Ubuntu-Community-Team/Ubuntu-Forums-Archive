---
title: "HELP: BCM43xx Kubuntu Hardy"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by csall on 2008-02-28
I just install a fresh copy Kubuntu Hardy alpha 5 I believe. Right off I noticed my wireless card was automatically recognized. However, the LED for my wireless was not on. After researching awhile I came a cross a bug post that referred me to install b43-fwcutter.

sudo apt-get install b43-fwcutter

then I rebooted. Nice, I noticed the LED turned on for my wireless. So, I was hoping everything was all good to go. Wrong. haha. I checked my iwconfig output.

[B]Here is the ouput of my iwconfig:
[/B]
craig@LAPTOP:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I noticed, something different I had never seen before. wmaster0. Anyways, I then setup my network as usual. Here is my output of my wireless card after.

wlan0     IEEE 802.11g  ESSID:"GRUNDLE"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I then do a dhclient to try t renew an IP. No success. It seems I'm not able to see any wireless networks for some reason. I even tried to get it to connect directly to the AP by:

sudo iwconfig wlan0 ap ##:##:##:##:## 

Still no success. I can't seem to find out what's going wrong. I must be on the right track for as I said the wireless light is on and wasn't before. Any help is greatly appreciated. Thanks in advance!

---

### Post by dahouse on 2008-03-04
I got it working under Hardy Alpha 5.


I uninstalled Bcm43 fwcutter and b43 fwcutter both in synaptic, then opened up the terminal and wrote this to reinstall b43, but with a text menu

sudo apt-get install b43-fwcutter


This automated the installation, downloaded the firmware (via ethernet) and after a 3 minute pause, got my wireless running. *Do it from the terminal, not Synaptic*


In my previous installation (GUTSY), the Network Card LED turned on but I still didn't get the wireless running. I had to enable roaming mode in the network manager.

---

### Post by daemonfly on 2008-06-27
> **dahouse said:**
> I got it working under Hardy Alpha 5.


I uninstalled Bcm43 fwcutter and b43 fwcutter both in synaptic, then opened up the terminal and wrote this to reinstall b43, but with a text menu

sudo apt-get install b43-fwcutter


This automated the installation, downloaded the firmware (via ethernet) and after a 3 minute pause, got my wireless running. *Do it from the terminal, not Synaptic*


Refference for anyone else with a Dell Latitude c640 - the above is what worked for me. B43-fwcutter wasn't installed at all (on Xubuntu 8.04), entered the command above into terminal, answered "yes" to the ascii graphics window prompt, and it installed what it needed. Then went into Network Settings, and enabled the Wireless Connection.

Edit: well, that fixed it until the next reboot. Now, every reboot, I have to go into Network settings, reenable it, close out, go back in a 2nd time, and this 2nd time, the WPA key is now gone, so I reenter it, finish up, and wireless is working again...

2nd edit: Solution: do the b43-fwcutter procedure above, but don't use bcm43xx, use the "b43" module. Add "b43" to /etc/modules (remove any other bcm43xxx, etc...). Wireless works perfect, no screwing around with any settings, and no ndiswrapper either. This is for the Broadcom BCM4306 card in Dell Latitude c640, "lspci -nn" lists it as 14e4:4320.

---

