---
title: "Wireless connectivity is dropped after changing the rate"
date: 2014-10-01
forum: Networking &amp; Wireless
---

### Post by h.hittini on 2014-10-01
Hi,

I have a computer running Ubuntu Server 10.0.4 and 2.6.32-55-generic
I have Asus N53 USB adapter and it's using this driver/module rt3572sta

I need to limit the rate
When I use iwconfig with a rate and auto I get an error
```
hosam@RB110-01:~$ sudo iwconfig ra0 rate 36M auto
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device ra0 ; Operation not supported.
```
When I do the following, the connection is dropped
```
hosam@RB110-01:~$ sudo iwconfig ra0 rate 36M
```
What's wrong here


Thanks,

---

### Post by tgalati4 on 2014-10-01
Try 12 or 24 (without auto).  What is the purpose for limiting the data rate?  The placement of the antenna is critical to decent wireless performance.  If this is a server, then why are you using wireless?  Typically a stationary server uses a wired connection for reliability and maximum throughput.

Use a smartphone with WiFi Analyzer and examine the amount of wireless traffic in your area.  You might benefit from a frequency change.

---

### Post by h.hittini on 2014-10-02
> **tgalati4 said:**
> Try 12 or 24 (without auto).  What is the purpose for limiting the data rate?  The placement of the antenna is critical to decent wireless performance.  If this is a server, then why are you using wireless?  Typically a stationary server uses a wired connection for reliability and maximum throughput.

Use a smartphone with WiFi Analyzer and examine the amount of wireless traffic in your area.  You might benefit from a frequency change.

I can easily get 54Mbps; I already checked that
At the moment, the board is quite close to the router and I'm using channel 48
In addition, I need to use Wi-Fi and I need to limit the rate for research purposes

---

