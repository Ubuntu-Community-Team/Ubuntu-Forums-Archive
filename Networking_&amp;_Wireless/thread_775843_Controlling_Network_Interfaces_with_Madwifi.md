---
title: "Controlling Network Interfaces with Madwifi"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by CoffeeBreath on 2008-04-30
Hi
I've been fooling around with kismet and occasionally it will stop without a prompt from me. When I restart it will say that wifi0 as a problem with my madwifi-ng drivers, and then I can't restart it (kismet). The only way I can restart kismet at this point is by restarting the computer.
Instead of restarting the computer, I've tried I can use "airmon-ng stop "ath0" and wlanconfig to destroy the VAP's but I can't seem to get them back up. I'm guessing I need to restart the interfaces to the same condition they were in before I started kismet. Can someone tell me how to restart the network interfaces without restarting the computer or give me any other advice?

---

### Post by Monicker on 2008-04-30
> **CoffeeBreath said:**
> Hi
I've been fooling around with kismet and occasionally it will stop without a prompt from me. When I restart it will say that wifi0 as a problem with my madwifi-ng drivers, and then I can't restart it (kismet). The only way I can restart kismet at this point is by restarting the computer.
Instead of restarting the computer, I've tried I can use "airmon-ng stop "ath0" and wlanconfig to destroy the VAP's but I can't seem to get them back up. I'm guessing I need to restart the interfaces to the same condition they were in before I started kismet. Can someone tell me how to restart the network interfaces without restarting the computer or give me any other advice?


Kismet creates its own vap for atheros cards, so you should not need to use wlanconfig or airmon-ng at all.  If you are manually creating vaps then they are probably interfering with the one which kismet creates - kis0, iirc.

There is an option is kismet.conf to let it destroy other vaps as necessary, if you want to let it handle that for you.

---

### Post by CoffeeBreath on 2008-04-30
> **Monicker said:**
> Kismet creates its own vap for atheros cards, so you should not need to use wlanconfig or airmon-ng at all.  If you are manually creating vaps then they are probably interfering with the one which kismet creates - kis0, iirc.

There is an option is kismet.conf to let it destroy other vaps as necessary, if you want to let it handle that for you.

Is "ifconfig ath0 down" enough to stop it from interfering with kismet? Or do the other vaps need to be destroyed. Is there a difference between destroying and the down command? Once they are "destroyed" how do I get them back to their original condition?

---

### Post by Monicker on 2008-04-30
> **CoffeeBreath said:**
> Is "ifconfig ath0 down" enough to stop it from interfering with kismet? Or do the other vaps need to be destroyed. Is there a difference between destroying and the down command? Once they are "destroyed" how do I get them back to their original condition?

Down is not sufficient.  With multiple vaps present any devices trying to use monitor mode may not receive the proper information.  I believe this is a limitation of the drivers.  Also make sure your kismet source is pointing at the wifi0 interface.

Did you check the config to verify whether or not Kismet is already set to destroy other vaps?  I can't recall which version introduced this feature, but its been there for a while.

As for recreating a vap:

```
wlanconfig ath create wlandev wifi0 wlanmode sta
```

That will create a vap which is in managed mode, for normal wireless connectivity.

---

### Post by CoffeeBreath on 2008-04-30
> **Monicker said:**
> Down is not sufficient.  With multiple vaps present any devices trying to use monitor mode may not receive the proper information.  I believe this is a limitation of the drivers.  Also make sure your kismet source is pointing at the wifi0 interface.

Did you check the config to verify whether or not Kismet is already set to destroy other vaps?  I can't recall which version introduced this feature, but its been there for a while.

As for recreating a vap:

```
wlanconfig ath create wlandev wifi0 wlanmode sta
```

That will create a vap which is in managed mode, for normal wireless connectivity.


I get this error: wlanconfig: ioctl: Input/output error

any suggestions anyone?

---

### Post by Monicker on 2008-04-30
> **CoffeeBreath said:**
> I get this error: wlanconfig: ioctl: Input/output error

any suggestions anyone?

Did you prefix it with sudo?


```
sudo wlanconfig ath create wlandev wifi0 wlanmode sta
```


I still forget to add that on the forum sometimes.  Still used to just becoming root on the other linux machines I use.  :)

---

### Post by CoffeeBreath on 2008-04-30
Yep. I do.

---

### Post by Monicker on 2008-04-30
> **CoffeeBreath said:**
> Yep. I do.

What is the output of the following:

```
ifconfig -a
iwconfig
```

---

### Post by CoffeeBreath on 2008-04-30
xccc

---

### Post by CoffeeBreath on 2008-04-30
The strang thing is that i can use wlanconfig to get a vap in monitor mode but can't use it to get back to managed mode after I've detroyed one.

---

### Post by Monicker on 2008-04-30
> **CoffeeBreath said:**
> The strang thing is that i can use wlanconfig to get a vap in monitor mode but can't use it to get back to managed mode after I've detroyed one.


Hrmm. I dunno then.  I have never run into that when creating a vap in managed mode.  

Search for that error at the aircrack forum. There might be something relevant.

[http://forum.tinyshell.be/]("http://forum.tinyshell.be/")

---

