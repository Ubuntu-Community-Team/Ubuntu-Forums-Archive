---
title: "Solved SET failed on device xxx ; Invalid argument"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by klabeister on 2006-07-18
I am posting this, because I have found numerous threads with questions about the error messages when starting up the wlan interface and no answer that has really solved my problem.

What happend was:
Whenver I tried to start my wireless network with 
```
sudo ifup xxx
```
I would get the following error messages 

```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth2 ; Invalid argument.
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device eth2 ; Invalid argument.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth2 ; Invalid argument.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth2 ; Invalid argument.

```

In my interfaces file I have the following (correct) information:

```
iface xxx inet dhcp
wireless-essid whatever
wireless-key **********
wireless-mode Managed
wireless-channel 6
wireless-rate auto
auto xxx

```

This is the output ```
sudo iwconfig
``` would show after executing the ifup command. 

```
xxx       802.11b/g NIC  ESSID:""
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          Retry:off   RTS thr=9999 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:38/100  Signal level:21/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:300   Missed beacon:0

```

Setting the wireless parameters manually with

```
sudo iwconfig xxx essid whatever
```

would work correctly after I executed the ifup command despite the errors.

When I accidentally used the iwconfig command when the interface was not up yet, I got the same error message I would get, when starting up the interface with ifup.

And that was the solution!

The wireless-tools script resided in the directory ```
/etc/network/if-pre-up.d
```
I moved the script from there to a newly created directory ```
/etc/network/if-post-up.d
``` and voila everything works.

I hope this helps other people with the same problem too.

---

