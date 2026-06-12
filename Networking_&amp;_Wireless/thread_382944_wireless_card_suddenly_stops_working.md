---
title: "wireless card suddenly stops working"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by Eschatokyrios on 2007-03-12
My wireless card, and thus my internet connection, suddenly stopped working the other day. I have a Broadcom BCM4306 wlan card, which I had set up working fine with ndiswrapper. I can still see the card with lspci, and ndiswrapper -l lists that both the device and driver are installed, with exactly the same driver as I had when it was working. The card works fine when I boot into windows, so it's not a hardware issue. 

dmesg | grep ndiswrapper gives 

```
laptop:~$ sudo dmesg | grep ndiswrapper
Password:
[17179608.276000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179608.296000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179608.296000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179608.316000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179608.320000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179608.320000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179608.712000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179608.716000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179608.716000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179609.040000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179609.040000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179609.040000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179609.064000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179609.068000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179609.068000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179609.092000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179609.092000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179609.096000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
```

---

### Post by sjnovick on 2007-03-12
Can you post your output from
> iwconfig              ???

This shows which wireless devices are available.

---

### Post by sjnovick on 2007-03-12
A couple of thoughts:

1.  Here is my iwconfig output (ath0 is my wireless connection).  Do you get anything like ath0?

sjnovick@Kitchen:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys-sn"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:13:10:E9:1E:A6   
          Bit Rate:6 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/94  Signal level=-66 dBm  Noise level=-95 dBm
          Rx invalid nwid:1  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



2.  If your ndiswrapper fails to load, have you tried uninstalling and re-installing it with Synpatic?  Then re-installing the drivers with

ndiswrapper -i yourdriver.inf    ???

I'm not an expert linux-er, but I know how to install drivers with ndiswrapper.
(All as sudo or su)
a.  ndiswrapper -i yourdriver.inf
b.  depmod -a
c.  add ndiswrapper to /etc/modules
d.  modprobe ndiswrapper

Then you should be good to go.

3.  Did you disable the included broadcom drivers?
a.  rmmod bcm43xx
b.  Add (wtihout quotes) "blacklist bcm43xx" to /etc/modprobe.d/blacklist


Hope that helps.

---

### Post by Eschatokyrios on 2007-03-13
> **sjnovick said:**
> A couple of thoughts:

1.  Here is my iwconfig output (ath0 is my wireless connection).  Do you get anything like ath0?


I get no wlan0 at all. I see only lo, eth0, and sit0, none of which have wireless extensions. Before it stopped working, I used to get wlan0, with all the proper information.

> 
2.  If your ndiswrapper fails to load, have you tried uninstalling and re-installing it with Synpatic?  Then re-installing the drivers with

ndiswrapper -i yourdriver.inf    ???

I'm not an expert linux-er, but I know how to install drivers with ndiswrapper.
(All as sudo or su)
a.  ndiswrapper -i yourdriver.inf
b.  depmod -a
c.  add ndiswrapper to /etc/modules
d.  modprobe ndiswrapper

Then you should be good to go.


Did you mean add the line of text 'ndiswrapper' on a new line in /etc/modules? I did that. When I did modprobe ndiswrapper I got the error:

```

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid arguement

```

I can't reinstall anything with Synaptic because I have no internet connection without wlan0 working.

> 
3.  Did you disable the included broadcom drivers?
a.  rmmod bcm43xx
b.  Add (wtihout quotes) "blacklist bcm43xx" to /etc/modprobe.d/blacklist


I never did this before. In any case, rmmod bcm43xx returns the error that it does not exist in /proc/modules.

---

### Post by Eschatokyrios on 2007-03-17
bump

---

### Post by HumbleGod on 2007-03-17
> **Eschatokyrios said:**
> My wireless card, and thus my internet connection, suddenly stopped working the other day. 

Did you upgrade your kernel by any chance? That screwed mine over, too.

---

### Post by saracen on 2007-03-31
Can anyone help on this issue?  I'm having the same problems with ndiswrapper```
saracen@acer:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```

---

