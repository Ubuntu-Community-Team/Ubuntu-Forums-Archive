---
title: "My WiFi network does not show up on 13.04"
date: 2017-05-04
forum: Networking &amp; Wireless
---

### Post by marcecastro on 2017-05-04
Hi,

I'm new to Ubuntu, and Linux (so please excuse me for my silly questions). I just installed Ubuntu 13.04 and can't connect to my home wireless network. I see my neighbors WiFi networks in the list, but not mine. What I've done so far:

1. Read [this]("https://help.ubuntu.com/stable/ubuntu-help/net-wireless-find.html") and make sure none of those issues affects me.
2. I've restarted the network service. No changes.
3. My WiFi adapter shows up under the list of devices and drivers and installed.
4. Tried to connect to hidden network and entered my network details. Won't connect either (since it's not hidden)

I'm thinking my router isn't compatible somehow. Any ideas? Thank you

---

### Post by wildmanne39 on 2017-05-04
13.04 is way to old and not supported there is really no way to help with this version of Ubuntu, please upgrade, I recommend 16.04 LTS because it is stable and has five years of support total.
Thanks

---

### Post by marcecastro on 2017-05-04
> **wildmanne39 said:**
> 13.04 is way to old and not supported there is really no way to help with this version of Ubuntu, please upgrade, I recommend 16.04 LTS because it is stable and has five years of support total.
Thanks

Ouch! Sorry! It's actually 16.04, since I downloaded it yesterday :-/ My hand slipped when writing the post...

---

### Post by wildmanne39 on 2017-05-04
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by marcecastro on 2017-05-04
> **wildmanne39 said:**
> Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

Hi,

Sorry for not going through that nice thread before. I've followed all the steps, but still not getting my network. This is the link to my results:

[http://paste.ubuntu.com/24512289/](http://paste.ubuntu.com/24512289/)

I did notice that I'm using a Broadcom card, so I also tried to install the correct drivers, as instructed in your post. But this is what I got:

> marcecastro@marcecastro-desktop:~$ sudo apt install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version (6.30.223.271+bdcom-0ubuntu1~1.1).
The following package was automatically installed and is no longer required:
  snap-confine
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

It seems the drivers were already installed properly.

Thanks

---

### Post by wildmanne39 on 2017-05-04
Is this the network you want to connect too Marce? it shows you are connected to it, but no internet access I take it?

After you let me know for sure there are some changes we will make to see4 if we can get it working.

Edit:


You have driver errors, you have a strange version I believe, where did you install this driver from?

---

### Post by marcecastro on 2017-05-04
> **wildmanne39 said:**
> Is this the network you want to connect too Marce? it shows you are connected to it, but no internet access I take it?

After you let me know for sure there are some changes we will make to see4 if we can get it working.

Edit:


You have driver errors, you have a strange version I believe, where did you install this driver from?

"Marce" is not my network. I can't get the PC to an Ethernet connection right now, so I had to create a wireless hotspot with another computer. I'm able to connect to that network, but my actual WiFi connection still won't show up.

About the drivers, I didn't install any. I just installed Ubuntu with the default driver. Thanks!

---

### Post by wildmanne39 on 2017-05-04
Please do:
```
sudo apt update
sudo apt dist-upgrade
```
Then:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
Then remove your wifi connection from network manager and reboot your router, shutdown your computer when the router is back up boot your computer and let it find your connection hopefully.

---

### Post by marcecastro on 2017-05-05
> **wildmanne39 said:**
> Please do:
```
sudo apt update
sudo apt dist-upgrade
```
Then:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
Then remove your wifi connection from network manager and reboot your router, shutdown your computer when the router is back up boot your computer and let it find your connection hopefully.

I took all the steps carefully, no errors. But still, my network won't show up.

This is what I see on Ubuntu:

[IMG]https://monosnap.com/file/AWmIQZZVqldKdx6U6YNLUEBHHpmqxP.png[/IMG]

This is what I see on my Mac:

[IMG]https://monosnap.com/file/6z8w0la5h1XXVb8Q4QmTdButa1G1zy.png[/IMG]

New script log: [http://paste.ubuntu.com/24517764/](http://paste.ubuntu.com/24517764/)

Thanks for the help

---

### Post by wildmanne39 on 2017-05-05
Go into your router settings and change the channel for your 5ghz connection to 40 and set it as a fixed channel instead of auto and see if it can see it then reboot your computer after the settings are saved in the router.
Thanks

---

### Post by marcecastro on 2017-05-07
> **wildmanne39 said:**
> Go into your router settings and change the channel for your 5ghz connection to 40 and set it as a fixed channel instead of auto and see if it can see it then reboot your computer after the settings are saved in the router.
Thanks


FIXED!

Sorry for taking so long to reply, but my broadband connection has been down for almost 2 days (thanks to my provider). So, A little update. I had to reinstall the system (since I screwed up when mounting a NTFS drive).

Since I had to start from the beginning, I decided to move my computer close to the router and connect through Ethernet. I installed the correct drivers, as instructed [here]("http://ubuntuforums.org/showthread.php?t=2214110") (from your post). I rebooted and... my 2.4G wireless network showed up, couldn't see my 5G connection, though. So, I changed the channel to 40, rebooted and... voilá! I'm now connected from my 5G connection. However, it seems I can't get as fast as before. Using fast.com, I get up to 130 Mbps, while with this same machine and Windows 7 I'm able to get to 250 Mbps. Anyway, I'll settle for this.

Thanks a million :-)

---

### Post by wildmanne39 on 2017-05-07
Glad to help.
Enjoy!:)

---

