---
title: "Unexplainable Atheros 242x. Behaviour!!!"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by hamofgrey on 2008-12-25
Hi,

Firstly I hope everyone had a jolly Xmas :)

Secondly can anyone explain the odd and strange goings on with my wireless card. I have a Atheros 242x. wireless card and used this tutorial to get the card up and running - [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/).

I had to re-install Ubuntu due to some other problem I have followed through this tutorial several times now and the card no longer works. The card does not seem to detect any wireless networks at all! Which is very odd.

Even when I boot into Windows XP the card still does not find any wireless networks?!? What on earth could cause this?

When I insert a Wireless USB stick it detects the different networks fine, just not when I use my card. The bizarre thing about this is the card did work after the re-installation and have randomly stopped.

HELP anyone?

Thanks in advance for your posts!

---

### Post by hamofgrey on 2008-12-25
Here are some commands in terminal which maybe of some use. These are executed with the wireless USB stick inserted and working with an Internet connection.


```
graham@Graham-Laptop:~$ uname -a
Linux Graham-Laptop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux


```

```

graham@Graham-Laptop:~$ cat /etc/issue
Ubuntu 8.10 \n \l

```

```

graham@Graham-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

wmaster1  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Brownbase"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:D0:F7:A6:3F   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:36/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

```

graham@Graham-Laptop:~$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:90:D0:F7:A6:3F
                    ESSID:"Brownbase"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=100/100  Signal level:35/100  
                    Encryption key:on
                    IE: Unknown: 000942726F776E62617365
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0107
                    IE: Unknown: 2F0107
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000203f0aa018a
                    Extra: Last beacon: 96ms ago

```

I'll do these again without the Wireless USB stick inserted as well...

---

### Post by hamofgrey on 2008-12-25
These were the results without the Wireless USB stick running...


```

graham@Graham-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

```

graham@Graham-Laptop:~$ iwlist wlan0 scanning
wlan0     Interface doesn't support scanning.

```

---

### Post by hamofgrey on 2008-12-26
I woke up this morning and turned my laptop on to find the wireless card working in Windows!?!? I have no idea why, is there any way testing to see if the card is overheating?

Just booted up in Ubuntu and the card now also works. No idea why! As I said before could this be due to overheating or is it again something else causing this?

---

### Post by hamofgrey on 2008-12-27
My wireless card has dropped out again for no reason. Randomly on turning off the laptop and restarting it the card was detected by Ubuntu and Windows but on scanning for networks (which are there) it found none? After a couple of re-boots the problem disappeared. 

I went into the Windows System Log and looking at an information log about the system it said the card had successfully started up but was disconnected from the network, if this was a malfunction try updating your drivers.

I went into the Ubuntu System Log but was unable to find any information.

Please could anyone else spread the perspective on this problem, as I am quite out of my depth?

---

### Post by hamofgrey on 2009-01-04
Again the same problem has occurred. Anyone?

---

### Post by hamofgrey on 2009-01-05
hi i have discovered that my laptop runs very hot. I typed acpi -V and got the following results:

```

    Battery 0: Charging, 34%, 00:00:02 until charged
  AC Adapter 0: on-line
     Thermal 0: ok, 63.0 degrees C
     Thermal 1: ok, 63.0 degrees C    Battery 0: Charging, 34%, 00:00:02 until charged
  AC Adapter 0: on-line
     Thermal 0: ok, 63.0 degrees C
     Thermal 1: ok, 63.0 degrees C
     Cooling 0: LCD 0 of 8
     Cooling 1: LCD 0 of 8
     Cooling 2: Processor 0 of 10
     Cooling 3: Processor 0 of 10
     Cooling 0: LCD 0 of 8
     Cooling 1: LCD 0 of 8
     Cooling 2: Processor 0 of 10
     Cooling 3: Processor 0 of 10

```

could the problem be related to overheating?

---

