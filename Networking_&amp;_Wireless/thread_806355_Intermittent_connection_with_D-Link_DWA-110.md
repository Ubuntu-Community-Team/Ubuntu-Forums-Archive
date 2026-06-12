---
title: "Intermittent connection with D-Link DWA-110"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by peterballard on 2008-05-24
Hi all,

I've asked on this archived thread [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) without much success, so I am asking here in the hope of a wider audience...

I have a new PC with Ubuntu 8.04, using a D-Link DWA-110 wireless adapter. Since it (apparently) uses the RT73 chipset, I followed the instructions at this thread: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) i.e.:

1. Installed the drivers from [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) 

2. Added a few lines to /etc/modprobe.d/blacklist:
```

blacklist rt73usb
blacklist rt2570
blacklist rt2500usb
blacklist rt2x00lib
blacklist dr71wu

```

3. Added a few lines to /etc/network/interfaces:

```

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "default"
pre-up iwconfig wlan0 key "off"

```

I use default as my essid name because that's what comes out of "sudo iwlist scan":

```

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:84:B9:DE
                    ESSID:"default"
                    Mode:Managed
                    Channel:6
                    Encryption key:off
                    Bit Rates:0 kb/s

```

That's it. Otherwise it's a new ubuntu 8.04, though I've also added these ubuntu packages: ubuntu-restricted-extras, emacs, gawk, fetchmail, sendmail, m4, procmail, sendmail-base, sendmail-bin, sendmail-cf, sensible-mda.

Unfortunately my PC only connects to the Internet intermittently. "sudo ifup --f wlan0" is meant to bring the internet connection up, but doesn't.

Can anyone suggest files to check or commands to run to try to work out what the problem is? I know it's not a hardware problem, because when I boot into Windows XP it comes up every time.

--
Peter

---

