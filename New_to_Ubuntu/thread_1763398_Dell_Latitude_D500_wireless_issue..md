---
title: "Dell Latitude D500 wireless issue."
date: 2011-05-20
forum: New to Ubuntu
---

### Post by Pontster on 2011-05-20
Hello
I've only recently started using ubuntu (10.10) and running it on a relatively old laptop.  It's been working fine up until the last update when the wireless has stopped connecting.  When booting up normally it connected automatically but after the update it tries a few minutes and then says it can't connect.  When I look at available networks I select mine enter my key and then after a few minutes it says it can't connect.  The key is correct as everything else connects fine.

I've had a look at some of the other posts where people have had similar problems but none to do with this dell model which makes me reluctant to run any of the other solutions.

I've run the lspci -v | grep -i Network command and this is what comes back.
Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04).

Can anyone help or have a solution specific to this model please?

Cheers

---

### Post by _0R10N on 2011-05-20
I know this is not a solution, but can be step toward it: does disabling and re-enabling networking solve the problem?. I experienced the same problem with a broadcom network adapter.


Regards!

---

### Post by Coachdbeard on 2011-05-20
If you haven't already, try following the [wireless troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide").  It has been a BIG help to me.
 
My most recent issue was with an upgrade my wireless just wouldn't connect.  Following the troubleshooting guide led me to see that the driver (b43) was there but not loading on start-up.  I put "sudo modprobe b43" in a terminal and it jumped to life.  Maybe it's a similar issue?
 
Good luck!:D

---

### Post by josephmills on 2011-05-20
I do not think that you need the b43 driver that is not the issue lets take a deeper look at that card of yours please open your terminal and type in ```

sudo iwlist eth1 scan

```
```

dmesg | grep -e eth -e ipw

```
```

lsmod
``` 
and
```

rfkill list all 

``` 
And please paste here thanks

---

### Post by Coachdbeard on 2011-05-20
Sorry about that josephmills, I meant that my b43 issue behaved the same way as what was described here by Ponster.  I was thinking it might be a similar issue with a module or driver not activating on start-up (for his particular model)- which is included in connectivity problems as you said, and would be revealed eventually if it is the problem as info is gathered as you suggested.  I just didn't express that correctly.  Thanks for the help, I know how aggravating it is to not be able to connect.:D

---

### Post by josephmills on 2011-05-20
> **Coachdbeard said:**
> Sorry about that josephmills, I meant that my b43 issue behaved the same way as what was described here by Ponster.  I was thinking it might be a similar issue with a module or driver not activating on start-up (for his particular model)- which is included in connectivity problems as you said, and would be revealed eventually if it is the problem as info is gathered as you suggested.  I just didn't express that correctly.  Thanks for the help, I know how aggravating it is to not be able to connect.:D
Dear couchbeard you did nothing wrong at all, and am glad to see you posting I think that you might be right that it has something to do with the firmware. I also know how aggravating it can be.
ohh and one other thing 
YOU :guitar:

---

