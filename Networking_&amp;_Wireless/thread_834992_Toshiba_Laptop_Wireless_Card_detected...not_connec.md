---
title: "Toshiba Laptop Wireless Card detected...not connecting!"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by logreeval on 2008-06-20
I have a toshiba portege 4010 laptop that has a built in wireless card...

It detects the card, the card sees networks, but when i try to connect it just can't....the signal says 0/92...

Does someone know what I can do to get internet working?

Thanks!!

---

### Post by superprash2003 on 2008-06-20
go to the terminal and type iwconfig and post output..similarly post ifconfig output

---

### Post by logreeval on 2008-06-20
Thank you for the reply! :)

Here it is...

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0




ANd...

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:5a:0e:d2  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe5a:ed2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:776580 (758.3 KB)  TX bytes:104380 (101.9 KB)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:69:3c:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1892 (1.8 KB)  TX bytes:1892 (1.8 KB)


Thanks for the help!

---

### Post by logreeval on 2008-06-20
Well i took it to my other house and now the internet works....weird...

The only difference is the other house has WEP...

Here are the posts with working internet....

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"LRV"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:7E:6C:21:30   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=74/92  Signal level=-15 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:2
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0


and..

eth0      Link encap:Ethernet  HWaddr 00:00:39:5a:0e:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3761380 (3.5 MB)  TX bytes:259362 (253.2 KB)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:69:3c:52  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:2dff:fe69:3c52/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4401 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7856239 (7.4 MB)  TX bytes:672693 (656.9 KB)
          Interrupt:11 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1900 (1.8 KB)  TX bytes:1900 (1.8 KB)

So thats great....atleast i know the internet does infact work....

Maybe a WEP issue with the wireless driver??

For now its fine though...

I only have one other question, I can only 800x600 resolution, but it is so small, i need the 1024x768, do you know how to make that possible?

Thanks for the help!!

---

### Post by lisati on 2008-06-20
I, too, have a Toshiba laptop, but a different model. Just one question: do you have "Roaming mode" enabled for your wirelss connection?

---

### Post by logreeval on 2008-06-21
lisati, yes i do.. all i know for sure is open networks work, not password encrypted ones...

And for the screen resolution, this helped MUCHO!:

> **atomkarinca said:**
> If you did a fresh Xubuntu install then you might not have the "Screen and Graphics Preferences" application. Open up a terminal (Applications > Accessories > Terminal) and type:

```
sudo apt-get install displayconfig-gtk
```

then run the application with admin privilages:

```
gksudo displayconfig-gtk
```

and configure your monitor and resolution settings. If you have nVidia card the next thing you should do is install nvidia-settings

```
sudo apt-get install nvidia-settings
```

and run it again with admin privilages:

```
gksudo nvidia-settings
```

configure your settings and hit "Save to X Configuration File". Restart the system and you should be ok.

---

### Post by logreeval on 2008-07-10
I am still trying to get it to work, but was on vacation.

All i know is that the orinoco driver is being used, and it works on open wireless connections...

Thanks

---

### Post by logreeval on 2008-07-13
Anyone know any possible way to fix this?

Thanks

---

