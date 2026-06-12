---
title: "Broadcom wireless card turns itself off"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by Zyrshnikashnu on 2007-11-15
I'm using Ubuntu 7.10 and wicd for my network manager.

I have a Broadcom 4311 chipset with my Dell Inspiron 1420. When I boot up, the hardware is fine. The blue LED light comes on and I can connect to my university's WPA networks without too much issue.

The issue comes after connecting. Often, the light will turn off without warning. Nothing I do can turn it back on. The card is definitely off, since wicd is suddenly unable to find any networks.

While the LED is off, I get periodic dmesg outputs reading something like "IRQ_TIMEOUT". No other messages are relayed. I'm sorry I don't have the exact output (is dmesg archived?), but I'll update the thread the next time it happens.

I can't switch back to network-manager, since it can't seem to handle my school's WPA networks anymore. I don't know why this is (it handles other encrypted networks without too much trouble).

Any help is appreciated.

EDIT:

The only relevant dmesg output is

bcm43xx: IRQ_READY timeout

I get the output every several seconds after the failure occurs.

---

### Post by dfme on 2007-11-16
hi,
try this command and post the result:
```
dmesg | grep switch
```

---

### Post by Zyrshnikashnu on 2007-11-16
Like I said, I can't provide much information before the problem occurs. I'll save the output before I restart next time.

Anyway, before the loss of wireless:

**dmesg| grep switch**
```
[    9.665787] SMP alternatives: switching to UP code
[   10.222476] SMP alternatives: switching to SMP code
```

---

### Post by dfme on 2007-11-17
> **Zyrshnikashnu said:**
> 
Anyway, before the loss of wireless:

hi there again...
i would like to know the output after the loss of wireless.

EDIT: Maybe i should clarify why:
i have an old maxdata laptop and the wireless is not working even though the ipw2100 module would support it and the configuration is good.
the thing is that in BIOS the WLAN is enabled but as soon as i boot up the OS the dmesg tells me that the WLAN has been disabled as if the WLAN button had been pushed on the laptop... however nothing happens when i push the button again. this is annyoing and maybe you have the same problem. when doing 
```
dmesg | grep switch
```
you should get something in the line of:
```
eth1: Radio is disabled by RF switch
```

---

### Post by Zyrshnikashnu on 2007-11-17
Yes, I know you want the output after the disabling. I'm not trying to be difficult, honestly. :P

I haven't been using wireless in the past 24 hours, so I can't give you a report. I will bring it up as soon as it happens again.

I will note, however, that I haven't seen any messages related to eth1 (my wireless adapter) around the point that it turns off.

Of course, I'll still run the search. Stick around. Thanks for helping out.

---

### Post by Zyrshnikashnu on 2007-11-25
Ah, it happened again. I was beginning to think the issue had melted away.

I've attached the dmesg output as it read about a minute after the disconnect. I trimmed out a few obviously unrelated bits to keep the file size down to something the forum can handle. As you can see, there is nothing explicitly stated about disabling wireless or a switch trigger.

While trimming the dmesg output, I noticed that both ndiswrapper and the Linux bcm43xx drivers were being loaded. Could this conflict cause the problem?

---

### Post by uscfan185 on 2008-04-22
Hi, I have also had this problem too. When I run dmesg | grep switch after the card turns itself off I get this:
 
```
[39.430888] SMP alternatives: Switching to UP code.
```

Also "bcm43xx: IRQ_READY timeout" appears in my system log multiple times.

Any help would be appreciated. Thanks.

---

