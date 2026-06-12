---
title: "Realtek RTL8192, intermittent and slow data transfer"
date: 2017-07-16
forum: Networking &amp; Wireless
---

### Post by john_ladasky on 2017-07-16
Hi there,

I've got a fairly new, dual-boot system running Ubuntu Gnome 17.04 and Win10.  My system is equipped with an ASUS PCE-N15 PCI Express Wireless Adapter.  I purchased this particular wireless NIC because I found it on a list of Linux-compatible devices (and I will attempt to find the list again, if anyone is interested).

I get a stable and fast connection to my house's router, using Win10.  Ubuntu will work similarly for long periods, say 10 to 30 minutes.  But then, it will suddenly slow down, or completely stop for a few minutes at a time.  When this happens, I do not see any notifications from Ubuntu that the wireless adapter dropped its connection, scanned, and reconnected (I have an older laptop which does drop the connection, then issue reconnect messages in Ubuntu 15 and in Win7).

The chip on the NIC is the Realtek RTL8192CE.  I have seen various bits of advice floating around the Net, regarding various flavors of RTL8192 chips and Linux, suggesting driver upgrades, etc.  Some of this advice goes back over five years, and I'm reluctant to follow it and break my installation of Ubuntu.  I'm a little surprised that I'm struggling with such issues at all.  

Does anyone have any suggestions?  (Recommendations alter settings on the router will likely be problematic, since the landlord would need to get involved.  Wish I was living in my old place, with proper Cat5e wired connections.)

Thanks!

---

### Post by wildmanne39 on 2017-07-16
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by praseodym on 2017-07-16
Try these module parameters:

```
echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot

---

### Post by john_ladasky on 2017-07-16
> **wildmanne39 said:**
> Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

Hi wildmanne,

I've only gotten as far as "sudo apt update", "sudo apt dist-upgrade", and a reboot.  I am testing out my connection now, it has been running for close to an hour without problems.  Maybe the upgrade fixed it?  I haven't declined any automatic upgrades offered by Ubuntu.

I just keep playing videos and opening web pages.  I am also watching the Network History graph in the System Monitor.  I haven't seen a long pause, web page timeout, or connection reset so far.

---

### Post by wildmanne39 on 2017-07-16
It will most likely need the parameters praseodym posted in his post or even a newer driver.

---

### Post by john_ladasky on 2017-07-17
OK, I eventually started getting problems again.  Here's [my Pastebin link]("http://paste.ubuntu.com/25110647/").  I won't change any parameters yet.

Thanks for you continued assistance.

---

### Post by praseodym on 2017-07-17
Change the encryption mode in your router to WPA2-AES (CCMP) only, not mixed mode WPA/WPA2. Additionally change the channel to fixed "13" there

---

### Post by john_ladasky on 2017-07-18
> **praseodym said:**
> Change the encryption mode in your router to WPA2-AES (CCMP) only, not mixed mode WPA/WPA2. Additionally change the channel to fixed "13" there

OK, I'm not exactly a network guru, but I think that you want me to modify the settings in some network config file as follows (and I will have to find out how to do that):

> WIFI-PROPERTIES.WPA:                    no
WIFI-PROPERTIES.WPA2:                   yes

As for changing my WiFi to channel 13: first, I don't see channel information reported anywhere in the wireless-info output.  Also, I guess I should have mentioned that I'm in the USA.  We only have eleven 2.4 GHz WiFi channels here.  You want me to try a fixed channel, instead of allowing channel hopping?  Does it need to be channel 13?

---

### Post by john_ladasky on 2017-07-18
Oh, I just discovered [SIZE=3]**iwlist**[/SIZE] for [wireless channel scanning]("https://www.howtogeek.com/197268/how-to-find-the-best-wi-fi-channel-for-your-router-on-any-operating-system/")... cool.  That might help me choose a fixed channel for my computer.

---

### Post by praseodym on 2017-07-18
Yeah, 11 should be fine

---

