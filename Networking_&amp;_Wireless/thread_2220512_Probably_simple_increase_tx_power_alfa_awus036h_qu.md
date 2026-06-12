---
title: "Probably simple increase tx power alfa awus036h query"
date: 2014-04-28
forum: Networking &amp; Wireless
---

### Post by King_Canute on 2014-04-28
Hi all,
Relatively new ubuntu user here. I am trying to increase the tx power of my alfa awus036h. I realise there is plenty online regarding this issue - and have read much of it - but googling threw up nothing at all regarding my specific query... I expect it is something simple.

On my laptop iwconfig shows my alfa card as being wlan8. Wlan0 is the laptop's internal wireless card - there are no other wireless devices attached to my system. Seems slightly unusual but unless someone tells me that is relevant to my problem I won't dwell on it now!

Below is what I have tried - my query is why is SET failing on device wlan8? Can't seem to figure it out.

root@computer:~# ifconfig wlan8 down
root@computer:~# iw reg set BO
root@computer:~# ifconfig wlan0 up
root@computer:~# ifconfig wlan8 up
root@computer:~# ifconfig wlan0 down
root@computer:~# iwconfig wlan8 channel 13
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan8 ; Device or resource busy.

Thanks in advance for any help!

---

### Post by chili555 on 2014-04-28
> Wlan0 is the laptop's internal wireless card - there are no other wireless devices attached to my system. Seems slightly unusual but unless someone tells me that is relevant to my problem I won't dwell on it now!It's only significant because the wireless drivers may conflict; I'd suggest you blacklist the driver for the internal device.> root@computer:~# iwconfig wlan8 channel 13
Error for wireless request "Set Frequency" (8B04) :
SET failed on device wlan8 ; Device or resource busy.What does that have to do with TX power?

In any case, when the device is in Managed mode, the channel is not available to be set by the user; it is only available to be managed by the router.```
$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          [COLOR="#FF0000"]Mode:Managed [/COLOR] Frequency:2.462 GHz  Access Point: xx:D7:19:41:54:xx 
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm 
```Finally, running as root is dangerous and not recommended. Is this even Ubuntu?

---

### Post by King_Canute on 2014-04-28
Thanks for the reply appreciate it. 

> It's only significant because the wireless drivers may conflict; I'd suggest you blacklist the driver for the internal device.
  
Thanks, I think I know how to do that so will give it a go.

> What does that have to do with TX power?


Nothing I now assume is the answer. There are various discussions on increasing the tx power online - one of which included this line. I wasn't having any luck with the others, so tried this...

> 
In any case, when the device is in Managed mode, the channel is not  available to be set by the user; it is only available to be managed by  the router.

Okay, didn't know that, thanks. I guess this answers my question.

> Finally, running as root is dangerous and not recommended. Is this even Ubuntu?

It is Ubuntu. Although basically a noob, I understand running as root is dangerous. I learn best getting my hands dirty, and it won't be a total disaster if I mess things up. Cheers.

Am going to go away and try again to see if I can more clearly find the problem I am having.

---

