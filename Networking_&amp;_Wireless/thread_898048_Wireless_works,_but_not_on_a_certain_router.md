---
title: "Wireless works, but not on a certain router"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by lnlds on 2008-08-22
I have an issue with ubuntu on my friends wireless router. I've had no problems with wireless networking and this happens on multiple laptops. The network is detected but Ubuntu can't connect. Windows has no problem connecting. Under what circumstances would this occur? How would I go about fixing this

---

### Post by chkneater on 2008-08-22
I have a similar problem, I can see the Windows network icon but there is nothing in it.  I don't know if the windows network can see me or not, but I've heard that Linksys routers might be to blame.

---

### Post by pytheas22 on 2008-08-22
The next time you're in range of your friend's router, open up a terminal and type:
```

iwlist scan
```

and post the output here (if there are multiple networks in the scan, please tell us the name of your friend's).  Please do the same for your network at home.  That way we can see what's different between the two networks that might be causing the problem.

Also, you may want to try connecting using [wicd]("http://wicd.sourceforge.net").  It works better in a lot of cases.

---

### Post by lnlds on 2008-08-23
> **pytheas22 said:**
> The next time you're in range of your friend's router, open up a terminal and type:
```

iwlist scan
```

and post the output here (if there are multiple networks in the scan, please tell us the name of your friend's).  Please do the same for your network at home.  That way we can see what's different between the two networks that might be causing the problem.

Also, you may want to try connecting using [wicd]("http://wicd.sourceforge.net").  It works better in a lot of cases.

Alright, I'll do that next time Thanks!

---

### Post by caljohnsmith on 2008-08-23
> **pytheas22 said:**
> The next time you're in range of your friend's router, open up a terminal and type:
```

iwlist scan
```

and post the output here (if there are multiple networks in the scan, please tell us the name of your friend's).  Please do the same for your network at home.  That way we can see what's different between the two networks that might be causing the problem.

Also, you may want to try connecting using [wicd]("http://wicd.sourceforge.net").  It works better in a lot of cases.
I believe "iwlist scan" will just print out the last cached iwlist scan. Correct me if I'm wrong, pytheas22, but shouldn't iwlist scan be run as root to do a current scan?
```
sudo iwlist scan
```

---

### Post by pytheas22 on 2008-08-23
> I believe "iwlist scan" will just print out the last cached iwlist scan. Correct me if I'm wrong, pytheas22, but shouldn't iwlist scan be run as root to do a current scan?

That's interesting that you think it prints out information from a cached scan...maybe there's a way to make it do this.  But as far as I know, it just performs the scan immediately.  And you don't need to be sudo to use iwlist on Ubuntu (other Linux distributions may require root privileges)--at least, I definitely don't on my machine.

---

### Post by caljohnsmith on 2008-08-23
> **pytheas22 said:**
> that's interesting that you think it prints out information from a cached scan...maybe there's a way to make it do this.  But as far as i know, it just performs the scan immediately.  And you don't need to be sudo to use iwlist on ubuntu (other linux distributions may require root privileges)--at least, i definitely don't on my machine.
OK, I guess I was remembering incorrectly. Sorry for the confusion.

---

### Post by pytheas22 on 2008-08-23
You may be right.  The reason I thought that the scanning occurred when iwlist was called is that whenever I've done it, there seems to be a pause of a few seconds while the card scans, during which the light on my card blinks.  If it were just pumping out information from a cache, I wouldn't expect there to be any delay in getting it, and I wouldn't expect to see any action on my wireless device.

So I'm not sure what's going on.  It's possible that the man page is wrong, or perhaps calling iwlist as a normal user triggers a call by root to issue a scan or something--this may be the way that the Ubuntu developers worked around permission issues with iwlist.

Either way, for the original poster in this thread, posting the "iwlist scan" outputs as either a normal user or root should work fine.

---

### Post by vban77 on 2008-08-23
Saw this thread an was hoping you may be able to help...

I am new to linux, and my wireless connection works everywhere by my home.

Have Linksys WAP54G Access Point.

I ran iwlist and got following:

eth1     Scan completed :
         Cell 01 - Address: 00:0F:66:19:38:C5
                   ESSID:"TheArk"
                   Protocol:IEEE 802.11bg
                   Mode:Master
                   Channel:6
                   Frequency:2.437 GHz (Channel 6)
                   Encryption key:off
                   Bit Rates:1MB/s; 2MB/s; 5.5 MB/s; 6MB/s; 9 MB/s
                             11 MB/s; 12 MB/s; 18 MB/s; 24 MB/s; 36 MB/s
                             48 MB/s; 54 MB/s
                   Quality=93/100  Signal level=-37 dBm  Noise level=-37 dBm
                   Extra: Last beacon: 72ms ago

---

### Post by pfdevil on 2008-08-23
You may want to check if the router that your trying to connect to is dhcp enabled. This may seem a little trivial, but if dhcp is not enabled on the router you would have to connect manually.

---

### Post by vban77 on 2008-08-23
Tried that... still no connection...

---

### Post by vban77 on 2008-08-24
i tried iwconfig and the following was what i got

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Managemetn:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retires:0  Invalid misc:14  Missed beacon:0

---

### Post by pytheas22 on 2008-08-24
vban77,

Please try connecting using [wicd]("http://wicd.sourceforge.net"), a different connection manager.  It may work better.

If that doesn't help, please try disabling encryption on your router and see if you can connect then.  That way we'll know whether the encryption is to blame, or some other thing.

Also, it looks like you're using WEP at home.  Is that right?  And when you say that you can connect to networks everywhere else besides your home, are those also encrypted or have you only tried unsecured networks?

---

### Post by vban77 on 2008-08-25
Tried both, and still not getting a connection...

My pc is able to see the router, but it will not connect, both wired and wireless...

---

### Post by pfdevil on 2008-08-26
If you can't connect to your router even though wired. There is a problem with you settings. Most likely your router isn't dhcp enabled of you are entering your key wrong. Boot up in windows and connect with the wired. Get all the info like ip, default gateway and that. Put it in manually. Then try to browse your router again.

---

### Post by vban77 on 2008-08-27
I feel like an idiot... I was using a Linksys wap54g access point...

That's what my problem was...

Bought a netgear Router, and got online w/ no issues...

Thank you to anybody who posted replys and sorry to take up you time!!

---

