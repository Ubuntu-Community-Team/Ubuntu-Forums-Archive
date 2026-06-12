---
title: "Kernel Upgrade Broke Wireless"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by kolslorr on 2007-03-27
Hi all, 

I did the most recent kernel upgrade, and after that my wireless is broken. I have to boot into the previous kernel to get my wireless back.

This is the output of my iwconfig when it works (before upgrade)
```

> kolslorr@kolslorr:~$ iwconfig
> lo        no wireless extensions.
> 
> wmaster0  IEEE 802.11g  Frequency:2.447 GHz  
>           RTS thr:off   Fragment thr=2346 B   
>           
> rausb0    IEEE 802.11g  ESSID:"hillstreet"  
>           Mode:Managed  Frequency:2.447 GHz  Access Point: 00:13:10:23:49:F7   
>           RTS thr:off   Fragment thr=2346 B   
>           Link Signal level=-217 dBm  Noise level=-199 dBm
>           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
>           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
>
```

This is the iwconfig when it doesnt work.. (after upgrade)
```

> kolslorr@kolslorr:~$ iwconfig
> lo        no wireless extensions.
>
> rausb1    RT2500USB WLAN  ESSID:"hillstreet"  Nickname:""
>           Mode:Managed  Frequency=2.447 GHz  Access Point: 00:13:10:23:49:F7   
>           Bit Rate=18 Mb/s   
>           RTS thr:off   Fragment thr:off
>           Link Quality=68/100  Signal level:-70 dBm  Noise level:-201 dBm
>           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
>           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
> 
```

I realised that after upgrade, the wmaster0 is missing, can anyone tell me how to correct this? please please...

Thanks~

---

### Post by kolslorr on 2007-03-27
I know it has been less than 1 hour since I posted... but I figured it will end up just like all the other query posts I made, unanswered... 

I actually can see all the available networks, but they are all shown as 0%... So anyway I got it working, here's what I did...

Right click on the Network Manager Icon, and disable it.

Go to System->Admin->Network

Manually configure the remaining network card

Untick the box to disable the card, and retick it back to enable it.

And now I got it working... I guess the network manager screw up.. but I dunno why.. However I do really hope it will be solved since theres no reason to break it on updating kernel... :confused:

---

### Post by kolslorr on 2007-03-31
......

The Feisty Upgrade this morning broke my wireless AGAIN. and this time it dont even work with or without the Network Manager.

.......

*EDIT*
I realised Feisty update reinstalled Network Manager, and re-enable this crap...

so i had to nuinstall it and it works fine again... Using wicd and everythings fine..

---

