---
title: "Can't get internet to work"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by dubnium on 2011-06-07
Freshly installed 11.04 with Windows (not wubi). Boots up etc fine but can't at all get internet. Everything is definetly connected and internet works fine on Windows. I'll be happy to provide any additional info needed. Motherboard is an MSI 770-G45 (AM3 socket) just so you know.
Thanks in advance!

---

### Post by frankbooth on 2011-06-07
Open a terminal and write:
```

ifconfig

```
and post the output.

---

### Post by jtarin on 2011-06-08
Describe your connection.Cable,ADSL,Dial-up or Wireless? Router/Modem? What have you tried?

---

### Post by seawolf167 on 2011-06-08
We need more information please:
Do you have internet access when plugging in a physical ethernet cable?
Are you trying access the internet via a wireless connection? If so, you'll probably only need wireless drivers for your device.

---

### Post by astrobob.tk on 2011-06-08
> **dubnium said:**
> Freshly installed 11.04 with Windows (not wubi). Boots up etc fine but can't at all get internet. Everything is definetly connected and internet works fine on Windows. I'll be happy to provide any additional info needed. Motherboard is an MSI 770-G45 (AM3 socket) just so you know.
Thanks in advance!

Welcome to Ubuntu & the forums.

I guess you're talking about a wireless connection right ? If so, the drivers should be installed.
Usually when you do a fresh install, once you login a notification on your desktop notifies of existing hardware drivers. These are usually proprietary ones whose source code is not public; they are provided by the manufacturer.

Anyways, if this is your case; i.e.; wireless, do the following:

1. connect to a wired connection; make sure it works
2. open Main Menu > Administration > Hardware Drivers; you should see inactive driver(s). select the appropriate & click active (it would be helpful if you know what device you have). If you have a graphics card w/ 3D capability you might find another driver for that.

3. test your wireless.

This webpage gives a visual aid to the process (Note that i am not affiliated with the page & hold no responsibility beyond what I mentioned above): [http://www.ghacks.net/2009/04/15/using-proprietary-drivers-in-ubuntu/](http://www.ghacks.net/2009/04/15/using-proprietary-drivers-in-ubuntu/)

P.S.: when your problem is solved, please mark the thread as "Solved" so that others in a similar situation can easily find it.

good luck

---

### Post by dubnium on 2011-06-08
Sorry for the delay. I'm using wired ethernet, to a BT HomeHub 2 ([http://en.wikipedia.orgw/wiki/BT_Home_Hub ]("http://en.wikipedia.org/wiki/BT_Home_Hub")). ifconfig is as follows:
 eth0   Link encap:Ethernet  HWaddr 40:61:86:61:de:b9  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe61:deb9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:703 (703.0 B)  TX bytes:8102 (8.1 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:138112 (138.1 KB)  TX bytes:138112 (138.1 KB)

Hope that helps

---

### Post by astrobob.tk on 2011-06-08
> **dubnium said:**
> Sorry for the delay. I'm using wired ethernet, to a BT HomeHub 2 ([http://en.wikipedia.orgw/wiki/BT_Home_Hub ]("http://en.wikipedia.org/wiki/BT_Home_Hub")). ifconfig is as follows:
 eth0   Link encap:Ethernet  HWaddr 40:61:86:61:de:b9  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe61:deb9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:703 (703.0 B)  TX bytes:8102 (8.1 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:138112 (138.1 KB)  TX bytes:138112 (138.1 KB)

Hope that helps

Nice device, but I do not yet understand what is ur problem exactly.

th ifconfig shows the eth0 (ethernet device) & lo. It does not show the eth1 (for th wireless).

Please state which of the following is the problem: wired connection OR wireless connection ?

---

### Post by dubnium on 2011-06-08
Sorry if this wasn't clear in my last post, it's _**wired**_. I turn it on, it does the animation like it's connecting then nothing. Can't ping anything and no websites work. It works fine in Windows (using that now), so it has to be Ubuntu. It doesn't work in the live CD too.

---

### Post by astrobob.tk on 2011-06-08
> **dubnium said:**
> Sorry if this wasn't clear in my last post, it's _**wired**_. I turn it on, it does the animation like it's connecting then nothing. Can't ping anything and no websites work. It works fine in Windows (using that now), so it has to be Ubuntu. It doesn't work in the live CD too.

Have you tried to connect the ethernet cable directly to your computer (without the BT device) ?

---

### Post by dubnium on 2011-06-08
The BT device is modem and router. My PC doesn't have a port for a modem, only cat5.

---

### Post by OM NOM NOM on 2011-06-08
Looks like your IP address is 192.168.1.1...which might be the same as your router. What's your router's internal IP address?

---

### Post by dubnium on 2011-06-08
EDIT: got wrong thing.
 I think my router's IP is 192.168.1.254 (that's the address for doing the admin for it). I set the address to 192.168.1.1 manually to see if it did anything as DHCP didn't get internet access.

---

### Post by astrobob.tk on 2011-06-08
> **dubnium said:**
> The BT device is modem and router. My PC doesn't have a port for a modem, only cat5.

A cat5 is an ethernet cable: [http://en.wikipedia.org/wiki/Category_5_cable](http://en.wikipedia.org/wiki/Category_5_cable)

Well i guess its your device then; am afraid I can not help in this case.

Maybe someone else can ???

Well, wait a minute; I just searched it a search engine & i got the following:

[http://ubuntuforums.org/showthread.php?t=1518219&page=2](http://ubuntuforums.org/showthread.php?t=1518219&page=2) (check this first)

[http://ubuntuforums.org/showthread.php?t=218936](http://ubuntuforums.org/showthread.php?t=218936)

[http://ubuntuforums.org/showthread.php?t=1057028](http://ubuntuforums.org/showthread.php?t=1057028)

[http://ubuntuforums.org/showthread.php?t=589538](http://ubuntuforums.org/showthread.php?t=589538) (another possible solution ?)

[http://ubuntuforums.org/showthread.php?t=546885&page=2](http://ubuntuforums.org/showthread.php?t=546885&page=2) (also this is solved)

[https://lists.ubuntu.com/archives/ubuntu-uk/2007-June/005303.html](https://lists.ubuntu.com/archives/ubuntu-uk/2007-June/005303.html)

Check them out & if any solves your problem state it in a reply & mark the thread as solved please.

hope it helps

Tip: try searching in a search engine & in the forums for a possible solution before opening a new thread. It'll save both you & others time :P

---

### Post by dubnium on 2011-06-08
Hmm all of those seem to be for wireless problems. I'll try unplugging it and the like but I really can't see why it does this. On an older PC it works fine from live CD (was 10.10). Ubuntu wokrs fine in a virtualbox with the adaptor "bridged", but I guess it still goes through Windows. Ah well I'll see if anyone else can think of anything.
Thanks for all the links though, really appreciate it :)

---

### Post by doas777 on 2011-06-08
I've seen this before on the forums. 

the BTHomeHubs, like most cablemodem devices, needs powercycled whenever it believes a new device has been attached. my best advice is to install a router inline, so that the connection between your router and homehub never changes, regardless of what os boots on the inside of the router. 

to test that this is your issue, boot up in ubuntu, and then unplug your homehub from the wall power, and leave it unplugged for at least 2 minutes. then boot the homehub back up, and reboot straight into ubuntu. it should now work, but rebooting into windows will cause it to fail again.

---

### Post by dubnium on 2011-06-08
I appreciate that that will fix it temporarily but is there a permanent way to fix this? I would still boot into windows regularly for games etc so this doesn't really help. Thanks for the advice however and I'll try it later.
Edit: I have an oldish linksys router. Would having that in that between the PC and bt homehub help?

---

### Post by doas777 on 2011-06-08
> **dubnium said:**
> I appreciate that that will fix it temporarily but is there a permanent way to fix this? I would still boot into windows regularly for games etc so this doesn't really help. Thanks for the advice however and I'll try it later.
Edit: I have an oldish linksys router. Would having that in that between the PC and bt homehub help?
yeah, that would work, but be sure to test first. i may not be correctly diagnosing your issue. I just know that cablemodems don't like having the device they are directly connected to changed, be it hardware (unplugging desktop to plug in laptop) or driver software (rebooting from win to lin and vice versa).

---

### Post by jtarin on 2011-06-08
There have been post in the forum about this hub. There was a firmware update about 26 May that became problematic afterwards for anyone trying to connect with Linux.

---

### Post by dubnium on 2011-06-10
Any suggestions on how to fix it? And how can I link my routers and set it up?
Sorry for being a nub. Also, in the BT HomeHub's menu, it has an entry for the ubuntu connecting to it. Many thanks for any help ;)

---

### Post by comput99 on 2011-06-10
is tht a good change?

---

### Post by jtarin on 2011-06-10
The only advice I can offer is to search the forums using the term "BT HomeHub" and see if someone finally found a solution. This a non-Ubuntu issue as BT chose to update there firmware. A fix is probably in the works or has been found. Just search is all I can provide.

---

### Post by astrobob.tk on 2011-06-11
> **dubnium said:**
> Any suggestions on how to fix it? And how can I link my routers and set it up?
Sorry for being a nub. Also, in the BT HomeHub's menu, it has an entry for the ubuntu connecting to it. Many thanks for any help ;)

Did you check the posts I linked above ? I think i read that they were able to fix it. I guess i also read that it was due to some firmware upgrade.

---

### Post by Swagman on 2011-06-11
This is the official BT Forums thread

[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473)

There are various fixes starting from page 9

Join the BT forum and add your displeasure to the thread.

---

