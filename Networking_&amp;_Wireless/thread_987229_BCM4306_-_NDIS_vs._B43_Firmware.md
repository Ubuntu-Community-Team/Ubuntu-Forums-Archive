---
title: "BCM4306 - NDIS vs. B43 Firmware??"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by caleb12 on 2008-11-19
I've used both methods of getting my BCM4306 v3 wireless card up and working in Intrepid 8.10. There always seems to be a trade-off, in my case it's speed vs. performance. 

When I was using the B43 Firmware, installed according to the description on linuxwireless.com notated [**_here._**]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new") I found that:
```
iwlist rate wlan0
wlan0     unknown bit-rate information.
          Current Bit Rate=1 Mb/s
```

Kinda sucks... And, to make things ever so slightly more annoying, my transfer speed during downloads goes up and down quite a bit... From 500+KBs down to 12KBs, and just kinda seesaws until the transfer is finished. I'm still playing with some settings on the router to help this problem, so I am not entirely convinced it is a B43 Firmware issue... However, I've seen similar problems posted and the other computers in the house which are not running *nix are not having this problem. Although, I admit that it may be a configuration issue with specifics in the router (using DD-WRT firmware there as well - what can I say... I really enjoy Open Source). 

On the plus side, my connection quality is around 90% with:
```
iwlist wlan0 txpower
wlan0     unknown transmit-power information.
          Current Tx-Power=27 dBm  	(501 mW)
```

So, I have some speed issues yet a solid performance level with the B43 Firmware. 

Now, with NDISWrapper... I am using the installed packages from the Ubuntu repos, version 1.52. The latest driver for my specific model and version. And well, the difference will be obvious... 

```
iwlist wlan0 rate
wlan0     4 available bit-rates :
	  6 Mb/s
	  9 Mb/s
	  12 Mb/s
	  18 Mb/s
          Current Bit Rate=48 Mb/s
```

Much better than 1Mb/s... 

```
iwlist wlan0 txpower
wlan0     1 available transmit-powers :
	  32 dBm  	(1496 mW)
          Current Tx-Power:32 dBm  	(1496 mW)
```

Not so good... with connection quality being around 65%. However, I don't notice the speed fluctuation during transfers... it's much more slight a variation of 50 to 100Kb/s - which is to be expected...

Has anyone else noticed anything similar? Are these known issues?? Workarounds???

~~~
[rant] - Linux has become so user friendly over the years, and yet we still run into these issues... *this is not because of Linux* it's due to these companies that develop proprietary firmware to go with proprietary closed source operating systems... It's total and utter crap, in the end we have to rely on various hacks to get wireless working - albeit sophisticated and well coded hacks... they are still hacks. The firmware doesn't natively work with the running kernel - which would solve all these problems. Instead we have to use B43-FWcutter to extract the firmware or NDIS as a wrapper for the firmware. I don't know about anyone else, but my next laptop will be fully supported by Linux - screw HP, screw Dell, and screwwwww BroadCom. [/rant]

---

### Post by arigold1 on 2008-11-19
This is interesting because yesterday I ran ndiswrapper with 8.10 on a gateway laptop that uses a broadcom card and my connection kept dropping, later that day i decided to reformat and used fwcutter and no more connection drops! Also, i did not see any difference in speed either (Through my speedtest.net and dsl reports test)

I'm sticking with fwcutter

---

### Post by yipperzz on 2008-11-19
> **caleb12 said:**
> I've used both methods of getting my BCM4306 v3 wireless card up and working in Intrepid 8.10. There always seems to be a trade-off, in my case it's speed vs. performance. 

When I was using the B43 Firmware, installed according to the description on linuxwireless.com notated [**_here._**]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new") I found that:
```
iwlist rate wlan0
wlan0     unknown bit-rate information.
          Current Bit Rate=1 Mb/s
```

Kinda sucks... And, to make things ever so slightly more annoying, my transfer speed during downloads goes up and down quite a bit... From 500+KBs down to 12KBs, and just kinda seesaws until the transfer is finished. I'm still playing with some settings on the router to help this problem, so I am not entirely convinced it is a B43 Firmware issue... However, I've seen similar problems posted and the other computers in the house which are not running *nix are not having this problem. Although, I admit that it may be a configuration issue with specifics in the router (using DD-WRT firmware there as well - what can I say... I really enjoy Open Source). 

On the plus side, my connection quality is around 90% with:
```
iwlist wlan0 txpower
wlan0     unknown transmit-power information.
          Current Tx-Power=27 dBm  	(501 mW)
```

So, I have some speed issues yet a solid performance level with the B43 Firmware. 

Now, with NDISWrapper... I am using the installed packages from the Ubuntu repos, version 1.52. The latest driver for my specific model and version. And well, the difference will be obvious... 

```
iwlist wlan0 rate
wlan0     4 available bit-rates :
	  6 Mb/s
	  9 Mb/s
	  12 Mb/s
	  18 Mb/s
          Current Bit Rate=48 Mb/s
```

Much better than 1Mb/s... 

```
iwlist wlan0 txpower
wlan0     1 available transmit-powers :
	  32 dBm  	(1496 mW)
          Current Tx-Power:32 dBm  	(1496 mW)
```

Not so good... with connection quality being around 65%. However, I don't notice the speed fluctuation during transfers... it's much more slight a variation of 50 to 100Kb/s - which is to be expected...

Has anyone else noticed anything similar? Are these known issues?? Workarounds???

~~~
[rant] - Linux has become so user friendly over the years, and yet we still run into these issues... *this is not because of Linux* it's due to these companies that develop proprietary firmware to go with proprietary closed source operating systems... It's total and utter crap, in the end we have to rely on various hacks to get wireless working - albeit sophisticated and well coded hacks... they are still hacks. The firmware doesn't natively work with the running kernel - which would solve all these problems. Instead we have to use B43-FWcutter to extract the firmware or NDIS as a wrapper for the firmware. I don't know about anyone else, but my next laptop will be fully supported by Linux - screw HP, screw Dell, and screwwwww BroadCom. [/rant]

i noticed the same thing.  i was playing around last night also and decided to just go with ndiswrapper because the speeds using the b43 was HORRIBLE.  i was testing it out with the 3 routers i have and it's funny because i can connect to one with b43 and another with ndiswrapper.  i'll play with it more tonight but as of now i'm sticking with ndiswrapper.

---

