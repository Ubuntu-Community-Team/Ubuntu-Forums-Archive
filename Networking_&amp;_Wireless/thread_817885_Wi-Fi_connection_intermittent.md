---
title: "Wi-Fi connection intermittent"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by Spanglegluppet on 2008-06-04
Hi all,

I've been had Ubuntu 8.04 installed via Wubi inside Windows Vista for a few weeks now (I would've posted this in the Wubi forum, but I didn't think that was significant) on my Acer Aspire 5610 laptop. I have a D-Link DI-524 wireless router in my house, that I haven't had any problems with until switching to Ubuntu (it works fine with Windows, and with my iPod touch). The problem is that the computer's connection to the Wi-Fi network seems to be rather intermittent, with a loss of connection occuring at seemingly random intervals (even though Ubuntu still says that it is connected to the network). This is solved by just reconnecting to the network, but this takes 15 seconds and it's a very annoying thing to have to do - especially if I'm in the middle of a download or an IM session. Some times I can go a whole day without a random disconnect, and other days (like today), it will happen every few minutes. The problem is getting very annoying. Any advice you could give me would be very helpful.

Thanks!

Tim

---

### Post by Spanglegluppet on 2008-06-05
sudo iwconfig (right now, while it's working) gets me:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"tim-home"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:5B:DD:12:A6   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:0270-0219-92
          Power Management:off
          Link Quality=76/100  Signal level=-58 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by cdtech on 2008-06-05
I'm having the same problem with my Hardy upgrade. I need to reset my network about every minute. I've tried pretty much everything known; updates, newest versions, reloading modules. I did set my interfaces file to static and that seemed to help some. Still working on this one.....

---

### Post by Spanglegluppet on 2008-06-14
Still having this problem, help would be greatly appreciated.

---

### Post by adamwhiles on 2008-06-14
having same problems here once I got mine to work.Anyone have any suggestions?

Adam Whiles
[http://adamwhiles.com](http://adamwhiles.com)

---

