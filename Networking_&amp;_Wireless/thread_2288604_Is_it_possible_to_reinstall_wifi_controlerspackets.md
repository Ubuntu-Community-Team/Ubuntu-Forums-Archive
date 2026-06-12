---
title: "Is it possible to reinstall wifi controlers/packets from CD? (no internet connection)"
date: 2015-07-28
forum: Networking &amp; Wireless
---

### Post by han2 on 2015-07-28
Hi,

My TP-Link TL-WN822N v3.0 wireless adaptor was not working correctly, so I decided to try the following:

sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware

After that, Xubuntu would not load. So I unplugged the wifi adaptor and uninstalled those packets. Now Ubuntu loads, but it doesn't detect the wifi adaptor at all.

Is it possible to reinstall from the Xubuntu CD the packets I deleted? I'm using Xubuntu 14.04 LTS.

What else could I do to make the TP-Link TL-WN822N v3.0 work?

Regards.

---

### Post by han2 on 2015-08-07
Nobody?

---

### Post by howefield on 2015-08-07
Thread moved to the "*Networking & Wireless*" forum. You'll stand a better chance of the fine folks in this forum finding your post then where it was originally.

---

### Post by Bucky Ball on 2015-08-07
Please open a terminal and copy/paste or type:

```
sudo lshw -C network
```

Post the results here, please, between code tags (see the last link in my signature).

Can you provide a link to where you got the information to add the third-party repository? Best to avoid unless necessary. ;)

---

### Post by han2 on 2015-08-07
Thank you, Howefield and Bucky Ball.

Here's the lshw:

```

  *-network               
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 94:de:80:66:d1:05
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:f7100000-f713ffff ioport:d000(size=128)

```

I got the information to add that third-party repository in this link (last comment):

[http://askubuntu.com/questions/625987/does-tp-link-wn822n-work-on-ubuntu](http://askubuntu.com/questions/625987/does-tp-link-wn822n-work-on-ubuntu)

---

### Post by Bucky Ball on 2015-08-08
Pretty sure the ALX driver is already included with the kernel so you shouldn't need to install anything else. :)

In the output above, you have the dongle plugged in when you run that command? That is showing 'Ethernet Interface'. Theoretically, that is your cable connection and the wireless is generally 'wlan*', where * is a number (starting from wlan0, but it can vary depending).

Please plug in the wireless dongle and try again if it wasn't in the first time. If it was, hmm. The machine is really not seeing it. If the latter, try running the wireless script in my signature and posting the output of that between code tags, thanks. :-k :)

PS: From the first line of the answer in the link you provided:

> It should work with Ubuntu without additional setup.

Yes, it should. Please remove that repo and reboot prior to doing the above stuff. (Just wondering, how did you install that repo when you can't get online? Did it also kill the cable connection? The output above appears not. Also, yes, that is the cable connection as it includes this in the output: port=twisted pair. When you're trying this stuff, best to use one or the other, dongle or cable, not both. The cable generally takes precedence over wireless so make sure that is unplugged when you are trying to get the wireless up).

---

### Post by han2 on 2015-08-09
Yes, I had the dongle plugged in. Since I removed that repo Ubuntu is not recognizing the dongle at all. 

Here's the script output: [http://pastebin.ubuntu.com/12038854/](http://pastebin.ubuntu.com/12038854/)

Before installing that repo, the wifi was working for a few minutes (4-5) every time I logged in. Then I realized that turning the wifi off and on (in Ubuntu) made it work again for another few minutes. That way I could install that repo. By the way, even in those few minutes the wifi wasn't working properly, because the signal was quite weak, and in Windows it's very strong.

---

