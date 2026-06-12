---
title: "Intel 2200 B/G Pro"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by m47h3us on 2006-11-11
Hi i have been looking on the forums for ages trying to get my wireless working basicaly it does not show up any wireless points dont no what to do

```
cat@cat-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      unassociated  ESSID:"wireless.mackarill.co.uk"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

```

i don't no what info u want just ask tho

---

### Post by wieman01 on 2006-11-11
Ok, what's the output of:
> iwlist scan

---

### Post by m47h3us on 2006-11-12
iwlist scan output:

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:09:5B:88:49:D2
                    ESSID:"wireless.mackarill.co.uk"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=90/100  Signal level=-39 dBm  
                    Extra: Last beacon: 20ms ago

sit0      Interface doesn't support scanning.

```

---

### Post by am_abdelsalam on 2006-11-12
I have the same problem with my Toshiba Tecra A4 laptop, I have an Intel Pro Wireless 2200 B/G card and I don't know how to make it works.

My trials was that I downloaded a driver from intel for 2200 B/G cards, when I tried to compile it, it gave an error saying that the 802.11 source libraries are missing.

Please, I want some help...

---

### Post by m47h3us on 2006-11-12
would be help full if you can get this problem solved for me

---

### Post by wieman01 on 2006-11-13
> **m47h3us said:**
> iwlist scan output:

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:09:5B:88:49:D2
                    ESSID:"wireless.mackarill.co.uk"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=90/100  Signal level=-39 dBm  
                    Extra: Last beacon: 20ms ago

sit0      Interface doesn't support scanning.

```
It seems encryption it turned off. I would disable it first, then use Gnome's networking applet to configure your network. It appears your card it up & running. You can configure the rest using the applet. It even supports WEP (but not WPA).

---

### Post by m47h3us on 2006-11-13
am n00b so you will have to tell me step by step what i would need to do to get it working

---

### Post by Gtaylor on 2006-11-13
The Tecra A4 is still in a state of flux in terms of wireless support. Even if you get it configured, there is a firmware problem that causes the interface to restart in short intervals. I'm still working with the laptop team to resolve this, but until then you're only likely to see horrible performance if any at all.

There is a bug on launchpad with the details, feel free to contribute:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/55532](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/55532)

---

### Post by m47h3us on 2006-11-13
i turned WEP off on my wireless router and it works on my laptop now just my network is insecure so dont no what i should do now

---

### Post by Gtaylor on 2006-11-13
I'd suggest making a comment on that bug link I posted, it might help the developers in debugging the problem.

---

### Post by m47h3us on 2006-11-13
yeah will do

---

