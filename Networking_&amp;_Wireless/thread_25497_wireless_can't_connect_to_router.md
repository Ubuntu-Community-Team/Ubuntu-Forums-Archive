---
title: "wireless can't connect to router"
date: 2005-04-10
forum: Networking &amp; Wireless
---

### Post by BartAfterDark on 2005-04-10
hello.
I'm very new to the linux world.
I'm trying to get my wireless network to work. But it wont connect.
I installed the drivers and everything. But ut wont even see the router

iwconfig
> wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist wlan0 scan
> wlan0     No scan results

I really hope someone knows what I could do.

Thank you.

 - lars

---

### Post by accuser on 2005-04-10
You are not using a Broadcom based wireless card with ndiswrappers by any chance?

---

### Post by BartAfterDark on 2005-04-10
[QUOTE=accuser]You are not using a Broadcom based wireless card with ndiswrappers by any chance?[/QUOTE]

I think I am
LINKSYS WMP54G

why?

---

### Post by accuser on 2005-04-10
Why? Because I just happend to spend the best part of yesterday getting the card working. It is very simple to solve:

Find the configuration folder for your ndis driver, which should be under the /etc/ndiswrapper folder. (It depends on how you installed the driver - I installed mine using 'ndiswrapper -i /media/cdrom/Drivers/bcmwl5.inf' and the drivers were placed in a folder '/etc/ndiswrapper/bcmwl5'.)

There should be 5 .conf files in this folder, like:

[INDENT]14E4:4320:14E4:0147.conf[/INDENT] 
[INDENT]14E4:4320:14E4:0148.conf[/INDENT] 
[INDENT]14E4:4320:1737:0013.conf[/INDENT] 
[INDENT]14E4:4320:1737:0014.conf[/INDENT] 
[INDENT]14E4:4320.conf[/INDENT]

The last file is a symbolic link to one of the other four .conf files. The settings in this file affect the way the card operates. The setting that you are interested in is 'RadioState'. When I installed my ndis driver, ndiswrapper forced RadioState to 1. Unfortunately, this disables the power to the radio! Edit the 14E4:4320.conf file and change:

```
RadioState|1
```

to

```
RadioState|0
```

Unload the ndiswrapper module ('sudo rmmod ndiswrapper') and then reload it ('sudo modprobe ndiswrapper'). You should now be able to configure your wireless network.

Enjoy!
Matthew

---

### Post by BartAfterDark on 2005-04-10
weee it's working :D
Just read a other post here with the same problem ](*,) 
Maybe I should dig a little deeper next time hehe :P

But thanks anyway ;)

---

