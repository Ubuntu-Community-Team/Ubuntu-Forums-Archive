---
title: "No wireless until after a reboot"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by lobo78 on 2006-11-11
I have successfully been able to get wireless working with ndiswrapper on a Dell Latitude D620.  I frequently access 3-4 different access points throughout the week.  If I boot up near an access point that I didn't use the previous time, Ubuntu will fail to get an IP address on boot up.  

Then, I try to get it working manually.  At first, I try the Network Manager, but I can never get it to work.  Then I start messing with iwconfig and the /etc/network/interfaces file.  I'll scan with "iwlist eth1 scanning".  Then I set the following:
sudo iwconfig eth1 essid *****
sudo iwconfig eth1 ap **********
sudo iwconfig eth1 ad-hoc
sudo iwconfig eth1 key off (if the wireless has WEP turned off)

Then I try either:

sudo dhclient eth1
or
sudo /etc/init.d/networking restart

But it never gets an ip.  The only thing that works is to set the essid and mode in /etc/network/interfaces and then reboot.  So, I'm wondering what I could be missing.  This is the case with WEP turned off.

Here is what my iwconfig typically looks like when it's not working:

eth1      IEEE 802.11b  ESSID:"******"  
          Mode:Managed  Frequency:2.412 GHz  Access Point:   
          Bit Rate:11 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Like I said, it doesn't matter if I change the mode or set the ap.  Generally, the essid gets set fine, but it won't pick up the AP no matter how many times I try to set it.  Is there an option I am forgetting?  Do the settings in the interfaces file interfere with the manual settings of iwconfig?  How do I get this to work without having to boot up twice every time I go somewhere?

---

### Post by FrodoB on 2006-11-11
Try using the ifup and and ifdown command they use the setting that are applied on startup and shutdown and may resolve your issue:

$ sudo ifup eth1 up

$ sudo ifdown eth1 down

Am I understanding your concern correctly?

---

### Post by lobo78 on 2006-11-11
Thanks FrodoB.  However, I have tried ifup and ifdown, also, and I get the same result as I get from using dhclient, which is that it sits there sending out broadcast dhcp requests, but never resolves with an ip address.  Any other ideas?

---

### Post by FrodoB on 2006-11-11
The only thing that I can suggest is for you to post the outputs of
the following just after a reboot when everything is working:

dmesg    # only the part that is relevant to your device

iwconfig

ifconfig

netstat -rn

contents of /etc/network/interfaces

Then post everything again except the interfaces file when you have tried manual configuration. By the way Ad-Hoc may or may not work on your card and Linux depending upon what you have for drivers and when you do that you are not going to be talking to the access point that you just set up.  Managed mode is for access point networking.

---

### Post by sgornick on 2007-01-22
I am having a similar experience so I filed a bug report.  It has not yet been confirmed, but if you are still experiencing the same problem, perhaps something from the bug report will help get you further.  If you learn anything that will help to confirm the issue please add it to the bug report.
[https://launchpad.net/ubuntu/+source/netbase/+bug/80499](https://launchpad.net/ubuntu/+source/netbase/+bug/80499)

---

