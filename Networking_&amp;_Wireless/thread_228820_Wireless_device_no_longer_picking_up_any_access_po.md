---
title: "Wireless device no longer picking up any access points!"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by Grog140 on 2006-08-03
It was working perfectly today up untill about half an hour ago when my connection just dropped. 

When I went into network connections to see what was the problem I couldn't choose my essid (or any)

Here is when I try and scan:

```
matthew@matthew-laptop:~$ iwlist eth1 scan
eth1      No scan results

```

I have a broadcomm device running off of ndiswrapper. And again, it was working fine earlier today. As in half an hour ago earlier.

Thanks

---

### Post by ajgreeny on 2006-08-03
Are you sure your telephone line is working?  If you dual boot with windows, try that, if you don't dual boot try with the live CD, or any other live CD to see if your ADSL is OK.

---

### Post by Grog140 on 2006-08-03
No, my other computer is connected via a wire and it is working fine.

Hmm...the hardware is still detected by ndiswrapper so it isn't malfuctioning its just not scanning or connecting to any essid.

---

### Post by Grog140 on 2006-08-03
I think I may have isolated what exactly is causing the problem...

```
matthew@matthew-laptop:~$ iwconfig eth1 essid linksys
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Operation not permitted.

```

I don't know what is causing the error but I am searching...

---

### Post by aquaxbat on 2007-01-08
I am in a similar boat as you but I have yet to see any networks. I know for a fact that when I had windoze on my laptop, it picked up mine as well as a few others. I finally got Edgy to see my stupid broadcomm wireless card but I can't see any networks at all.

```
root@peyote:/home/ryan# iwlist wlan0 scan
wlan0       No scan results
```

But I do know that my linksys router is configured correctly for wireless. Anyone know what I need to do to have my wlan card see networks?? 

I even forced it to see my wnetwork and everything and it won't see it not anyone else's.

---

