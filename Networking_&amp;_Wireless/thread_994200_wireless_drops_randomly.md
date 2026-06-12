---
title: "wireless drops randomly"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by happytechie on 2008-11-26
Hi all, n00b alert here so please go gently with me.

I have a clean install of 8.10 on a no name laptop with a built in 802.11 adaptor.  It picks up my wireless network fine and having entered the key it works fine using DHCP and all those good things.

After a random period of time it just stops working, the icon in the status bar shows that I'm connected with two bars but I can't get any access to the internet at all.  Other machines on my network can connect OK.

It takes a restart to bring the connection back (connects by default and I don't need to to anything).

Has anyone got any idea what's going on?

ifconfig tells me:

wlan0     Link encap:Ethernet  HWaddr 00:15:af:0a:6e:5f  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe0a:6e5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3840976 (3.8 MB)  TX bytes:562643 (562.6 KB)

---

### Post by happytechie on 2008-11-26
paul@paul-laptop:~$ lsusb
Bus 005 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

---

### Post by Garpur on 2008-11-26
I also have simular problem as you, it is though in most case related to heavy download. I can be using my computer for the whole day, but starting a bittorrent download it can go anything from 5 minutes to 1 hour until my internet stalls. 

My wireless adapter is also** Realtek Semiconductor Corp. RTL8187**, I am also running 8.10. and unfortunatly I am also n00b.

So far I have tried removing the wireless manager that came with the installation and installed Wicd and also installed the lates Compat drivers. It in some strange way seems to make things little better, that is, my connection does not stall as often [should not have said that, as it actully stalled while is was writting these words]

**iwconfig gives the following:**
wlan0     IEEE 802.11bg  ESSID:"ANYTHING"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: ##:##:##:##:##:##   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off 
          Link Quality=16/100  Signal level:65/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Garpur on 2008-11-26
**And my ifconfig gives:**
wlan0     Link encap:Ethernet  HWaddr 00:15:af:03:3a:f2  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe03:3af2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:695301 (695.3 KB)  TX bytes:131576 (131.5 KB)

---

### Post by Jackie999 on 2008-11-27
Loads of posts on this rtl8187 driver not working very well (search rtl8187) and look [here]("http://bbs.archlinux.org/viewtopic.php?pid=299642").  One thing that does help, not sure you can call it a fix, is to type this in terminal:
```
sudo iwconfig wlan0 rate 5.5M fixed
```

---

### Post by happytechie on 2008-11-28
Thanks for that, I think it makes sense :D

is it a problem with the specific driver or the 802.11 stack that's being used?

I guess the other question is if the command above will 'fix' the issue for ever or will it need to be typed every time I boot my laptop?

---

### Post by happytechie on 2008-11-28
right my network just dropped so I typed the command sugested above and it didn't come back, so I've just re booted and typed the command again and this is now reflected in the output from iwconfig:

wlan0     IEEE 802.11bg  ESSID:"electric fence"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:17:07:7C:7C   
          Bit Rate=5.5 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=55/100  Signal level:40/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Has anyone looked into the reasons for this?  I can't see that anyone has.  As an experienced C coder I'm more than happy to lend some time.  Can I run the driver in a debugger or something and wait till it drops?

---

### Post by Jackie999 on 2008-11-28
Here is a quote from that link I posted above:
> I can confirm problems with rtl8187 in vanilla kernels 2.6.23 and 2.6.24-rc1, especially short operation range due to problems with rate control (bit rate goes up and stay there even when you have transmission failures because there's no accounting of retries or failures in the driver). This was already reported to the developers but there's no obvious fix for that using the current mac80211 rate controller. As a workaround, you can manually set the bit rate to a lower value using the "rate" command in iwconfig.That's from a year old post and as far as I can tell there has been no change since then.

Setting the rate to the lower 'fixed' 5.5M seems to work, but still drops for me.   And yes, it needs to be either set to run every reboot or typed on startup each time.  Search these forums for a post by tom_d for how to make it run automatically on boot.
I've switched to another wireless but keep looking fixes on the rtl8187.

---

### Post by happytechie on 2008-11-28
it seems to be working for me still after that force to the lower bit rate so I'll add that to my startup commands for now.

I'm still tempted to try and fix the driver.  I've been looking for a bit of linux development to try for a while, this may be a bit hardcore for a n00b to linux coding but we can but try :lolflag:

thanks again for your help

---

