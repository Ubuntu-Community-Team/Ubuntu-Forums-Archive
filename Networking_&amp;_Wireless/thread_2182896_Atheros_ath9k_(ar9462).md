---
title: "Atheros ath9k (ar9462)"
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by ye_lo on 2013-10-22
Hello there. This is my first post on this forum, but I've lurked on Linux communities for a month, attempting to solve this mostly annoying issue.

(Skip to "long story short" if you wish, there's my help request) 


Problem: my laptop wireless connection hangs when uploading speed hits above 50 KB/s. My dl rate is quite happy, but it drops to zero when ul "overloads". I often have to reset this pc wi-fi to reanimate the connection. 

Router is well configured, other computers establish flawless communication with it.


Broadly known solutions attempted and failed:

-Wlan power management off.
-Nohwcrypt, btcoex and everything modprobe related.
-Latest backports on distros with older kernel versions (yeah, odd idea, but this is the internet).
-Disabling wi-fi N (kind of worst workaround ever suggested to people with 100mbps DSL connections, didn't work for me anyway).
-Different network managers (working under different daemons, of course).
-All distros with state-of-the-art kernel. I know, backports should be enough for that matter, but hopes die last.


I even set up an open access point (hidden ssid) for testing purposes, result: connection still unstable on my laptop. It's pointless not to have wpa2 enabled anyway, modern linux distributions deal with it perfectly.



**Long story short**: I decided to try distros running under older kernels. It turns out kernel 3.6.x-ish is perfect for my wifi connection... However, I can't find a way to port its drivers to the future. How about someone guiding me through a "future port"? [Compat-wireless-3.6.8-1.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1.tar.bz2") simply won't compile on new kernels.


I must emphasize that I've done big research, this help request is very specialized, I hope it doesn't annoy old-school users.


Thanks in advance.

---

### Post by ye_lo on 2013-10-24
Is it really impossible to compile [compat-wireless-3.6.8-1.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1.tar.bz2") on younger kernels (3.8.x on)? I truly appreciate any help. I am currently running an LTS version of Ubuntu (kernel 3.2.0), but I would really enjoy moving to the latest release. Thanks for the long read.

---

### Post by jaiguru on 2013-10-26
Hi,

I face(d ?) exactly the same issue with my Asus S400CA which comes with an atheros AR9485 chip. Like you I tried almost all I found on Internet (even things I know are not related).

I'm pretty sure you can't compile compat-wireless-3.6.8-1.tar.bz2 on recent kernels due to some design changes on them. Anyway, it seems that I solve my issue recently (well, in fact yesterday evening) with 2 things:

First: I use latest backports (backports-20130927) on the 3.1 kernel coming with Ubuntu 13.10 (here is my uname -a "Linux VivoBook 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux"). This helped me a lot with wifi stability, but not so much with speed (at best around 3-5 Mbps).

Second: I tested several configurations for my Internet Box and finally got very good results with 802.11 b/g (thus excluding N), and TKIP (not AES) key. This last point made a real boost on speed and I'm now almost always arround 12-15 Mbps (ok, not perfect but really usable).

One remark: I've read things about disable_ani debug parameter on ath9k module but didn't find a way to disable it through /sys/kernel/debug... I finally give it a try by changing default value in code (file /backports-20130927/drivers/net/wireless/ath/ath9k/init.c on line 672 : "common->disable_ani = true;"). In my case, this slightly improve stability when I'm near my AP, but things gets worse when I'm at more than 5m).

Hope this can help :-)

Regards

---

### Post by ye_lo on 2013-10-27
Hey, thank you for the detailed answer, that's some nice share of experience!

It seems a lot of Linux users pursue a permanent fix for a problem that should not even exist, since ath9k works fine under many older kernels.

My DSL connection is a little too fast to bottleneck, I believe I will stick to mature distributions for now.

WattOS R6 is working fine for me, it's blazing fast, saves ram (not that I need) and consequently battery, which's always welcome and also this distro's big deal.


PS: It seems you've researched deeper into that problem. I thought I wouldn't get any advice at all, specially such good advice... So whenever I finally decide to move to something newer, I sure will consider it.

---

### Post by ye_lo on 2013-11-03
Good news: latest backports project and some tweaking unleash our wifi chipset capabilities. Other late ports may also work. Yes, it fixes connection stability and speed problems completely.

First, download [backports-20131031.tar.xz]("https://www.kernel.org/pub/linux/kernel/projects/backports/2013/10/31/backports-20131031.tar.xz") and extract it. Open the extracted path on terminal, then type:

# make defconfig-ath9k
# make
# sudo make install

Ignore key related warnings if the final message states the driver is installed. Reboot your pc or perform sudo modprobe ath9k.

Now, on terminal again (_replace essid with your wireless ap ssid_):
# sudo nano /etc/NetworkManager/system-connections/essid

A text editor will open on the terminal. Look for [802-11-wireless] and add below:

system-ca-certs=false

If such line already exists, just make sure to set it as _false_. Press ctrl+o (write out/save), then enter. Reboot your machine or reconnect to your access point. Your wireless headaches may have ended.


I did it on kernel 3.11.6-031106-generic (may work from 3.7.x on, where desperate needs for this fix began). My DL (35Mbps) and UL (20Mbps) speeds are working properly now, no more hangs, even if I'm considerably away from the router. Speed goes way higher when I'm connected to faster aps.

Let's hope it helps someone out there.

---

