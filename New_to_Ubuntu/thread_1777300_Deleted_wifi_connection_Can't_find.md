---
title: "Deleted wifi connection: Can't find"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Dragonegg235 on 2011-06-07
I got Ubuntu a couple of days ago, and the wifi here worked fine for a while.  It started acting up, and so I do what any normal person does: started hitting random buttons (ok, maybe not every person).  I eventually brought myself to the internet connections page for the umpteenth time, and I clicked the little "delete" button under my wifi after right-clicking it.  It must have looked really inviting at the time.  So, the problem I am left with is being tethered to my router by my 5-foot ethernet cable, waiting for my new OS to magically restore the lost connection from the abyss that computers put deleted things into.  I think.  This is probably an easy fix, or maybe a really hard one, for that is how computers work.  Only the extremes of the difficulty spectrum.  Any helpful (or maybe funny, depending on the quality) replies are wanted.  Thank you for your time.

---

### Post by wolfen69 on 2011-06-07
Right click the network icon on the panel and select *edit connections*. Then go to the wireless tab and enter your info.

---

### Post by jaacko on 2011-06-07
Things I'd check first:

- Is 'Enable wireless' ticked when you click on the network connection icon in the indicator area (it's the thing on the top right corner with the date and time and a picture of an envelope)

- Since you clicked some 'Delete' button, I think you removed the automatic wireless connection from the list of known wireless networks. Your network should be listed in the network connections (the thing you clicked in the previous part), assuming of course that your wireless is enabled. Then just enter your network encryption key if any.

If these don't help, you could post what running the command
```
ifconfig
```
in terminal outputs for you.

---

### Post by Dragonegg235 on 2011-06-07
wolfen69: Sorry if I sound dumb, but I clicked "add" on the wireless network page, then put in the network name and password.  Not sure what to do from there, because nothing changes throughout the system, that I've seen.

jaacko: There's an "Enable Networking", but no "Enable Wireless".  I'm not trying to be sarcastic here, just accurate (Added this after I realized that it could be taken as sarcastic).

I haven't seen any indication of the network's presence.  Anywhere, frankly.  Not anywhere in the "Edit connections" page, or in the icon drop-box at all.

Oh, and what came back from terminal:
> 
eth0      Link encap:Ethernet  HWaddr 00:22:15:97:02:d0  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe97:2d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:9955 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7500 errors:0 dropped:0 overruns:0 carrier:13
          collisions:0 txqueuelen:1000 
          RX bytes:11254665 (11.2 MB)  TX bytes:1114148 (1.1 MB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

---

### Post by jaacko on 2011-06-07
Ok. It seems that you have managed to disable your wireless interface. Try running this command in terminal ```
sudo ifconfig wlan0 up
```
this should bring your wireless interface back to life.

---

### Post by Dragonegg235 on 2011-06-07
I would do something like that in an effort to fix something.
But, I think there's a problem:
> wlan0: ERROR while getting interface flags: No such device

---

### Post by jaacko on 2011-06-07
Ok. Then your wireless interface might have a different name... Are you sure your wireless radio is switched on on your computer (if there are any hardware keys or switches to toggle it on/off)?

You could try ```
sudo ifconfig ath0 up
```.

If that fails also run ```
sudo lshw
```
and look for something like this (the output is quite long):
```
       *-network
             description: Wireless interface
             product: AR5001 Wireless Network Adapter
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:03:00.0
             logical name: wlan0
             version: 01
             serial: 00:1f:e1:92:a5:df
             width: 64 bits
             clock: 33MHz

```
This is the output on my computer and as you can see, my wireless interface is wlan0.

---

### Post by Dragonegg235 on 2011-06-07
I cannot believe that this just happened.  I'm usually one of the good ones on computers.  But I've never used an Ubuntu before, so when my network stopped I thought "must be the new OS".  Now I must find a corner of the room I'm in to bang a pot against my head while simotaneously reading computer books and crying, for my internet switch is fn-f2.  
But in all seriousness, thank you for your time.  And help.  I hope I start to learn some day :P

---

