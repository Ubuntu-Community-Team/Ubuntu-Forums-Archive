---
title: "After 14.04 Upgrade Wifi does not coAfter 14.04 Upgrannect after suspend, ralink RT73"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by nknico on 2014-04-21
Hello everybody.

Since my update to 14,04, my wifi chipset is unable to connect after a suspend.

In 13.10 i solved the same problem by writing  SUSPEND_MODULES="rt73usb" in /etc/pm/config.d/load because the wifi chipset didn't wake up after suspend.

But in this case, with 14.04, the chipset is wake up, but completely unable to connect.

```
nico@nico-portable:~&#10219; sudo rfkill list
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```

Many other people seems to have the same problem. For instance : [http://ubuntuforums.org/showthread.php?t=2218043](http://ubuntuforums.org/showthread.php?t=2218043) and [http://ubuntuforums.org/showthread.php?t=2218445](http://ubuntuforums.org/showthread.php?t=2218445) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1286552](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1286552)

```
nico@nico-portable:~&#10219; lsmod |grep rt
rt73usb                26890  0 
rt2x00usb              20041  1 rt73usb
rt2x00lib              48886  2 rt73usb,rt2x00usb
```

---

### Post by squakie on 2014-04-21
The Launchpad link you posted to is a bug report for this when waking from suspend - just as you are experiencing.  That bug report does not have a fix yet, so you may not have any choice but to do what the bug report says - restart you PC.

---

### Post by nknico on 2014-04-21
Thank's for your reply.

The bug doesn't have a fix yet, just beacause it is not assigned to anybody !!

I am installing 3.14 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline) as sugested in one bug's duplicate.

---

### Post by nknico on 2014-04-21
Bug also present with 3.14-1 kernel

---

### Post by mih-com on 2014-04-21
i try also 3.11.0-19 - may be bug not in kernel?
who have 13.10 ? you can try new kernels

---

### Post by mih-com on 2014-04-21
[https://bugs.launchpad.net/ubuntu/+s...x/+bug/1286552]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1286552") here 13.10 bug, but i normaly work in 13.10 with kernel 3.11 
bug may be in new network-manager, but i cant understand, why reboot not helped
i try reload modules( they normaly load|unload), restart network-manager, write config to pm suspend_modules, all not helped

---

### Post by mih-com on 2014-04-21
strange thing,i boot in 3.11 for test, go to suspend, wake up - wifi not connecting, after in root terminal type:
iwconfig
iwlist wlan0 chan
iwlist wlan0 scan
i not stop network manager and on last command i see error in console something like "resours busy" and network-manager connect to wifi in same time
after this i try some times go to suspend and wake up, boot in 3.13 and test again, my wifi connect every times. 
 magic?)
PS: try again before post - all worked

---

### Post by squakie on 2014-04-21
You should all add your selves to the bug report as "affects me".

---

### Post by nknico on 2014-04-22
> **mih-com said:**
> [https://bugs.launchpad.net/ubuntu/+s...x/+bug/1286552]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1286552") here 13.10 bug, 

No the bug is saying that it worked with 13.10 and doesn't work after update to 14.04.

Maybe it's not kernel related, cause actualy with 3.11 on 14.04, the wifi doesn't reconnect after suspend either...

---

### Post by nknico on 2014-04-22
> **mih-com said:**
> strange thing,i boot in 3.11 for test, go to suspend, wake up - wifi not connecting, after in root terminal type:
iwconfig
iwlist wlan0 chan
iwlist wlan0 scan
i not stop network manager and on last command i see error in console something like "resours busy" and network-manager connect to wifi in same time
after this i try some times go to suspend and wake up, boot in 3.13 and test again, my wifi connect every times. 
 magic?)
PS: try again before post - all worked

Can you explain us better what did you do exactly ? Thank you in advance. Because, me too, I tried to boot with 3.11, and it doesn't reconnect.

---

### Post by mih-com on 2014-04-22
> **nknico said:**
> Can you explain us better what did you do exactly ? Thank you in advance. Because, me too, I tried to boot with 3.11, and it doesn't reconnect.
then i simple boot in 3.11 have same problem
but then boot and in  termnal typed next commands:
```
sudo -s
[COLOR=#000000]*iwconfig*[/COLOR]
[COLOR=#000000]*iwlist wlan0 chan*[/COLOR]
[COLOR=#000000]*iwlist wlan0 scan*[/COLOR]
```[COLOR=#000000][I]

on last command my netwok-manager connect to my wifi ap, and i dont see "not connected" more
i reboot in 3.13 and all ok
mb 3.11  not neeeded for this, I simple write that i doing before my wifi work again [/I][/COLOR]

---

### Post by nknico on 2014-04-22
I tried it but it doesn't work.

It looks like a proble with NetworkManager and not with kernel

---

### Post by mih-com on 2014-04-23
Yes method not work, after 2 days i have same problem, my instruction not helped me)
I noticed: when wifi not connecting "iwlist wlan0 scan" show me 2 wifi ap's 
they different only mac address: on first cell mac 00:00:00:00:00:00, on second real mac of my ap
I think what problem in wrong mac cell, but in syslog wifi round robin connect  to both aps.
When wifi work good  "iwlist wlan0 scan" not see first ap with wrong mac

---

### Post by squakie on 2014-04-24
Just FYI - this problem is not restricted to just the RT73.  I have RTL8188EE built in to my laptop and have the same problem.  I know "hibernating" and waking up has always been a crap-shoot due to all the differences in hardware.

---

