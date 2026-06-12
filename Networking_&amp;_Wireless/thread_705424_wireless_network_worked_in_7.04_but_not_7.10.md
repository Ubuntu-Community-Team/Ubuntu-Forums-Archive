---
title: "wireless network worked in 7.04 but not 7.10"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by travelor on 2008-02-23
I did a search, and read through of some people who had similar problems but the solutions provided did not help.

I have a T20 thinkpad with (currently) Ubuntu 7.10. I have a Orinoco Gold card to connect to my dlink router. I had originally started out with Ubuntu 7.04 and had that version for quite awhile, which automatically setup my wireless card, and could see my router, along with the 4 others in my neighborhood. After the system crashed during an upgrade to 7.10 I was forced to do a new installation of 7.10 using the alternate cd because of my savage video card did not like the live cd.

The built in nm-applet network manager worked fine on wired, but did not see any wireless signals - I checked with my pda phone, and I seen them all.

I read about a different manager called wicd that people had success with but it too does not see any signals. Nothing on my laptop has changed except for the core operating system, so I am stuck as to why it does not see any networks.

Anyone have any idea why that is?

---

### Post by Paris Heng on 2008-02-23
Ok, how about the Orinoco Gold card' driver? Did you installed correctly? I not sure what type of driver this NIC using. Yes. WICD did performed well instead of NM. Can you do the scanning with your Orinoco card if your driver is not a problems.

> iwconfig <interface> scan

---

### Post by travelor on 2008-02-23
Like I said, in 7.04 it installed it properly without me doing anything. I didn't have to install the drivers first time around.

I ran your command and it errored out. It bothers me that instead of my wireless card is listed as eth1.

@neen1090:~$ iwconfig eth1 scan
iwconfig: unknown command "scan"
@neen1090:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"NETGEAR"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:FC:B5:58   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=8/92  Signal level=-87 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have no idea why the essid is set to "netgear" or what the nickname is.

---

