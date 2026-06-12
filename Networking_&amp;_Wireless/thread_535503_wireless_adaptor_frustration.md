---
title: "wireless adaptor frustration"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by grantwfuller on 2007-08-26
I need help getting a Linksys WUSB54GC working on Ubuntu 6.10. I am very new to Linux. 
I have gone so far as getting it to work for a few hours but the following day, it would not. While it was working, the WMaster0 did not appear in "Networking" but it has returned as if something is rewriting this conflicting file when loading. I have been working on this for over a week. I have installed ndiswrapper and I have the rt73.inf file installed. I have blacklisted rt2570, I can't remember all the other things I have tried but it would be nice to have a .deb file that would load automatically and solve this. Failing that, can anyone offer some help? I will provide more details is necessary.

---

### Post by chrome307 on 2007-08-26
You most probably know more than me about this but I managed to get online today .... here's the instructions I followed to get online

[http://ubuntuforums.org/showthread.php?t=534617](http://ubuntuforums.org/showthread.php?t=534617)

Hope there's something there that might be useful to you

---

### Post by grantwfuller on 2007-08-27
Thanks, I am still working my way through that thread. No success so far, I wish I knew more command line vocabulary. This is slow going but I would hate to have to go back to Vista. regards, Grant

---

### Post by grantwfuller on 2007-08-27
I think the clue is somewhere in here but I don't know enough to find it or what to do if I found it.
THIS IS FROM TERMINAL $ lsmod
arc4                    3200  1 
rate_control            6784  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
r1000                  17792  0 
sr_mod                 18212  0 
cdrom                  38944  1 sr_mod
sg                     37404  0 
libusual               17040  1 usb_storage
rt73usb                37888  0 
80211                 175880  2 rate_control,rt73usb
crc_itu_t               3200  1 rt73usb
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss

THIS IS THE RESULT OF $ iwconfig

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"grant"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.

RESULTS OF $ ifconfig
~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 b)  TX bytes:480 (480.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1A:70:3A:59:E2  
          inet6 addr: fe80::21a:70ff:fe3a:59e2/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:14976 (14.6 KiB)
          Base address:0xd000 

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-70-3A-59-E2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xd000

RESULTS FROM NDISWRAPPER -L
~$ ndiswrapper -l
Installed drivers:
rt73    invalid driver!
rt73_linux_sta_drv.1.0.4.0      invalid driver!
(rt73 is a folder and inside is the rt73.inf file)
If anyone understands this, please help.

---

