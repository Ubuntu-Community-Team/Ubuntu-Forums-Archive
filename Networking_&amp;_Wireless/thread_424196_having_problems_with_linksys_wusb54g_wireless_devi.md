---
title: "having problems with linksys wusb54g wireless device in Feisty?"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by wickstopher on 2007-04-26
I was too.  An annoying thing about this device (and it happens in Windows, too), is that it intermittently cuts out....might happen once in a day, or it might happen several times in an hour.  The solution in Edgy (and in Windows), for myself, at least, was just to unplug the USB cable and plug it back in.  But for some reason, whenever I tried that in Feisty, it would lock up the Network Manager and pretty much everything else (couldn't even restart the system) and I would have to turn off my computer's power supply and boot back up.  I have found, however, that if this happens, simply go to System > Administration > Network and disable the wireless connection, then re-enable it, and you should be back in business.  I'd be interested to know if anyone else has had similar problems with this device and if they have any comments on the situation.  Hope this helps if anyone else has been as frustrated as I was with this...I was on the verge of reinstalling Edgy, even though everything else about Feisty for me thus far has been fantastic.  Once again, I'd be interested in hearing any comments/stories/alternative solutions on this topic.  Thanks!

---

### Post by Floppyjoe on 2007-04-26
There are several different versions of this device. Do you know what your version is?  The One I have is a WUSB54G v4. I have not noticed any problems like that with this device. I am using Ndiswrapper with the Windows driver.

---

### Post by wickstopher on 2007-04-26
I never had to use NDISwrapper with my device....it worked fine (aside from the problem mentioned) in both Edgy and Feisty without it.  I did actually install NDISwrapper and the windows driver and use it with the device in Edgy (just to see if it would make any difference), and it worked exactly the same as it did without it, problem and all.  It also worked with Feisty right out of the box...and in fact, I've experienced a noticeable boost in internet speed (particularly in Firefox) since upgrading to Feisty.  How would I find out what version of the device I own?

---

### Post by Floppyjoe on 2007-04-26
On mine it has the version on the bottom of the device.

---

### Post by wickstopher on 2007-04-26
Weird.  Mine doesn't!

---

### Post by Floppyjoe on 2007-04-27
You could do a:
```
lsusb
```
and search the internet for the Id that the lsusb brings up to find your version number.

---

### Post by wickstopher on 2007-04-27
cool.  well, mine would appear to be a version 4 as well.  perhaps it's just slightly broken.  i seem to remember (faint, distant memory from when i was first starting my linux/ubuntu journey) someone else having the problem of it cutting out and recommending the whole unplug-replug solution.  but i'm not sure.  like i said, it's a faint memory.

---

### Post by andwpoh on 2007-05-02
> **wickstopher said:**
> I was too.  An annoying thing about this device (and it happens in Windows, too), is that it intermittently cuts out....might happen once in a day, or it might happen several times in an hour.  The solution in Edgy (and in Windows), for myself, at least, was just to unplug the USB cable and plug it back in.  But for some reason, whenever I tried that in Feisty, it would lock up the Network Manager and pretty much everything else (couldn't even restart the system) and I would have to turn off my computer's power supply and boot back up.  I have found, however, that if this happens, simply go to System > Administration > Network and disable the wireless connection, then re-enable it, and you should be back in business.  I'd be interested to know if anyone else has had similar problems with this device and if they have any comments on the situation.  Hope this helps if anyone else has been as frustrated as I was with this...I was on the verge of reinstalling Edgy, even though everything else about Feisty for me thus far has been fantastic.  Once again, I'd be interested in hearing any comments/stories/alternative solutions on this topic.  Thanks!

am having almost the same problem wireless router wrt64g v7, not able to browse the net eventhought the wifi is connected. Have to shut off and restard the router. I hve tried similar router borrowed from friend and it do not face the problem. Used a second modem router no problem, and also proling modemrouter . Its a problem  to switch on and off all the time especially when you left it idle for some time. It there something wrong with the wifi router?

---

### Post by vronp on 2007-05-08
wickstopher,

My WUSB54G does not cut out, but my system does lockup when I remove it and plug it back in, just like your setup.

I like Feisty as well but the overall situation with wireless networking seems to be somewhat grim.

> **wickstopher said:**
> I was too.  An annoying thing about this device (and it happens in Windows, too), is that it intermittently cuts out....might happen once in a day, or it might happen several times in an hour.  The solution in Edgy (and in Windows), for myself, at least, was just to unplug the USB cable and plug it back in.  But for some reason, whenever I tried that in Feisty, it would lock up the Network Manager and pretty much everything else (couldn't even restart the system) and I would have to turn off my computer's power supply and boot back up.  I have found, however, that if this happens, simply go to System > Administration > Network and disable the wireless connection, then re-enable it, and you should be back in business.  I'd be interested to know if anyone else has had similar problems with this device and if they have any comments on the situation.  Hope this helps if anyone else has been as frustrated as I was with this...I was on the verge of reinstalling Edgy, even though everything else about Feisty for me thus far has been fantastic.  Once again, I'd be interested in hearing any comments/stories/alternative solutions on this topic.  Thanks!

---

### Post by clemkonan on 2007-05-11
I too have experienced the cutting in and out problem and I am at maximum 50 feet away from the access point .

I was hoping however you could explain how you got this stick to work with Feisty without using ndiswrapper, etc. Network manager find my SSID tells me its got 7-% connectivity but thats all. I cannot connect.

Thanks clemkonan

---

### Post by gkinal on 2007-05-15
From all of the threads/posts, it definitely seems that there is a serious problem in using the WUSB54G with Feisty, with or withut NDISwrapper.

What seems to work best for me (so far, not done yet) is to avoid plugging in the USB cable until after the boot/login process has been completed. 

If the WUSB54G is left plugged in during the boot process, it is recognized by the network manager but there is no successful wifi connection.

Is there a way of delaying the Linksys' start-up to a later stage in the startup sequence ?

GK

---

### Post by introspectif on 2007-05-23
I'm facing the same problem too i.e. I get disconnected every random few minutes. 

Perhaps similar in effect to (unplug+plug)ging the device is to issue a 

```
sudo /etc/init.d/networking restart
```

That's what I've been doing to get my connection back, and it has been consistently successful. 

It's still every annoying to have to do it every now and then, of course. :(

---

### Post by introspectif on 2007-05-28
*bump*

Anyone found a workaround for this? I've been so desperate, I turned to setting up a cron job to run this command every 5 minutes or so, just so my bittorrent downloads can continue. How dump :(

---

### Post by NfF on 2007-06-13
I also have the same problems as clemkonan, but the wireless internet access point is less than 2 metres away from the adapter! The signals show above 50%, but my adapter cant connect to the wireless internet point no matter how near it is.
 I didnt install ndiswrapper(cuz i dont know how), and my adapter, i just plug and play.

---

### Post by cwood06 on 2007-07-10
iv been having the same problems it never happend in edgy, in fiesty the network gadget says it goes idle so i change it to a diffrent ipassignment ex. changing it to zeroconf then back to dhcp works for me then it works for acouple more hours

---

### Post by be4truth on 2007-07-11
I connected a Linksys WUSB54G Ver.4 to my xeron laptop and installed Ubuntu Mint. After the installation it worked out of the box. Haven't checked with encryption but otherwise works fine.

---

