---
title: "Apt/Synaptic problem"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by caravel on 2009-04-10
Running Ubuntu 8.10 64bit with an rtl8180 wireless adaptor.  This is pretty much a clean install.  All I've done is fully update and enable the restricted driver for my ATI graphics card.

The problem I'm having is a strange one.  I have two other machines connected to a wireless router and whenever I download anything through apt or synaptic it seemingly uses the entire wireless network bandwidth.   When I am downloading anything, these other machines cannot even browse to a webpage.  The requests time out.  Also browsers on this machine have the same problem.  It's as if apt is consuming the entire bandwidth.

Any ideas as to what could be causing this.

Thanks in advance

---

### Post by Paqman on 2009-04-10
Your router handles stuff like this. Even if one machine is chewing through a lot of bandwidth, it should send some packets the way of the other machines. So i'd say the first place to look would be in your router settings, maybe yours has some weird feature you can fiddle with. Do you know how to access your router's settings page in your browser?

---

### Post by sowelie on 2009-04-10
That is strange...what do you have for a connection?  My best guess is that you are actually having router troubles.

---

### Post by caravel on 2009-04-10
Well the router was fine under XP.  I haven't had this problem in the past either.  It's all properly configured.  I'm thinking that the wireless NIC linux driver might be the issue?  I get decent speeds but the link quality is always very low.  The small signal strength meter in the menu bar is only ever on the first bar also - strangely this was also the case in 8.10 32 bit but I don't remember any issues with that.  This was running perfectly under Windows XP.

Is ndiswrapper advisable?  I've been reluctant to go down that route in the past as I dislike messy emulation involving windows files etc.

```
caravel@caravel-desktop:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point:    
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=8/100  Signal level:-174 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

caravel@caravel-desktop:~$
```

---

### Post by sowelie on 2009-04-15
Are you dual booting with Windows?  If you log into Windows now you're saying you don't see the same problem?  I am not familiar with ndiswrapper as I've never had wireless trouble with Ubuntu.

---

