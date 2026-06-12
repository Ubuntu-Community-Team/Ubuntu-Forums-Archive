---
title: "Ralink RT3060: Ndiswrapper/Wireless connection nightmare"
date: 2014-10-26
forum: Networking &amp; Wireless
---

### Post by godzillathecing92 on 2014-10-26
Alright, I know you probably get a lot of these, but bare with me here - I've probably read them all.

I installed Ubuntu yesterday, hoping to get rid of Windows' many blisses, to be unfortunately encountered with an issue - I can't connect to the internet. It showed a list of networks, and I saw mine there, but when I tried to connect it just disconnected me. I assumed it's a driver-related issue, so I went online on my laptop in pursuit of an answer (my driver is Edimax EW 7711 In). What I found out is that using a tool called "ndiswrapper" I can install the drivers provided by my driver's manufacturer. Only problem is, all solutions I saw involved using some Synaptic package manager, which I simply don't have on my Ubuntu.

 How the hell do I install ndiswrapper without it? Is there a way for a complete (and quite stupid) newb and noob to install the drivers?

Thanks in advance.

---

### Post by Bucky Ball on 2014-10-26
Welcome. You don't install ndiswrapper. You avoid it at all costs. It is largely superceded. How old was the link you got that info from?

You're card was working fine, seeing networks, just disconnecting, so a fix is probably not that far away. Glad we got here before you worked out how to install ndiswrapper!

Please open a terminal and paste this in:

```
sudo lshw -C network
```

... and post the output back here (between ```
 tags; see the last link in my signature for how). This will give us a start. I presume you can still see networks but you are getting disconnected? 

Do you know the IP address of your router? Can you ping it?

[code]ping 192.***.***.***
```

... where 192.***.***.*** is the IP of your router.

If you get a ping, try:

```
ping google
```

---

### Post by godzillathecing92 on 2014-10-26
Heh, I wish I knew that yesterday Bucky! Still, good to hear that this is even solveable :p

I did what you asked and for the sudo I got:

```
 
PCI (sysfs)  
  *-network 
description: Ethernet interface
 
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor Co., Ltd.  
physical id: 0 
bus info: pci@0000:04:00.0   
logical name: eth0 
version: 06    
serial: 50:e5:49:50:04:40    
size: 10Mbit/s
capacity: 1Gbit/s   
width: 64 bits   
clock: 33MHz     
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s  
resources: irq:42 ioport:ee00(size=256) memory:fbeff000-fbefffff memory:fbef8000-fbefbfff
  *-network    
description: Wireless interface  
product: RT3060 Wireless 802.11n 1T/1R  
vendor: Ralink corp.  
physical id: 0    
bus info: pci@0000:06:00.0     
logical name: wlan0     
version: 00      
serial: 00:1f:1f:b8:da:52     
width: 32 bits     
clock: 33MHz      
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt2800pci driverversion=3.13.0-32-generic firmware=0.34 latency=32 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn   
resources: irq:19 memory:fbdf0000-fbdfffff


```

I also tried pinging my IP, it said the network is unreachable.

---

### Post by Bucky Ball on 2014-10-26
From my investigations that is how it should be looking, right driver for that wireless card, so don't think the problem lies with the driver. Can you go to the network manager and delete your wireless profile in there, please? Reboot the machine and wait for the 'wireless networks available' (if you get this then your card is working fine). Choose your network and post back what happens next. Still disconnecting after you put in your details?

Are you using static IP for you local machine or the router is serving you an IP address?

* Actually, just digging around a bit more and not sure that is the correct driver for that card. You may be able to dig something up with a search for 'RT3060 ubuntu 12.04' as there doesn't seem to be much around for that card and 14.04, which is a good sign in one way. ;)

Just a couple of things: The router set to channel one might give better results and if you have an ethernet cable plugged in that will take precedence over the wireless. They will not work at the same time. Therefore, to check the wireless, you need to pull the ethernet cable out.

---

### Post by godzillathecing92 on 2014-10-26
Well, I went to Network Connections and deleted my network's name from under the Wireless list, rebooted my computer and got the same results: networks are available, but whenever I try to connect it just sorta tries to "load" them for a while and then disconnects.

>  Are you using static IP for you local machine or the router is serving you an IP address? 

I think I'm using static, not entirely sure though (how do I check? :P)

>  Just a couple of things: The router set to channel one might give better  results and if you have an ethernet cable plugged in that will take  precedence over the wireless. They will not work at the same time.  Therefore, to check the wireless, you need to pull the ethernet cable  out. 

Err, to be completely honest I don't really work with routers and wifi much, so I'm gonna need some help here >.< (yeah I know it must be pretty basic, but I'm also pretty stupid)

---

### Post by Rob Sayer on 2014-10-26
Here's a link on ubuntu 12.04 and the Ralink RT3060:

[http://askubuntu.com/questions/199273/ralink-rt3060-wireless-device-configuration-on-ubuntu-12-04](http://askubuntu.com/questions/199273/ralink-rt3060-wireless-device-configuration-on-ubuntu-12-04)

---

### Post by godzillathecing92 on 2014-10-26
> **Rob Sayer said:**
> Here's a link on ubuntu 12.04 and the Ralink RT3060:

[http://askubuntu.com/questions/199273/ralink-rt3060-wireless-device-configuration-on-ubuntu-12-04](http://askubuntu.com/questions/199273/ralink-rt3060-wireless-device-configuration-on-ubuntu-12-04)

Thanks, I tried that but for some reason at step 6 it gives me this error:

```

Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package build
E: Unable to locate package essential

```

Do you (or anyone) happened to know why this is happening and/or how to fix it?

Also, on a slightly unrelated note: I know there are some Ubuntu based OSes floating around out there, does anyone know if there's possibly 1 that somehow for some reason works with my card out of the box?

---

### Post by Bucky Ball on 2014-10-26
The first step in step 6 is:

```
sudo apt-get update && sudo apt-get install build-essential linux-headers-generic
```

You are doing it? That should prevent the error you're getting (it installs build-essential). 

Make sure you are following the instructions exactly (copy and paste best).

---

### Post by godzillathecing92 on 2014-10-27
> **Bucky Ball said:**
> The first step in step 6 is:

```
sudo apt-get update && sudo apt-get install build-essential linux-headers-generic
```

You are doing it? That should prevent the error you're getting (it installs build-essential). 

Make sure you are following the instructions exactly (copy and paste best).

Well, I tried going through the thing again and this time when I got to the build-essential part it gave me this:

```

Err http://gb.archive.ubuntu.com trusty InRelease
  
Err http://gb.archive.ubuntu.com trusty-updates InRelease
  
Err http://gb.archive.ubuntu.com trusty-backports InRelease             
  
Err http://security.ubuntu.com trusty-security InRelease                
  
Err http://extras.ubuntu.com trusty InRelease                           
  
Err http://gb.archive.ubuntu.com trusty Release.gpg                     
  Could not resolve 'gb.archive.ubuntu.com'
Err http://gb.archive.ubuntu.com trusty-updates Release.gpg
  Could not resolve 'gb.archive.ubuntu.com'
Err http://gb.archive.ubuntu.com trusty-backports Release.gpg
  Could not resolve 'gb.archive.ubuntu.com'
Err http://security.ubuntu.com trusty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://extras.ubuntu.com trusty Release.gpg
  Could not resolve 'extras.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'gb.archive.ubuntu.com'

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Could not resolve 'gb.archive.ubuntu.com'

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Could not resolve 'gb.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'extras.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essential


``` 

If I got the code right I'm not very surprised it can't download build-essential, I don't have any internet access on my Ubuntu lol..

Also, a late answer to the question you asked a couple of posts ago: my IP is dynamic and my ethernet cable is disconnected.

---

### Post by Bucky Ball on 2014-10-27
You need to be online with a cable for this to work ...

---

### Post by slickymaster on 2014-10-27
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by godzillathecing92 on 2014-10-27
> **Bucky Ball said:**
> You need to be online with a cable for this to work ...

I don't know if that's an option for me... I'll check, but still - Is there a way to do it offline? :sad:

---

