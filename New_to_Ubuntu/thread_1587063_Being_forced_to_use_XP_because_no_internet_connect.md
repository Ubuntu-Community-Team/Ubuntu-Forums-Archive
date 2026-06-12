---
title: "Being forced to use XP because no internet connection"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by zdubun on 2010-10-02
Hi all, 

Some time ago, i posted my problem. No replies. Because of this I am being forced to use xp.  In ubuntu although the WIFI LED is on, the wifi radar cannot seem to connect to the connection, or if it tries to connect the blue bars go grey( signal not picked up)
Irritatingly the ubuntu does not even connect through the wired connection. I could REALLY use some advice
I am pasting the out puts:-
 zeek2@zeek2-laptop:~$ ifconfig
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:12 errors:0 dropped:0 overruns:0 frame:0
              TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
    zeek2@zeek2-laptop:~$ iwconfig
    lo        no wireless extensions.
  eth0      no wireless extensions.
  eth1      IEEE 802.11  Access Point: Not-Associated   
              Link Quality:5  Signal level:0  Noise level:0
              Rx invalid nwid:0  invalid crypt:0  invalid misc:0
  pan0      no wireless extensions.
    [FONT=&quot]zeek2@zeek2-laptop:~$ [/FONT]

---

### Post by Dustin2128 on 2010-10-02
wifi radar? You're not using nm-applet?

---

### Post by dirghrabadia on 2010-10-03
Are you running Ubuntu via WUBI? If so, I had problems connecting to wireless networks, with 8.04 through WUBI install.

---

### Post by spcwingo on 2010-10-03
What cards do you use?

```
lspci
```

or if a USB wifi dongle:

```
lsusb
```

---

### Post by zdubun on 2010-10-03
No cards or dongle, I use a dell d530 core 2duo 2.2GHz And I have installed ubuntu as well as winodws. Not thru wubi.

---

### Post by spiky001 on 2010-10-03
can you post output of ```
lspci
```

---

### Post by sandyd on 2010-10-03
nvm

---

### Post by spcwingo on 2010-10-03
> **zdubun said:**
> No cards or dongle, I use a dell d530 core 2duo 2.2GHz And I have installed ubuntu as well as winodws. Not thru wubi.

There's some sort of card there if you're able to connect under your Win environment...the output of lspci would help to determine which one that is so we can help you get it going.  ;)

---

### Post by zdubun on 2010-10-03
Hi all, posting the ouput of lspci:-
 zeek2@zeek2-laptop:~$ lspci
    00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
    00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
    00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
    00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
    00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
    00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
    00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
    00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
    00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
    00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
    00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
    00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
    00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
    00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
    00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
    00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
    00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
    00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
    03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
    03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
    09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
    0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    zeek2@zeek2-laptop:~$ 
    Thanks in advance

---

### Post by spcwingo on 2010-10-03
You might want to have a look at this for your wireless:

[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

### Post by RetchingRabbit on 2010-10-03
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

Seems to indicate you have a Broadcom 4311 chip.

[This post may help...]("http://ubuntuforums.org/showthread.php?t=1426973&highlight=bcm+4311")

---

### Post by zdubun on 2010-10-04
Thanks, next question. What files do I download from this place, and should I download them onto a USB via windows and them install them into ubuntu as the ubuntu has no connection at all?

---

### Post by zdubun on 2010-10-20
Hi there, tried it. Followed the instrucions. No success. Help.

---

### Post by CtrlAltLife on 2010-10-20
i have the same problem but it detects my wifi card but the driver wont install

 Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

thats what i get when i try and Activate the driver

i have never had this problem before till now for some reason

---

