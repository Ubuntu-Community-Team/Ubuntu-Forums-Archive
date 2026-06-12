---
title: "can I create a pretend wireless interface"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by danmiddle2 on 2008-10-22
Hi there,

I have an Atheros WiFi card that works fine under Hardy. The atheros card creates a wifi0 interface and an ath0 'VAP' interface... and as I say, everything works fine with that card for all my Internet needs.

I am trying to get a piece of software working which is free, but not OpenSource and that software all works fine, except that it can't talk to the Internet. Some functions of the software require this.

I have a theory that this is because the system that this software is built for uses a different wireless chipset, which assigns the interface WLAN0 to it's wireless card and the software is monitoring for the presence of WLAN0 and it's connection status before it tries to send any traffic.

Is there any way I can create the interface wlan0 as a fake interface that is really ath0?

In file terms, I would do this;
```
ln -s ath0 wlan0
``` 

But that clearly isn't going to work here.

Many thanks

Dan

---

### Post by Greyed on 2008-10-22
```

ls -l /dev/ath0
man MAKDEV

```

Pull the major/minor numbers from /dev/ath0, use MAKEDEV to create one with the same numbers named wlan0.  Not the preferred method but I'm an old fuddie duddie from the pre-udev days.  It should work but no guarantees.

---

### Post by Greyed on 2008-10-22
Er, actually, wait, why wouldn't a softlink work?  /dev is full of softlinks!  

```

{grey@igbuntu:/dev} ls -l | grep lrwx
lrwxrwxrwx  1 root    root          13 Oct 21 18:00 MAKEDEV -> /sbin/MAKEDEV
lrwxrwxrwx  1 root    root           4 Oct 21 18:00 cdrom -> scd0
lrwxrwxrwx  1 root    root          11 Oct 21 18:00 core -> /proc/kcore
lrwxrwxrwx  1 root    root           4 Oct 21 18:00 dvd -> scd0
lrwxrwxrwx  1 root    root          13 Oct 21 18:00 fd -> /proc/self/fd
lrwxrwxrwx  1 root    root          24 Oct 21 18:00 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx  1 root    root           4 Oct 21 18:00 sr0 -> scd0
lrwxrwxrwx  1 root    root          15 Oct 21 18:00 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root    root          15 Oct 21 18:00 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root    root          15 Oct 21 18:00 stdout -> /proc/self/fd/1

```

---

### Post by danmiddle2 on 2008-10-22
> **Greyed said:**
> Er, actually, wait, why wouldn't a softlink work?  /dev is full of softlinks!  

```

{grey@igbuntu:/dev} ls -l | grep lrwx
lrwxrwxrwx  1 root    root          13 Oct 21 18:00 MAKEDEV -> /sbin/MAKEDEV
lrwxrwxrwx  1 root    root           4 Oct 21 18:00 cdrom -> scd0
lrwxrwxrwx  1 root    root          11 Oct 21 18:00 core -> /proc/kcore
lrwxrwxrwx  1 root    root           4 Oct 21 18:00 dvd -> scd0
lrwxrwxrwx  1 root    root          13 Oct 21 18:00 fd -> /proc/self/fd
lrwxrwxrwx  1 root    root          24 Oct 21 18:00 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx  1 root    root           4 Oct 21 18:00 sr0 -> scd0
lrwxrwxrwx  1 root    root          15 Oct 21 18:00 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root    root          15 Oct 21 18:00 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root    root          15 Oct 21 18:00 stdout -> /proc/self/fd/1

```

In the full knowledge that this is probably a really stupid question. What would I link from and too?

I have no /dev/ath0 to link to /dev/wlan0?

Thanks for your help.

Dan

---

### Post by danmiddle2 on 2008-10-23
> **Greyed said:**
> ```

ls -l /dev/ath0
man MAKDEV

```

Pull the major/minor numbers from /dev/ath0, use MAKEDEV to create one with the same numbers named wlan0.  Not the preferred method but I'm an old fuddie duddie from the pre-udev days.  It should work but no guarantees.

I get the following;
```
 root@ux1xn:/dev# ls -l /dev/ath0
ls: cannot access /dev/ath0: No such file or directory
```

My wireless connections are as follows
```
root@ux1xn:/dev# iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"*****"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:******************   Security mode:restricted
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:2020  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

I also tried
```
 root@ux1xn:/dev# ls -l /dev/wifi0
ls: cannot access /dev/wifi0: No such file or directory

```

Any further help would be appreciated.

---

### Post by Greyed on 2008-10-23
I was probably off base, then.

---

