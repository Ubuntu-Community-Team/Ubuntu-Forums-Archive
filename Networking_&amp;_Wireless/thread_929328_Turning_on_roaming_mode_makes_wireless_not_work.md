---
title: "Turning on roaming mode makes wireless not work?"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by smiley505 on 2008-09-24
I've been using Ubuntu for months now on my 'extra' laptop, a Dell Inspiron 2650.  Everything has worked just fine, included my wireless via ndiswrapper, for as long as I've had it basically.

Last week, I enabled 'Roaming Mode' via the Manual Configuration Tool for networking settings (found up in the right panel next to the date and volume settings).  Roaming mode worked just fine; I had internet and everything.  Then, I shut it down.

When I booted it back up again, the Manual Config Tool did not have my wireless connection in the tool.  Which is odd.  I checked ifconfig and wlan0 didn't even show up.  But the card has the power light on.  

I started checking ndiswrapper.  Not only is the driver still there, it also recognizes that the device is present.  Here's the output:

kevin@KDW-Ubuntu:~$ ndiswrapper -l
net8180 : driver installed
        device (10eC:8180) present
kevin@KDW-Ubuntu:~$

Why wouldn't the tool find the wireless device and connection if it's found by ndiswrapper?  Why would enabling 'Roaming Mode' cause such a problem?

I don't even care about roaming mode...I'll never use it again if I can just get the connection back.

Help???

KDW

---

### Post by summertanks on 2008-09-24
kevin 
having the same problems... 
posted my issue too....
i think we have to artificially recreate the wlan0 in the config files. sad bit is have no idea how to do it... which are the files which define eth0...? may be we can force feed a wlan0 into it too...

keep me updated if u get something...
thnx

---

### Post by willca on 2008-09-25
I assume you are using dhcp.

Can you paste the contents of this file.

/etc/network/interfaces

---

### Post by smiley505 on 2008-09-25
kevin@KDW-Ubuntu:~$cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 10.0.10.145
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp



auto eth0
kevin@KDW-Ubuntu:~$

---

### Post by superprash2003 on 2008-09-25
post output of iwconfig and lshw -C network

---

### Post by smiley505 on 2008-09-25
kevin@KDW-Ubuntu:~$ iwconfig
lo       no wireless extensions

eth0     no wireless extensions


kevin@KDW-Ubuntu:~$ lshw -C network
.
.
.
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=64 mingnt=32
kevin@KDW-Ubuntu:~$

---

### Post by summertanks on 2008-09-26
ok... try this...

1. install backports
2. kernel parm noapic
3. put ur eth0 in dhcp... (correction sorry :( )
4. an asprin

and call me in the morning... :)

---

### Post by superprash2003 on 2008-09-26
[http://ubuntuforums.org/showthread.php?t=95879](http://ubuntuforums.org/showthread.php?t=95879)

---

### Post by smiley505 on 2008-09-26
summertanks:  What did that allow you to do?  It looks like it just gets your eth0 connection to use wireless???

superprash2003:  Will compiling that source and adding those two lines fix my card?  Or is it a workaround?

Thanks!!!

---

### Post by summertanks on 2008-09-26
well earlier... when i turned on roaming... the wlan0 dissapeared all to gether
check ur logs ... if there is a complain abt MAC in deep sleep... the kernel parm and backports should help. somehow kernel now remembers to wake up the card...

its not clear why it worked... but 'something' caused something to happen. if we can replicate it in ur system then we know 'something' worked. then we can figure out...why!!!

ps: correction to the earlier scrap... its dhcp and not roaming (sorry abt that)

---

### Post by smiley505 on 2008-09-26
summertanks:  Great!  Couple questions though...

1)  When you say backports....which ones in particular?  Can you outline the process to do so (if not for me, for any other who will see this).

2)  The kernel parameter thing?  How is that done?

3)  Which logs do you find the MAC notifications/errors in?

Thanks!!!

KDW

---

