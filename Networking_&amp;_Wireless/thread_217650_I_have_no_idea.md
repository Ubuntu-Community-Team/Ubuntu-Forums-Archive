---
title: "I have no idea"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by spreelinux on 2006-07-17
I just downloaded ubuntu linux today, another person sick of windows.I've searched around these boards for fixes and those common problems but none of it works. My network card is frozen .. all 3 lights are on and not blinking or anything. I've tried to reset it but I keep getting the same response.. does not respond.

My guess is the drivers are not correct but unfortunetly I'm writing this throught my Mac Laptop.( I switch the ethernet cable back to the PC when attempting a fix ) 

typing in <lspci> the card is shown { 0000:00:09.0 ethernet controller: intel corporation 82557/8/9 [ethernet pro 100] (rev 02) }

it sees the hardware yet its frozen. I'm stuck and been messing around with it for 2 or 3 hours now. Any help?  ](*,) 

( I would like to note that in my opinion the auto detection of the speed. When I was using windows I always changed the cards speed to 100megabytes/ full duplex, after that it connected. I don't know if this would be the same issue or not.)

---

### Post by philippe_carlo on 2006-07-17
Is the network card's module loaded? What does 
```
sudo ifconfig
```
produce?

---

### Post by spreelinux on 2006-07-17
It produces something like this ```
eth0    Link encap: Ethernet HWaddr 00:A0:C9:35:b2
        UP BROADCAST MULTICAST MTU: 1500 Metric: 1
        RX packets: 0 errors: 0 dropped: 0 overruns:0 frame: 0
        TX packets: 0 errors: 0 dropped: 0 overruns 0 carrier: 0
        collisions: 0 txqueuelen: 1000
        
        RX bytes: 0(0.0 b) TX bytes: 0(0.0b)

lo      Link encap: local loopback
        inet addr: 127.0.0.1 Mask 255.0.0.0
        inet6 addr: ::1/128 Scope:HOst
        UP LOOPBACK RUNNING MTU:16436 Metric: 1
        RX packets: 21 errors: 0 dropped: 0 overruns:0 frame: 0
        TX packets: 21 errors: 0 dropped: 0 overruns:0 carrier: 0
        collisions: 0 txqueuelen: 1000
        
         RX bytes: 1456(1.4 KiB) TX bytes 1456(1.4 KiB) 
```


I think its a bit off at the end. But thats what it looks like.

---

### Post by philippe_carlo on 2006-07-18
At least the module seems to be loaded just fine. The fact that there a no blinking lights is not a good sign. Try unloading the network card's module and reloading it again:
```

sudo rmmod <module name>
sudo modprobe <module name>

```
Next, see what ```
dmesg | tail
``` comes up with.

---

### Post by spreelinux on 2006-07-18
I did those commands. Looks like I did somewhat manipulate the driver on <dmesg | tail> after I put in the sudo commands, the lights are still not blinking though. Disabled IpV6 and still nothing happened. Maybe I should get another network card :p 
All my stuff is quite legend being 3-4 years old.

---

