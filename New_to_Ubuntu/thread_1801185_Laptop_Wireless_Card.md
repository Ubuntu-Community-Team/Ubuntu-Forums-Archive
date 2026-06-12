---
title: "Laptop Wireless Card"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by expatCM on 2011-07-10
I do not know how to get wireless working with an HP Pavilion DV2000 laptop.   Could someone please suggest the approach?

The broadcom driver 'Broadcom STA wireless driver' is activated.

The command rfkill list returns the following

0: hp-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no

It does not work though and the orange network light does not turn blue.

So ...  I booted from the CD and got no result.  I connected a D-Link USB wireless card and yes, it works.

The immediate temptation would be to suggest that the built in card is not doing too well but ...   that would not explain why it was working with Windows.

Is there any way to check that the card is actually functional and perhaps this is simply a driver issue?

Yes, I know how to use google.  In this case there are quite a range of differing opinions and even a number of solutions ...  to be found at the end of dead links ...

---

### Post by Bucky Ball on 2011-07-10
Plug in an ethernet cable, get updates, System>Administration>Additional Drivers (or Hardware Drivers depending on your release). You should find the Broadcom drivers there ready to load if they haven't done so automagically.

---

### Post by westie457 on 2011-07-10
> **expatCM said:**
> I do not know how to get wireless working with an HP Pavilion DV2000 laptop.   Could someone please suggest the approach?

The broadcom driver 'Broadcom STA wireless driver' is activated.

The command rfkill list returns the following

0: hp-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no

It does not work though and the orange network light does not turn blue.

So ...  I booted from the CD and got no result.  I connected a D-Link USB wireless card and yes, it works.

The immediate temptation would be to suggest that the built in card is not doing too well but ...   that would not explain why it was working with Windows.

Is there any way to check that the card is actually functional and perhaps this is simply a driver issue?

Yes, I know how to use google.  In this case there are quite a range of differing opinions and even a number of solutions ...  to be found at the end of dead links ...
In a terminal run ```
lspci
```
Click new reply to copy and paste the output so we can see what wifi chip you are using

---

### Post by Bucky Ball on 2011-07-10
westie, please don't quote entire posts for no apparent reason. It is a real scrolling time waster. ;)

Also, the output of: 

```
lshw -C network

```... might be more helpful as it provides the wireless card details plus a lot more info. ;)

---

### Post by gandaran on 2011-07-10
[this]("http://ubuntuforums.org/showpost.php?p=10796508&postcount=44") should help to fix the broadcom drivers problem.

---

### Post by expatCM on 2011-07-10
lshw -C network did not do a lot ....  the -C switch is known but 'network' did not generate a result.

lspci ...  Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

BCM4311 is listed in the description of the active driver.

I just ran apt-get update / upgrade and the system is completely up to date.

---

### Post by Bucky Ball on 2011-07-10
Disable STA driver, open Synaptic Package Manager, search for and install:

firmware-b43-installer
b43-fwcutter

Check 'Additional Drivers' again.

---

### Post by expatCM on 2011-07-10
OK ...   so I am very impressed.

I just installed

firmware-b43-installer
b43-fwcutter

and as soon as Synaptic had completed the task the blue light came on and I was connected to the Internet by a wireless connection.

Thank you all for your help in sorting this out :)

---

### Post by Bucky Ball on 2011-07-10
No probs, good news, and enjoy! That card should work out of the box. The catch 22 is that with Broadcom you generally need to get online with a wired connection to get wireless! That's proprietary drivers for ya. ;)

ps: If you now issue 'sudo lshw -C network' you should get the details of your card, including the IP, rate, AP, driver and other things.

---

