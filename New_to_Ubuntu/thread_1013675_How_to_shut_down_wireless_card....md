---
title: "How to shut down wireless card..."
date: 2008-12-17
forum: New to Ubuntu
---

### Post by nech.q on 2008-12-17
i got a dlink wireless card, but when i try to shut down original eth wireless card, following thing happened:

$ sudo ifdown eth1
[sudo] password for lala: 
Ignoring unknown interface eth1=eth1.

BTW, my new wireless card is d-link dwl-g650+, is there an appropriate driver for it?

---

### Post by kpkeerthi on 2008-12-17
What does ```
iwconfig
``` print?

---

### Post by nech.q on 2008-12-17
:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Adelaide Unit"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:27:BF:03:52   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:4

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Adelaide Unit"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:27:BF:03:52   
          Bit Rate=48 Mb/s   Tx-Power=16 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=92/100  Signal level:-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

[COLOR="Red"]:~$ sudo ifdown eth1
Ignoring unknown interface eth1=eth1.

:~$ sudo ifdown eth1
ifdown: interface eth1 not configured
[/COLOR]
**same command, different results :-(**

:~$ ifdown eht1
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied

**ifstate can't be opened btw, as the system told me, i'm not the OWNER of my laptop...**

---

### Post by hyper_ch on 2008-12-17
why is eth1 there a wireless device? actually exactely the same as wlan0? did you bridge somehow?

---

### Post by nech.q on 2008-12-17
Actually i got two wireless cards in my laptop, one is on the mainboard, the other is card bus

---

### Post by hongri1998 on 2008-12-17
**[ball valve](http://www.valvesupplier.net/petro-valve.htm)** featuring with uni-body, top entry trunnion mounted ball. This type of valves gives convenient of in-line repair or replace valve internal components without dismantling it from pipeline. series [ball valve]("http://www.valvesupplier.net/petro-valve.htm") is all fire safe designed comply with API 607 & API 6FA.

---

### Post by hyper_ch on 2008-12-17
and you want to disable the onboard one? If so, you could do this in the BIOS.

---

### Post by Marabu on 2008-12-17
what about this:

```
ifconfig eth1 down
```

Michael

---

### Post by nech.q on 2008-12-17
:~$ ifconfig eth1 down
SIOCSIFFLAGS: Permission denied

Onboard one could not be shut down in CMOS, there is one button built in my laptop for wireless control, if i press it, both of them will be shut down at the same time, any thoughts?

---

### Post by nech.q on 2008-12-18
Help

---

### Post by xjcannonx on 2008-12-18
try sudo in front of ifconfig eth1 down
```
 sudo ifconfig eth1 down
```

---

### Post by nech.q on 2008-12-18
It doesn't work, how come ubuntu can't even shut down a tiny onboard wireless card?
windows can do it by three or four clicks, i can't believe that

---

### Post by theamber on 2008-12-18
> **nech.q said:**
> It doesn't work, how come ubuntu can't even shut down a tiny onboard wireless card?
windows can do it by three or four clicks, i can't believe that

Most laptops have a Fn+ some f keys to shut down the wireless, but your has a buttom you said that disables the card buss too, that is strange since that buttom just remove power to the card. 
The only thing you can do is remove the two screws that hold the wireless cover and take it out is like removing a RAM stick, also you can disable the driver.Or change devices here /etc/X11/xorg.conf

---

### Post by hyper_ch on 2008-12-18
> **nech.q said:**
> It doesn't work, how come ubuntu can't even shut down a tiny onboard wireless card?
windows can do it by three or four clicks, i can't believe that

of course ubuntu can... you just didn't figure it out yet... and did you try to disable it in the bios?

---

### Post by newbee70 on 2008-12-18
> **nech.q said:**
> It doesn't work, how come ubuntu can't even shut down a tiny onboard wireless card?
windows can do it by three or four clicks, i can't believe that

what happens if you left click on the network icon on the upper left toolbar. 

can you shut it down here. or if you right click the network icon can you shut it down there?

"I only have 1 card so I don't know for sure."

---

### Post by nech.q on 2008-12-19
Cheers bodies, i'll try what u guys told me

---

