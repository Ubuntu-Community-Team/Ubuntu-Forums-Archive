---
title: "Apple roughter not registering"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by AxelFlames on 2009-08-30
[SIZE=2]ok i have a Apple wireless router at home but its not recognised by Ubuntu for some strange reason,

i can connect tto it fiine though Vista but i don like usin it for some obvious reasons....

it has wep personal
i got the pw and all the info to get in,
it just doesnt register to my acer notebook

i tried doing the hidden wireless network thingy and entering info but it still didnt work or pop up.

i am verry new to ubuntu, barely know how to do anything beyond click, drag, and type.
can i have some step by step 'understandable' help please?


- it actually works fine on my psp, though it showed up only as a blank weak signal at 7% , once i put in thessid, it suddenly became 99% and i had connection... it just doesnt work with ubuntu it seems
[/SIZE]

---

### Post by iver2435 on 2009-08-30
Have you been able to successfully connect to other wireless routers with your Ubuntu installation?  It could be that you need to look at getting the proper drivers installed.

try running: 

```
iwconfig
```

and see what comes up.  If you feel inclined, post the output of the command here and we can help further.

---

### Post by AxelFlames on 2009-08-31
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by AxelFlames on 2009-09-02
anyone help?
i have no idea what it means
:(

---

