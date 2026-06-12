---
title: "wireless disconnects and weird messages in dmesg"
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by Houman on 2005-11-30
Hi there,
I have a breezy on a centrino laptop (Dell Inspiron 6000) and I am using a wireless network. However the wireless gets disconnected every 10 minutes and reconnects again. This is very annoying for people on my msn list :???: otherwise it really wouldnt matter if i drop connection once in a while.

Also usually when the connection drops/comes back, i get some strange stuff in dmesg:

```

[4296163.625000] Inbound IN=eth1 OUT= 
MAC=00:12:f0:51:55:75:00:11:95:38:7e:ad:08:00 SRC=68.121.19.81
 DST=192.168.0.102 LEN=48 TOS=0x00 PREC=0x00 TTL=108 ID=58036 DF
 PROTO=TCP SPT=61292 DPT=49213 WINDOW=64512 RES=0x00 SYN URGP=0

```

And lots of that (that was just a snippet) in fact sometimes dmesg is just that, its filled with these messages;

anywyas here is dmesg | grep ipw ( i used what came with breezy)
```

[4294695.506000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 
1.0.6[4294695.506000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294695.510000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connecti

```

and here is my iwconfig

```

eth1      IEEE 802.11g  ESSID:"xuxu"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:38:7E:AD 
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-16 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1


```

I should also note that i tried what was suggested in another thread regarding  ipw2200 driver problems [http://ubuntuforums.org/showthread.php?t=75612]("http://ubuntuforums.org/showthread.php?t=75612") which was basically to add the hwcrypto=0 option to the ipw2200 module.

thank you in advance ;

Houman

---

### Post by Houman on 2005-12-04
hi there;
I fixed the problem by compiling the ipw2200 driver from source which is what i didnt want to do

anyways the strange thig is this happened to me before, in hoary i compiled the ipw 1.06 drivers and that fixed everything, but breezy actually shipped with ipw2200 version 1.0.6 so i assumed everything will go fine,
anywyas now i have the 1.0.8 version of the ipw driver and i dont loose conection and i have no more of those weird messages, although i have one strange line in dmesg:
```
[4294843.401000] ipw2200: Unknown notification: subtype=40,flags=0xa0,size=40
```

but eh, it works and im happy ,just wish i wouldnt have to compile stuff from source and scatter binary files across my filesystem without having any way of keeping track of them; 

regards;
Houman

---

### Post by Houman on 2005-12-06
it looks like im the only one posting to this thread :p

anywyas, unfortunately things are back to the way they were :( the old weird messages are coming back and msn barely works;

i dont know what happened :( this means i guess that 1.0.8 isnt the solution to the disconnects that people have been having on the ipw2200 drivers, 

im just gonna start using my wired net :(

regards;

---

### Post by ranf on 2005-12-06
[QUOTE=Houman]
Also usually when the connection drops/comes back, i get some strange stuff in dmesg:

```

[4296163.625000] Inbound IN=eth1 OUT= 
MAC=00:12:f0:51:55:75:00:11:95:38:7e:ad:08:00 SRC=68.121.19.81
 DST=192.168.0.102 LEN=48 TOS=0x00 PREC=0x00 TTL=108 ID=58036 DF
 PROTO=TCP SPT=61292 DPT=49213 WINDOW=64512 RES=0x00 SYN URGP=0

```[/QUOTE]
Do you have Firestarter installed?

Run it from the menu and stop the firewall and see if that helps.

---

### Post by jafenske on 2005-12-06
I had this problem!  It turned out to be my dlink 624 router.  It turned out the router was known to over heat if layed down.  As soon as I stood it up vertically, I haven't had a problem.

---

### Post by Houman on 2005-12-07
WOW;

I have the exact same router D-Link DI-624, and IT IS lying down;:???: 

How in the world did you narrow down the problem to the router? If it was me i would have never been able to figure this out;

and thanks for letting me know :)

regards

---

### Post by jafenske on 2005-12-07
Let me know it that works for you... I work in a R&D lab... Everything is suspect.

---

### Post by Houman on 2005-12-08
jafenske;

teh damn router is standing up and the windows are open (its -20 C outside) and still the same story;

maybe because i compiled the ipw2200 unnecessarily , 
but i think it is strange that we both have the same router, must be something to do with the router other that the heat thing, also my roomate is on the same router and he never gets disconnected ( he has windows)

I dunno how much a man should spend to get a decent router, i already thought this dang thing was a top router, next time ill save my money and get a 200$ Linksys;

regards

---

### Post by drakeoutlaw on 2005-12-16
[QUOTE=Houman]it looks like im the only one posting to this thread :p

anywyas, unfortunately things are back to the way they were :( the old weird messages are coming back and msn barely works;

i dont know what happened :( this means i guess that 1.0.8 isnt the solution to the disconnects that people have been having on the ipw2200 drivers, 

im just gonna start using my wired net :(

regards;[/QUOTE]

Upgrading to ipw2200 1.0.8 is the correct solution. and the problem in dmesg is also there but it still works fine.  I suggest you recheck your installed driver with modinfo command. Maybe your old driver was reinstalled by mistake by module-assistant or other program.

Further I recommend boosting your signal with a simple parabolic reflector on the router such as the ez-12 (costs pennies and takes 20 mins to make) on [http://www.freeantennas.com](http://www.freeantennas.com).

Regds, Drake

---

