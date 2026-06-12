---
title: "Which is the best network manager?"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by Mogurijin on 2008-02-25
Hi everyone. My wireless is connected and working. Well mostly. After optimizing (through sysctl.conf) and disabling ipv6 (Firefox and Ubuntu) I still only get about half to two-thirds of the internet speed I do in Windows XP. In Windows I get between 3 and 4 Mbps, while in Ubuntu I get about 2Mbps. This is better than when I started (>900Kbps), I would like to get better.

I think I would like to switch the default network manager (correct me if my terminology is incorrect) from the Gnome one to something else. I've seen Wifiradar and WCID (or something like that) pop up.

So my question is, which is the best (in your opinion) network manager for Ubuntu. And a reason would be nice.

Thank you!

EDIT: My speeds were fine in Feisty Fawn. I didn't have to do anything (short of using ndiswrapper for my drivers) for the speed. This is now in Gutsy that I'm having these issues.

---

### Post by kevmitch on 2008-02-25
I would definitely recommend wpasupplicant if you are not going to use one of the gnome/kde ones. It has a nice gui as well as a very powerful .conf file in the /etc/ directory. 

As far as the speed issues that may have more to do with your actual wifi driver. What chip/driver are you using?

---

### Post by jblackthorne on 2008-02-25
The GUIs you are mentioning are just that, GUIs.  Well, wpa_supplicant is not a gui at all:

[http://en.wikipedia.org/wiki/Wpa_supplicant](http://en.wikipedia.org/wiki/Wpa_supplicant)

WICD, as a GUI, is a bit of an exception in that it ships with other drivers, such as madwifi, you can try.  However, in general, your driver and driver configuration underneath the GUI are combined to be the bottlenecks.  So, the question is, can you improve upon the driver and configuration you are currently using?  To answer that, maybe research your wifi chipset driver to see what others might have found.  You can find this:

sudo lwhw -vv : shows system hardware
ifconfig : shows you the name of configured network interfaces
dmesg : normally will contain the name of the current wireless driver somewhere in there

Hope this helps and good luck.

---

### Post by imdano on 2008-02-25
Wicd doesn't actually ship with other drivers, it just lets you choose which driver wpa_supplicant should try to use when it authenticates.  It's the equivalent of what goes after the "-D" in (for example) ```
wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -B -D <driver goes here>
```

---

### Post by jblackthorne on 2008-02-25
Thanks for the corrections.  I did not realize that wpa_supplicant shipped with a client.  Learn something new every day :)

---

### Post by Mogurijin on 2008-03-07
Sorry about being slow to respond. I kinda forgot that I posted this :oops:.

Well, I'm using a Netgear wireless adapter. I have it going through ndiswrapper. Like I said before, the driver and everything worked fine in 7.04. I've seen were people had reported increased speeds with different network managers.

And by the way. My Ubuntu install is kinda hosed at the moment since Wicd took out the default manager and now I can't get an internet connection at all. Instead of messing with transferring files from my Windows install, I'll probably just reinstall.

---

### Post by Paris Heng on 2008-03-07
WICD is the best so far, it having no problems with variety of driver and NIC card.

Ref: [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

