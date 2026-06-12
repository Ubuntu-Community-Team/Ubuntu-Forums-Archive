---
title: "Wifi problem after update?"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by Symbiote on 2008-05-23
hello,

until today my wifi was working fine but when I started my computer again, it just couldn't connect and knetworkmanager wasn't probably recognizing it at all... it started after installing updates from adept and rebooting my notebook so I thought about some kind of bug or something... I am using Kubuntu 8.04 on Lenovo Thinkpad R61i... wireless device is Intel 4965 AGN...

do you have any ideas what might be the problem?

---

### Post by superprash2003 on 2008-05-23
go to the terminal and type iwconfig and post output here

---

### Post by Snappo on 2008-05-24
> **superprash2003 said:**
> go to the terminal and type iwconfig and post output here

no wireless devices

---

### Post by Symbiote on 2008-05-24
symbiote@symbiote-notebook:~$iwconfig
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr: off   Fragment thr:2346 b
          Power Management: off
          Link Quality=0  Signal level=0  Noise level=0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by superprash2003 on 2008-05-24
see if you can enable any restricted drivers.. system->administration-hardware(restricted) drivers manager

---

### Post by xp_newbie on 2008-05-24
> **superprash2003 said:**
> see if you can enable any restricted drivers.. system->administration-hardware(restricted) drivers manager
I have the same exact problem in my Lenovo 3000 laptop, with the same exact output:


> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


And I tried what you suggested, but the 'Hardware Drivers' dialog comes up with an empty list saying: "No proprietary drivers are in use on this system".

What do I do next?

Thanks,
Alex

---

### Post by gimmic on 2008-05-24
Having similar problems on kernel 2.6.25+. iwlist says network is down.

On 2.6.24, my 4965 AGN works fine but causes a kernel panic during heavy network usage. 

What kernel are you using?(uname -r)

---

