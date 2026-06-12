---
title: "Which USB wireless works 'out of the box'?"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by Jackie999 on 2008-08-29
I'm starting a USB wireless connection and still end up running a cat5 across the floor to connect :)
I have the Alfa AWUS036H which works BUT is very erratic ..dropping connection frequently.
I have the Belkin USB (rt2870) which I have tried, quite a few times, to get working.  The driver appears okay  (rt2870sta) but iwconfig doesn't show a device so I assume I've done something wrong...
Is there a USB I can buy that is proven to work 'out of the box' on hardy?
I can't use ndiswrapper..I have been using it but hourly freezes on my lappy render it useless..hence the cat5 backup. But I'm game to add to my USB collection if anyone has a suggestion.
Thanks

---

### Post by Crafty Kisses on 2008-08-30
Post the results of this output when the devices are plugged in > lsusb

---

### Post by chronographer on 2008-08-30
my belkin works ok (its a rt73, fsd7050 'b') I head d-link is ok, jsut get something with a recogniseable name, high volume, as that way its most likely that someone will be working on drivers, if its not already supported.

---

### Post by Jackie999 on 2008-08-30
Thanks chronographer, I'll see if there are any of the fsd 7050 around. I bought the belkin F5D8053 v3 because it was 'n' version and figured it would be of more use, I didn't realize you need to use older devices to maintain linux support. Actually it does work with ndiswrapper. I ran Gutsy for awhile since it seemed stable..only one freeze a day..but the recent updates made that worse. So I upgraded to Hardy hoping the issues had been fixed but freezes every few minutes with it.

Codename, here is the output of the lsusb with the Alfa AWUS036H plugged in. I have googled and found this same problem with others, that the native linux drivers cause it to drop connection. As I watch the WICD I can see it fluctuating between 0% and 95%..changing contantly
```
jackie@ubuntu:~$ lsusb
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. 
```Here is the lsusb with the Belkin F5D8053 v3 (chip is rt2870) and I've tried installing using 2008_0718_RT2870_Linux_STA_v1.3.1.0 but it doesn't show in iwconfig so I'm missing something and dont' know enough to fix it
```
jackie@ubuntu:~$ lsusb
Bus 001 Device 003: ID 050d:815c Belkin Components 

```I wonder if the ndiswrapper, even though I've removed it is causing me problems. I'd do a format and reinstall if you think that would help.

---

### Post by rashwan on 2008-08-30
Jackie999 , i have AWUS036H and the same problem also
before i used to use D-Link DWL-G510 (RT61) it works well out of the box

---

### Post by Tom--d on 2008-08-30
> **Jackie999 said:**
> 
Codename, here is the output of the lsusb with the Alfa AWUS036H plugged in. I have googled and found this same problem with others, that the native linux drivers cause it to drop connection. As I watch the WICD I can see it fluctuating between 0% and 95%..changing contantly
```
jackie@ubuntu:~$ lsusb
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. 
```

Easy to fix!
Install ndisgtk
```
sudo apt-get install ndisgtk
``` (It installs ndiswrapper with it, saves me typing it out :p)

and go, 
System > Admin > Windows Wireless Drivers

Download these drivers here [http://download2us.softpedia.com/dl/b544e03738f8ace418480c8d5351950a/48b1ee59/800025580/drivers/network/win_8187B_6.1063_RtlWlan_402.zip](http://download2us.softpedia.com/dl/b544e03738f8ace418480c8d5351950a/48b1ee59/800025580/drivers/network/win_8187B_6.1063_RtlWlan_402.zip)

And find the **Windows 98** driver!
And install it through Windows Wireless Drivers. ([b]MAKE sure you have the .inf and .sys file in there
And MAKE sure they are the Windows 98!![/b]

---

### Post by Jackie999 on 2008-08-30
Unfortunately Tom--d, I'm unable to run ndiswrapper..well I can run it..but lappy freezes pretty much constantly. I have to remove battery and unplug to get it going again so thats really not an option for me..but thanks for trying :)

---

