---
title: "[SOLVED] Lost wireless connection"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by Scunnered on 2008-11-14
I was looking at an article on how to speed up 8.10 and tried some of the suggestions with adverse results.

I had hoped to automatically logon and in changing settings seem to have done something wrong as I have totally lost my connection. No matter what I try I am unable to make any connection to the wireless setup.  When I initially set things up not only could I see my setup but 3 others locally. Now there is nothing on view.

I have been asked for a password and providing it does not do any good.

Can anyone offer guidance.

PS When will I ever learn to believe if it aint broke then dont fix it !

---

### Post by Zhukov on 2008-11-14
Dont worry, we all try to hack the system, no matter how good it is :D

Now, do you still have the interface listed in iwconfig?

Best regards!

---

### Post by Scunnered on 2008-11-14
Zhukov 

Many thanks for your reply.  This is where I show my complete ignorance as I have only just come over to Ubuntu from XP.  I only started working with a wireless connection days ago and hit this problem.

I have yet to look further into the OS.  If you could guide me to where I may find the information you require I will look for it and report back.

Sorry to put you to the extra work

---

### Post by superprash2003 on 2008-11-14
post output of the following commands from the terminal
1)lshw -C network
2)iwconfig

---

### Post by Scunnered on 2008-11-14
Superprash

Many thanks for your guide.  This is what was produced when I ran the 2 items

ian@ubuntu:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Wireless interface 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: wmaster0 
       version: 01 
       serial: 00:15:af:e6:9f:98 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg 
  *-network 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 7 
       bus info: pci@0000:01:07.0 
       logical name: eth0 
       version: 10 
       serial: 00:22:15:5e:5c:e3 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 4e:92:f8:a2:c7:82 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 


ian@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 

Was totally unsure about run as super-user so if this is significant please say so and I will go around again.

Trust this assists

---

### Post by superprash2003 on 2008-11-15
hope this helps [http://ubuntuforums.org/showthread.php?t=766169&page=2](http://ubuntuforums.org/showthread.php?t=766169&page=2)

---

### Post by superprash2003 on 2008-11-15
also check system->admin->hardware drivers , to see if there are any drivers that can be used..

---

### Post by Scunnered on 2008-11-15
superprash

Thanks again.

Had a look at the link provided but it only confused me totally. My reading of it was that it referred to an earlier **how to** which I could not find.

I have a further problem which is a complete pain so I am seriously thinking of totally starting from the begining and doing a fresh install.

I will speak to my supplier to seek their reaction before I totally foul matters up.

Hope this will resolve matters and will get back to everyone later to advise how matters worked out.

---

### Post by Zhukov on 2008-11-16
Well, we can try to put the system back on tracks but if you can reinstall the system, IMHO, i would do it...

---

### Post by Scunnered on 2008-11-17
My thanks to everyone on this problem.  I have re-installed and have now been reconnected with the world.

I will take greater care with this installation and see about a complete system backup once I have restored things to where I was before the mess

---

