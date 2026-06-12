---
title: "Wep wireless issues on Feisty"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by JHuizingh on 2007-05-10
I installed feisty kubuntu on my laptop last week.  Here's the wireless info:

Hardware:
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

drivers:
ipw2200               148040  0
ieee80211              34760  1 ipw2200


I have been playing around with the wireless for a couple of days trying to get it to work flawlessly, and have had varying success.  I found this page [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")
which talks about setting up wpa_supplicant.  I followed the directions and actually had wep working for a short period of time.  Then I realized that I had 2 eth1 stanzas in my /etc/network/interfaces file and I tried to comment the original one out.  Since then I have not been able to get it to work again.  I'm not exactly sure what was or was not commented it out when it was working.  Here is the eth1 part of my interfaces file:

```
auto eth1
iface eth1 inet dhcp

#auto eth1
iface eth1 inet manual
        wpa-driver wext
        wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf

```

The current state of my wireless is that I can use knetworkmanager to connect to open wireless networks.  It also sees my wep network, opens up the kde wallet and asks for the wep key, but it does not authenticate and connect.

Can somebody point me in the right direction to get this working?

---

### Post by chili555 on 2007-05-10
WEP and WPA are two very different things, like the proverbial apples and oranges. The link you referred us to is for WPA, not WEP. If you are using Network Manager, or it's younger sister Knetworkmanager, your *interfaces* file should work perfectly like this:```
auto eth1
iface eth1 inet dhcp

#auto eth1
#iface eth1 inet manual
#       wpa-driver wext
#        wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
```Leave loopback alone. Reboot. Then go to System -> Administration -> Network and enable Roaming on your wireless interface. Knetworkmanager should now accept your WEP key and connect.

---

### Post by JHuizingh on 2007-05-10
You're right, I'm only trying to get WEP working right now.  WPA is not important for me at this point.

I've followed your instructions as closely as possible.  I couldn't find System -> Administration -> Network.  I'm assuming that those are ubuntu directions which are different because I'm running kubuntu?

The closes thing I could find for configuring the network is K Menu -> System Settings -> Network Settings -> Network Connections.  In this window there is no option to enable roaming on my wireless interface.  Is there a way that I can make a change directly in a config file to enable roaming?

---

### Post by chili555 on 2007-05-10
Oh, kubuntu, or KDE as we used to call it! You are right. Let's try the brute force method. *sudo gedit /etc/network/interfaces* and comment out everything except loopback, thus:```
#auto eth1
#iface eth1 inet dhcp

#auto eth1
#iface eth1 inet manual
#       wpa-driver wext
#        wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
```By the way, these two: *iface eth1 inet dhcp* and *iface eth1 inet manual* seem to be a conflict that would cause your computer to say, "You wanna do what???"

Restart networking *sudo /etc/init.d/networking restart* and let us know if your wireless interface has appeared in knetworkmanager.

---

### Post by JHuizingh on 2007-05-10
Ok, here is the contents of my /etc/network/interfaces file while running these commands.


```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth1
#iface eth1 inet manual
#       wpa-driver wext
#       wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

After setting my file to that, I ran 
```
sudo /etc/init.d/networking stop
```


After that I had some interfaces still running so I brought down all of the interfaces using a combination of 
```
ifdown interface
``` and ```
ifconfig interface down
``` until the output of ifconfig showed nothing.

At this point I also killed knetwork manager.  I ran ```
sudo /etc/init.c/dbus/stop
``` and made sure that NetworkManager and any related processes were not running anymore by doing ```
ps ax|grep etwor
```

Next I started networking:

```
$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                 [ OK ]
jh@jh-laptop:~/code/test_app$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:252244 (246.3 KiB)  TX bytes:252244 (246.3 KiB)

```


Next I started knetwork manager, and it said that NetworkManager was not running.  I fixed that by running ```
sudo /etc/init.d/dbus start
```

At this point, my wireless WEP network appears in the list.  When I select it, it brings up the screen where I enter my wep key.  When I enter the key and click on the button, it starts trying to connect but stalls out on the "Starting IP Configuration" stage.

I am able to connect to an open access point when the computer is configured this way, just not my wep access point.  Would enabling wpa_supplicant make it so knetworkmanager handles something correctly that wasn't being handled correctly without it?  Like I said, I had it working for a brief period of time yesterday.  

Any suggestions?

---

### Post by adibudeen on 2007-05-11
Oddly enough, since the latest kernel update for Feisty, I haven't been able to get WEP working with knetworkmanager.  It works fine if I do it manually, i.e.

```
iwconfig eth1 essid ID_NAME enc WEP_KEY
```
and then
```
dhclient eth1
```

What's even stranger is that I have WPA at work, and it works perfectly.  When I come out of suspend, by the time I get back to the desktop, knetworkmanager has already connected to it automatically.  It used to be that way with my home WEP access point, until the latest update.  So, the workaround for me will be to switch to WPA at home, something I was planning to do anyway, but obviously, this is something that we need to get fixed for people who use WEP.

I figured it was just me, but I thought I'd check the forums just to be sure.

---

### Post by JHuizingh on 2007-05-11
Adibudeen, do you think it would work if went back to an older kernel?  What is the last kernel version that it worked for you on?

---

### Post by adibudeen on 2007-05-11
I suppose there's only one way to find out.  I still have the old kernel installed, so I can try to boot from it when I get home (I'm at work now).

The last working version was: 2.6.20-14

The current running version is 2.6.20-15

It is possible that something was changed with the ipw2100 driver (i.e. I think it to be no coincidence that we both have the same wireless card).

It seems to be a timing issue, though, something I've experienced with the dreaded bcm43xx (broadcom wireless) driver in the past.  NetworkManager attempts to bring up the interface, but the kernel returns the error 

```
eth1: link is not ready
```

It eventually does bring up the device and says:

```
ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
```

but it never is able to finish configuring the device.  It never gets to the "IP address" stage with mine.  Furthermore, if I connect to it manually using iwconfig, knetworkmanager still shows it as disconnected, as though communication with the device is not even occurring.  That has never been the case in the past.  Usually, it will detect the connection, even if it was performed manually.

---

### Post by amarra on 2007-05-11
Hello everybody,
I'm getting crazy with the same error. I've an ASUS W3N laptop with the Intel 2200 wifi chipset and since I've updated my Kubuntu to Feisty I cannot get a wireless connection with my access point (the same laptop and AP work perfectly together in Windows....).
I've noticed that if I use NetworkManager for both wired and wireless connection, I can't obtain an IP address through DHCP. The only network link I've managed to function is a wired one with a static IP address.
When I switch to wireless network through NetworkManager (knetworkmanager) i've seen that the laptop associates with the access point but then it cannot obtain an IP address.
I've also reinstalled Feisty from scratch, but nothing different has happened.
I think this is definitely a serious bug. I've searched this forum, googled around, searched in Launchpad for filed bugs but between several similar situations I cannot found any solution.
Any ideas?
Bye

P.S. dmesg reports "eth1: link is not ready" to me, also!

---

### Post by adibudeen on 2007-05-11
Is your network using a WEP as well?

---

### Post by JHuizingh on 2007-05-11
Ok, I tried using an older kernel 2.6.17-11-generic and the exact same problems were happening.

In knetworkmanager I switched it to offline mode, and then I tried adibudeen's suggestion of

```
iwconfig eth1 essid ID_NAME enc WEP_KEY
dhclient eth1
```

and the connection came up just fine. 

So, the kernel and drivers work correctly and the wireless connection works correctly.  That narrows the issue down to NetworkManager (or knetworkmanager).  

I am going to try and submit a bug.  At least there is a workaround so I can connect to my home network.

---

### Post by JHuizingh on 2007-05-11
I found a bug that seems to address this issue here:  [https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/34505]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/34505")

---

### Post by adibudeen on 2007-05-11
I tried the older kernel version with the same results.

As expected, switching to WPA instead of WEP allowed me to connect with knetworkmanager.

---

### Post by amarra on 2007-05-14
I was using WPA.
I've also tried to connect to a WEP network at work, without success. This time I've found in dmesg output several errors saying 'firmware error'. I've also tried to disable hardware encryption in ipw2200 but nothing has changed...:(

Edit: Firmware files are in place, being those installed directly by Feisty in /lib/firmware/.../ipw2200-*
Ciao

---

### Post by Teleyinex on 2007-05-14
Hi to everyone.

I have the same problem here with Feisty and Gnome. The solution is to do it by hand, as you have commented.

I have opened a BUG, but I don't know why the bug is assigned to Bazar instead of Network-Manager. This is a real BUG and it's confirmed :) by us. So I think that we could get fixed in not so much time.

The bug link: [https://bugs.launchpad.net/bugs/114605](https://bugs.launchpad.net/bugs/114605)

---

### Post by chili555 on 2007-05-14
A Google search of "launchpad ipw2200 WEP' shows a few bug reports which concern the deadly combination of WEP, ipw2200 and Network Manager. One of the work-arounds that seems to have worked for some people is to try to establish a connection from the command line, not Network Manager and use the word 'restricted' in the key, thus:```
sudo iwconfig eth1 essid <your_eesid>
sudo iwconfig eth1 key <your_key> restricted
sudo dhclient eth1
```Also, *iwconfig* seems to like keys with lower case letters, not caps: 097c2efa..etc.

Please let us know if this helps.

---

### Post by amarra on 2007-05-15
Maybe I've found a workaround.
As you can see from my previous posts, I could not use my ipw2200 wireless network on my laptop with NetworkManager (knetworkmanager). But I've tried a new way to solve my problem.
I've downloaded the last version of ipw2200 drivers v1.2.1 from SourceForge ([http://ipw2200.sf.net](http://ipw2200.sf.net)) and their companion modules ieee80211 version 1.2.17 ([http://ieee80211.sf.net)](http://ieee80211.sf.net)). I've compiled and installed them on my laptop (ieee80211 first, then ipw2200) and now it can get IP address from the DHCP server, thus completing the connection to the access point.
I hope that ends my troubles with KNetworkManager, and yours too...:)

Bye
Antonio

---

### Post by JHuizingh on 2007-05-16
Amarra, did your new drivers make it so you can connect within knetworkmanager, or just using the command line?

I have just set up an executable script in my home directory called wireless_connect with the contents

```
#!/bin/bash

iwconfig eth1 essid 2WIRE086 enc your_wep_code_here
dhclient eth1

```

I have an icon in my quick launch panel that runs 'kdesu /home/myuser/wireless_connect'.  I just click that when I start the computer and it connects.  Not ideal, but not too bad.

---

### Post by visctrix on 2007-05-16
I seem to be having something like this problem, but I'm not sure if this solution is a good idea for me... (I'm also still using Edgy on my laptop)

I can connect to a WEP network at home, to a different WEP network at a place I sometimes work at, to a WPA network at my new office, but **not** to the WEP network at the back of this office...

NetworkManager is mainly working ok, so I don't want it to stop working for the other networks. Most of the time when I try to connect it asks me for a WPA key, with no option for WEP. The closest I've come to success is by creating a new network, defining the security as WEP - then it connects for about a second before being disconnected.

Maybe I should start a new thread for this question?

---

### Post by riles32807 on 2007-05-27
I'm using Ubuntu generic not Kubuntu, but I just found that I had set up my Access Point WEP to use key 3.  I guess that multiple keys aren't supported yet or something because as soon as I changed my AP to use key 1 I can connect fine now.

I haven't seen this anywhere else, hope that helps someone.

---

