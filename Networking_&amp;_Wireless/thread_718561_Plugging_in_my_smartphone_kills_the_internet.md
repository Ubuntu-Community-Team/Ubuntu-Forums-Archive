---
title: "Plugging in my smartphone kills the internet"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by surfdoc on 2008-03-08
I've recently configured synce to connect to my HTC WM6 smartphone. When I plug the phone in, i loose my internet connection on the computer. I think that the phone is being setup as the default connection for the internet.

The output of route -n before and after pluging in is

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 ath0

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         169.254.2.1     0.0.0.0         UG    0      0        0 eth1

So the default gateway has been changed. If I add back the old route to give ...

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ath0
0.0.0.0         169.254.2.1     0.0.0.0         UG    0      0        0 eth1

... I still don't have internet.

Any help appreciated!

---

### Post by tact on 2008-03-08
Are you running a default installation of ubuntu (or kubuntu, etc..?  Which one?).   What version?

When you say you lose internet - what internet?  Is it a wifi connection that gets dropped?  More info please.

The reason I ask is that recent versions of ubuntu have networkmanager setup by default to manage multiple network adapters and it is setup to automatically choose the fastest connection if more than one are available.   

Not sure of the logic in networkmanager's decision as to which is the faster network adapter but I have observed on a friend's rig that when he plugs in his smartphone:
- networkmanager detects his phone as an available "wired" adapter (it can be seen in the nm-applet on the top panel)
- for whatever reason networkmanager thinks the phone's 3G data link is faster than the wifi connection and changes over to the phone, dropping the wifi.  (just doing its job).

If this is whats happening to your system then try taking the phone's network adapter out from the control of networkmanager by turning off "roaming mode" in System>Prefs>Network

Hope that helps.

---

### Post by surfdoc on 2008-04-07
Whoops - didn't have email notification on - didn't know i'd had a reply!

I'm running kubuntu gutsy 7.10

My internet connection is through wifi (ath0 on my system). When i plug my mobile in, it creates eth1 and seems to set it as the default. Since i'm plugging the phone in to transfer files, i don't really want it to be used as a modem (although i might look at that later). Anyway, it shouldn't take preference over a wifi connection like you say.

I've configured my wifi manually (/etc/network/interfaces) because the network manager just didn't work. I don't think its running - although i can't be 100% sure its not lurking in the background!

In the system config gui i have ath0 set as the default gateway, but this doesn't seem to stop it from being changed. I presume the roaming option is in network manager (which i don't have running). 

My usual fix is to run /etc/init.d/networking restart.

Regards

---

### Post by yoshimira80 on 2008-04-07
i'm a total noobie and haven't yet figured out how to connect my HTC Excalibur (WM6) to my system running Gutsy Gibbon 7.10...
i'm amazed!! how did u do that?

---

### Post by surfdoc on 2008-04-13
Ah well.....

There's two ways to do it:

1) Install software on ubuntu 

synce seems to be the program to use - however it ain't easy as you have to compile the program and update the kernel. I've got my system to recognize the device and create a network interface - but I haven't actually been able to do anything further.

2) Install software on the phone

There are programs that can turn your phone in to a mass storage device. wm5torage (note no 's') is the only free one i could find, and i couldn't get it to work on my o2 xda orbit 2. In the end I decided to buy a commercial program by softick called cardexport. You can try it for free first and it only costs about £8.

Hope this helps

---

