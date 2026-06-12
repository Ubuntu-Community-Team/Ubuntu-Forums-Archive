---
title: "kismet configuration"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by xiaomahe on 2009-01-09
hai, i am trying to setup my kismet configuration file.

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
[COLOR="SandyBrown"]source=none,none,addme
[/COLOR]

i am wondering on how to fill up those 3..

first is my wireless card driver is it? or the ethernet controller when i run lspci.. if so my wireless card is intel  wireless 3945 abg while ethernet controller is broadcom corporation netlink BCM5789.. so which 1 i have to fill in for the first field??

second one is our interface card right? when i run iwconfig.. this is the result

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"sasdasd"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:08:7A:BC   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=71/100  Signal level:-63 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


see all the interface doesn't have any wireless extensions.. how i can solve this? how do i feel the second part?

and finally what do i have to fill in the third part?

---

### Post by albinootje on 2009-01-09
> **xiaomahe said:**
> hai, i am trying to setup my kismet configuration file.

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
[COLOR="SandyBrown"]source=none,none,addme
[/COLOR]

i am wondering on how to fill up those 3..
That should be explained in the kismet documentation.
Check the text files in /usr/share/doc/kismet/ or visit the kismet website.

The second one would be wlan0 as I doubt wmaster0 would have to go there.

---

