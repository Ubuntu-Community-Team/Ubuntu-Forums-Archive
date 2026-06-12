---
title: "How can I add wlan0 to network devices?"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by antiemptyv on 2006-08-26
This is my wireless hardware:

[INDENT]
**$ lspci | grep Broadcom\ Corporation**
0000:00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
[/INDENT]


I have installed the driver:

[INDENT]
**$ ndiswrapper -l**
Installed ndis drivers:
bcmwl5          driver present, hardware present
[/INDENT]


But wait... eth0 is my wired connection.  There is no wireless one?

[INDENT]
**$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
[/INDENT]

Where do I go from here to set up my wireless device?

Thanks.

---

### Post by antiemptyv on 2006-08-26
OK.  So, a good old-fashioned restart seemed to work.  Now iwconfig gives me this:

[INDENT]
**$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
[/INDENT]

However, even after activating the connection through eth1 (I'm using **network-admin**), I can't seem to connect through it.  Any ideas?  Am I missing something in the output from iwconfig?  

Thanks!

---

### Post by antiemptyv on 2006-08-26
OK.  So, a good old-fashioned restart seemed to work.  Now iwconfig gives me this:

[INDENT]
**$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
[/INDENT]

However, even after activating the connection through eth1 (I'm using network-admin), I can't seem to connect through it.  And when I close network-admin, and restart it, the wireless  connection has returned to it's inactive state.

Any ideas?  Am I missing something in the output from iwconfig?  

Thanks!

---

### Post by Maylar on 2006-08-26
```

sudo apt-get install wifi-radar
```
This got my wireless up working just fine

---

### Post by antiemptyv on 2006-08-26
> **Maylar said:**
> ```

sudo apt-get install wifi-radar
```
This got my wireless up working just fine

I tried that, actually.  When I run wifi-radar, it goes into an infinite loop, and in the terminal shows this text over and over and over and...

[INDENT]
**$ sudo wifi-radar**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
.
.
.
[/INDENT]

But thanks for the idea.  Any other ideas?

---

### Post by Maylar on 2006-08-26
> **antiemptyv said:**
> This is my wireless hardware:

I have installed the driver:

[INDENT]
**$ ndiswrapper -l**
Installed ndis drivers:
bcmwl5          driver present, hardware present
[/INDENT]


Actually. Then you are in the same boat I was in. There is two different drivers for this chipset. bcmwl5 and bcmwl5**a**

I had to use the later to get mine to work. I have zipped the entire Acer folder that includes both drivers and put it up for download for someone else. You can download it [here]("http://www.maylar.net/ndiswrapper/802.tar.gz") unless you are running the 64bit version. You can download those straight from Acer [here]("ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit/80211g.zip")

---

