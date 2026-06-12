---
title: "MAC address changes after reboot"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by zend on 2007-06-22
I need to have an IP address that doesn't change since I port forward in linux and windows on my computer.   I've always used a IP address linked to my MAC address on my router.  

I just changed my motherboard and now everytime I reboot my computer is getting a different IP address.  I checked, and it seems that the MAC address in Linux changes evertime I reboot.  Consequently, my router assigns a new IP address after every reboot.

How does this happen?  I thought each network card only had one MAC address.

I'm using Ubuntu version 7.04.

Anyone have any ideas how to make this stop?

I know I could just assign a static ip in both Linux and windows, but I'd rather not since sometimes I switch my machine to my second network, and I don't want to have to redo the networking every time I do.

---

### Post by chippy99 on 2007-06-23
You are quite right MAC addresses do not change and are unique. The only thing I can think of is that your router is not recognising your mac address and using dhcp to provide your IP address.

Check that hw address from ifconfig is exactly the same as MAC address you have entered into the router.

---

### Post by scrupul0us on 2007-06-23
what evidence do u have to support that the mac changes? where are you checking the mac address?

---

### Post by zend on 2007-06-23
When I type ifconfig it shows a different HWAddr.

---

### Post by zend on 2007-06-24
Anyone have any ideas for how I can fix this?

---

### Post by zend on 2007-06-24
This is really causing me problems.  I have a piece of software linked to my MAC address.  I can't get it to install.

---

### Post by zend on 2007-07-08
Just in case anyone else has this problem, I thought  I'd post what I did to fix my issue.  I booted into windows and wrote down the MAC address since it didn't seem to change in windows.  I then booted back into Ubuntu and edited the file:

/etc/init.d/bootmisc.sh

At the bottom of the file I added the following:

```

killall dhclient
killall dhclient3
ifconfig eth1 down
ifconfig eth1 hw ether MY:MA:CA:DD:RE:SS
ifconfig eth1 up
/sbin/dhclient
/sbin/dhclient3


```

Now it always sets the same MAC and my IP is always the same from the router.

---

### Post by jimmygza on 2008-07-23
I have the same problem, but worst, because every time I reboot I get eth(n+1) so I'm now in eth11 and it has gone like that from eth0. Apparently the kernel assigns a new ethx for every new MAC Address.

Can someone please help me?

Cheers!

Jimmygza

---

