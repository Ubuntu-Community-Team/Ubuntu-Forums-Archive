---
title: "Problem with D-link router"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by ep3w on 2007-05-17
I have a dell M65 and i am having trouble connection to my home wireless network.  I have my wireless drivers installed correctly as when I was at school my wireless worked fine.  When i got home I could not get it to connect.  There is no security on it as far as i know.  I tell it to connect to it and the little picture shoes it connecting then it just goes to the two computers with orange triangle.  I think it is a problem with the router.  It is a D-link DI-524.  I can connect to wireless with XP no problem.  It is also a dynamic IP. Here is my iwconfig:

ryan@ryan-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11g  ESSID:"maas"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:39:20:49   
          Bit Rate=36 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off 
          Link Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by gradedcheese on 2007-05-17
```


eth1 IEEE 802.11g ESSID:"maas"
Mode:Managed Frequency:2.437 GHz Access Point: 00:11:95:39:20:49 

```

That means you are connected (associated), and the ESSID is 'maas' (is that what the router's SSID is?) and it's MAC address is 00:11:95:39:20:49

Now that you are associated, you need to get an IP address.  What does:

```

ifconfig eth1

```

show?

---

### Post by ep3w on 2007-05-17
here is the output:

ryan@ryan-laptop:~$ ifconfig eth1 
eth1      Link encap:Ethernet  HWaddr 00:16:CE:6C:64:4D  
          inet6 addr: fe80::216:ceff:fe6c:644d/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:2638 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:872672 (852.2 KiB)  TX bytes:1872 (1.8 KiB) 
          Interrupt:17 Memory:dcffc000-dd000000

and yea that is the correct network

---

### Post by gradedcheese on 2007-05-17
ok, lets ask for an IP address:

```

sudo dhclient eth1

```

---

### Post by ep3w on 2007-05-17
I did it and my internet worked! The icon on the task bar still didn't so i clicked it and told it to connect to my network and it did the same thing as before and stopped working.  So i did the code again and it works again.  I can live without the task bar icon.  Any easy way of getting it to work again though?  Thanks a lot for the help! Will i just need to put that could in everytime i restart?

---

### Post by gradedcheese on 2007-05-18
Alright, so NetworkManager (the icon in the panel) seems to associate but can't do DHCP, but manually getting a DHCP lease works.  When you click the icon, NetworkManager will try to do its thing again.  I would, if you have time, go to [https://launchpad.net/](https://launchpad.net/) and file a bug in the right place about this: tell them exactly what WiFi chipset you have and explain the problem.  It's probably something easy to fix.

As for fixing it, you'll either need NetworkManager to start working, or you can get rid of it and do things the old (well, relatively speaking) way.  Click the NetworkManager icon and select "manual network configuration" from the menu and then set up your wireless interface there.  If that doesn't help, then we can just disable NetworkManager and set things up the way they were done before Ubuntu started shipping with it, but it's a nice tool so I'd rather have it work for you.

---

### Post by ep3w on 2007-05-18
thanks a lot for all the help!  I will file a bug as soon as i get a chance...

---

### Post by gradedcheese on 2007-05-18
To let them know what chipset you have,

```

lspci

```

Look for the line starting with "Network controller:" or "Ethernet controller:"

---

### Post by ep3w on 2007-05-18
thanks again...this is on e of the reasons i picked ubuntu. helpful people on the forums! :)

---

### Post by struess on 2007-05-19
i've been struggling with that same problem all day long.  thanks so much for the help :)

---

