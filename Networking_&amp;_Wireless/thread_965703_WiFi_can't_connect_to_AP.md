---
title: "WiFi can't connect to AP"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by jeezaa on 2008-10-31
Hi all,
at first - sorry for my english...

And now, my problem:
I bought new WiFi USB Edimax EW-7318UG.Then I tried to install driver for this device (I downloaded it from this addr: [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) )

Everything is OK, but when I want to connect to the internet, my graphic interface ask me for password (on AP is 64bit HEX WEP code), then it looks like it's connecting, but after some time, it ask me for password again.

I tried to unset password and it was OK - (maybe, it was connected with WiFi card fixed in my laptop, but I don't think)

So, there is some problem with encryption?
Can be broken device?

I use Ubuntu 8.04 on HP Compaq 6715b.
This is the page with guide how to install device.
[http://www.abclinuxu.cz/hardware/pripojeni-na-sit/sitove-karty/usb-2/edimax-ew-7318ug](http://www.abclinuxu.cz/hardware/pripojeni-na-sit/sitove-karty/usb-2/edimax-ew-7318ug)

Can anyone help?
(one more time - sorry for my english, I just learning it, so it isn't perect)

---

### Post by ciscosurfer on 2008-10-31
First, welcome to the forums. :-)  

Second, please read [this thread]("http://ubuntuforums.org/showthread.php?t=706370") by nixscripter and then re-post.

---

### Post by jeezaa on 2008-11-01
Thank you for welcome. :)

Maybe I resolve my problem - and I spend on it only 4 hours! :-D
So this is a "short" guide how to use usb wifi device Edimax EW-7318UG:

1)
I put usb WiFi into notebook, and it starts blinking.
It is usb device, so I think, that it won't be registred in "lspci",
but when I type "lsusb", it will show me this:
```

Bus 006 Device 003: ID 148f:2573 Ralink Technology, Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```
where Bus 006 - Ralink is this WiFi.

2)
Then I installed drivers for this device:
on this site is czech guide (but it's easy - only download driver, unzip, make, make install and set modprobe)
[http://www.abclinuxu.cz/hardware/pripojeni-na-sit/sitove-karty/usb-2/edimax-ew-7318ug](http://www.abclinuxu.cz/hardware/pripojeni-na-sit/sitove-karty/usb-2/edimax-ew-7318ug)
...and then, reboot

3)
Now, iwconfig will show me this:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"abcd"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:F0:B1:73:78   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:186  Invalid misc:73037   Missed beacon:0

wlan2     RT73 WLAN  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Where wlan2 is usb WiFi.

and if I tried "iwlist wlan2 scan", it will show me my AP. (only my WLan is now in my range)
```
wlan2     Scan completed :
          Cell 01 - Address: 00:1C:F0:B1:73:78
                    ESSID:"abcd"
                    Mode:Managed
                    Channel:1
                    Encryption key:on
                    Bit Rates:0 kb/s

```

I tried to connect via my GUI interface, - it asked me for password (I using on AP 64bit WEP password), then it looked like it's connecting and after some time, it asked me for passowrd again.

4)
So I tried to turn my primary WiFi off
by this command: "sudo iwconfig wlan1 txpower off"
This should close connection, but for more sureness I turned my wifi off with button.

5)
Then I tried again iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:36 Mb/s   Tx-Power:0 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan2     RT73 WLAN  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
where wlan1 is my primary wifi and wlan2 is my usb WiFi device.

At this step I tried to use "ping google.com" and it typed "unknow host google.com"

6)
Now, "iwlist scan" will show me this:
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     No scan results

wlan2     Scan completed :
          Cell 01 - Address: 00:1C:F0:B1:73:78
                    ESSID:"abcd"
                    Mode:Managed
                    Channel:1
                    Encryption key:on
                    Bit Rates:0 kb/s

```

7)
So I tried to connect with these commands:

sudo iwconfig wlan2 essid abcd
sudo iwconfig wlan2 enc my_hex_passwd
sudo iwconfig wlan2 key my_hex_passwd
sudo iwconfig wlan2 channel 1
sudo dhclient wlan2

At now, I can ping google - it will show me some nice answer.

----------------------------------------------------------------------
And last problem - firefox don't want to connect - so, just try file > und uncheck "Work Offline" 


That's all, what I know about it...

---

