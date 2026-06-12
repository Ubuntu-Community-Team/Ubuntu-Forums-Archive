---
title: "firmware-b43-installer error: &quot;unable to resolve host address ‘www.lwfinger.com’&quot;"
date: 2015-11-25
forum: Networking &amp; Wireless
---

### Post by halfshark-alligato on 2015-11-25
Hi, Trying to deal with broadcom wireless issues on a completely fresh installation of 14.04.03 on a Macbook Pro (version 8, 1, I believe). I've done apt-get updates and dist-upgrades. Results of wireless-info script at bottom.

The installation appears to basically work, but the main issue is as below, I think:

```
 
Setting up firmware-b43-installer (1:018-2) ...
No chroot environment found. Starting normal installation
--2015-11-25 16:39:34--  [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)
Resolving [www.lwfinger.com]("http://www.lwfinger.com") ([www.lwfinger.com]("http://www.lwfinger.com"))... failed: Name or service not known.
wget: unable to resolve host address ‘[www.lwfinger.com’]("http://www.lwfinger.com’")
dpkg: error processing package firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 4

```

While this is a series of error messages I've seen in many posts, I have been unable to resolve my issue using any of the methods described in previous threads.

I did see this mentioned somewhere--is this result significant?

```

ping lwfinger.com
ping: unknown host lwfinger.com

```

My particular configuration details are attached: [ATTACH]265773[/ATTACH] 

Thanks,

[HR][/HR]

---

### Post by Hadaka on 2015-11-25
Hi, from a working wired connection please do..
```
sudo apt-get remove --purge firmware-b43-installer
sudo apt-get install --reinstall firmware-b43-installer
sudo modprobe b43
```
then copy and paste..
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
thanks

---

### Post by halfshark-alligato on 2015-11-25
@Hakada, thanks for responding. Copying exactly those five commands into the terminal and then re-booting has made no apparent difference. I of course have a wired connection because that's how I accessed this forum, but there must be something more to having the wifi notice available networks.

Needless to say, I still got the same "unable to resolve host address" for the lwfinger.com url.

Can you give any more context that would help me understand what's going on? Why does the whole [www.lwfinger.com](www.lwfinger.com) domain not appear to have any functionality? Does that matter?

Craving new Bloom County cartoons,
W

I'm sorry I can't give more information about how things are failing. Please let me know what I can do to provide more debugging info.

---

### Post by Hadaka on 2015-11-25
Hi, try this..please do..
```
sudo apt-get remove --purge firmware-b43-installer
```
Then go here..
[http://ubuntuforums.org/showthread.php?t=2303861](http://ubuntuforums.org/showthread.php?t=2303861)
**Post #5 - just get the download
*by default is should save to Downloads.
back to terminal...
Then COPY and paste
```
sudo mkdir /lib/firmware/b43
sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/b43
```
BOOT

oh, i dont know whats going on with the finger account..i cant get in either??

---

