---
title: "how to set the wireless card ad-hoc up?"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by liaommx on 2008-10-19
i have a new nb and install it as ubuntu.
and i use the wireless card by PCMCIA one.
the card is CISCO AIR-CB21AG-W-K9

but i can't communicate with two ubuntu by ad-hoc.

i edit the  /etc/network/interface

```

iface ath1 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
wireless_mode ad-hoc
wireless_essid test
wireless_channel 1
wireless_power on

```

and and try to start the setting

```
sudo ifup ath1=ath1
```

but the error occurs.

```

error for wireless request "set mode" 8b06
error for wireless request "Set Power Management" (8B2C)

```


and i try to see the iwconfig 

the mode show by iwconfig
```

wireless mode:managed
access point:not-associated

```

how could i start the ad-hoc mode?

---

### Post by superprash2003 on 2008-10-19
hope this gives you an idea [http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html](http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html)

---

### Post by TenPlus1 on 2008-10-19
Here is my /etc/network/interfaces file which runs an ad-hoc wireless network, hope it helps:

auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.0.1
netmask 255.255.255.0
wireless-mode ad-hoc
wireless-keymode open
wireless-key s:password
wireless-essid wirenet

auto wlan0

---

### Post by liaommx on 2008-10-20
> **superprash2003 said:**
> hope this gives you an idea [http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html](http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html)

i find some technical docs.

but i still have problem when step 4
```
sudo iwconfig eth1 mode ad-hoc
```

when i enter the command.

```

ck@ck-laptop:~$ sudo iwconfig ath0 mode ad-hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.


```
mine wireless card is ath0 

so i can't continue the next step .

i know how to use ad-hoc.

but i can't start the ad-hoc mode of my wireless card :(

anyway thank you for your answer.
your website is helpful for me

---

### Post by liaommx on 2008-10-20
> **TenPlus1 said:**
> Here is my /etc/network/interfaces file which runs an ad-hoc wireless network, hope it helps:

auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.0.1
netmask 255.255.255.0
wireless-mode ad-hoc
wireless-keymode open
wireless-key s:password
wireless-essid wirenet

auto wlan0



i don't have the wireless-key..
i think i don't have to type the password,is that right?

the last line " auto wlan0" 
is this mean the config will auto config to device "wlan0"?
my device is ath0 ,so i need to change it to the "auto ath0"

right?

---

