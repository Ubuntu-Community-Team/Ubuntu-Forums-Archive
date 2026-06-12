---
title: "Problem with aircrack-ng"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by alizadeh_omid on 2008-12-01
Hi,

I have prob with aircrack-ng.

I can't use airodump-ng, I got this error:

ioctl(SIOCSIWMODE) failed: Invalid argument
Error setting monitor mode on eth1

I have vostro 1400 and my wireless interface is Intel 1395.

Please Help me!:(

---

### Post by vagelism on 2008-12-01
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ifconfig ath0 up


Try the above commands...
BUT why eth1 I think it sould be ath0.
I am also a new one.
Hope i had helped you.

---

### Post by al_mckin on 2008-12-01
> wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ifconfig ath0 up

wlanconfig is only for atheros chipsets using the madwifi driver.

How to set monitor mode depends on the chipset.
Aircrack-ng comes with an excellent script to do this for you called airmon-ng.

```
sudo airmon-ng start eth1
```

If this doesnt work I cant help!

Alastair

---

### Post by alizadeh_omid on 2008-12-02
Thank you for your comments but I have tried airmon-ng it says monitoring is enabaled on eth1 but when I use airodump-ng it says:
> 
ioctl(SIOCSIWMODE) failed: Invalid argument
Error setting monitor mode on eth1


please help me!

---

### Post by al_mckin on 2008-12-02
What driver are you using for the adapter?
I'm not sure what the chipset you are using is.

Type:

```
ls -l /sys/class/net/eth1/device/driver
```

And paste the output.

---

### Post by alizadeh_omid on 2008-12-04
I got this output:
> lrwxrwxrwx 1 root root 0 2008-12-04 09:17 /sys/class/net/eth1/device/driver -> ../../../../bus/pci/drivers/wl


my wireless driver is "wl" and when I use airmon-ng I get this message:

> 
Interface	Chipset		Driver

eth1		UNKNOWN		wl (monitor mode enabled)


---

### Post by waffen on 2008-12-18
I have the same result, any idea??

---

### Post by Marques de Sade on 2009-01-27
I have a new problem.

With Ubuntu 8.04 Hardy heron.

Before upgrading my version, I had kernell 2.26.19 and aircrack-ng 0.9 was function correctly.
I forgot include the ipwraw in the black list so I added it, but driver doesn't worked. So I reinstalled the ipwraw-ng driver adding it to the black list. 

 After I used the Ubuntu's upgrading tool, it upgraded the system to 2.26.23 kernell version, including the upgrade to aircrack-ng.

Now I try to continue with scanning, I start with airodump-ng and my system get freeze, It haven't ocurred to me until now, and I need to capture more .IVs, I so close to crack the wep. 

What&#347; happening to my system? ubuntu never freeze with other applications.

I'm waiting for responses.
Thanks,
Sade

---

