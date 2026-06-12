---
title: "Internet woes, Help!"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by 1993cb7 on 2008-09-27
So i just installed a fresh copy of Ubuntu and everything is good except my internet doesn't work. 

I am running a Belkin N F5D8053 USB wireless adapter that is running through a Linksys Wireless router. 

No problems on Vista. 

On Ubuntu it picks it up and see's it, i input my passkey and it connects. Im able to load google and if i click on images itll load but after that it usually cuts out. 

I cant download updates or packages, it usually hangs after a while. 

Ive read through about a dozen threads and im confused. I know i have to use ndiswrapper to install the drivers for windows in linux but i cant figure out how to get Ndiswrapper without internet?

Any help would be appreciated.

---

### Post by cariboo on 2008-09-27
Ndiswrapper is on the Livecd that you used to install Ubuntu. Make sure you have the cdrom enabled in your Sytem-->Administration-->Software Sources then in a Applications-->Accessories-->Terminal type:

```
sudo apt-get install ndisgtk
```

This will install the ndiswrapper package including a gui to set things up.

Jim

---

### Post by 1993cb7 on 2008-09-28
> **cariboo907 said:**
> Ndiswrapper is on the Livecd that you used to install Ubuntu. Make sure you have the cdrom enabled in your Sytem-->Administration-->Software Sources then in a Applications-->Accessories-->Terminal type:

```
sudo apt-get install ndisgtk
```

This will install the ndiswrapper package including a gui to set things up.

Jim

Ok well it went through and installed it (i believe) it ended saying setting up ndisgtk (0.8.3-1). . .       and nothing happened....


so what would be my next step?

---

### Post by 1993cb7 on 2008-09-28
Ok so i found the .inf file and installed it and rebooted and its still there but not running like it should?

What am i missing!?!?

---

### Post by 1993cb7 on 2008-09-28
anyone?

---

### Post by melojo on 2008-09-28
what wireless device are you using?
you might have a look here.  [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by 1993cb7 on 2008-09-29
> **melojo said:**
> what wireless device are you using?
you might have a look here.  [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Belkin N FD 8xxxx

RT2870 driver.

---

### Post by 1993cb7 on 2008-09-29
ralphie@ralphies-cp:~$ lsusb
Bus 005 Device 007: ID 0411:008b MelCo., Inc. 
Bus 005 Device 006: ID 046d:c525 Logitech, Inc. 
Bus 005 Device 005: ID 0951:1603 Kingston Technology 
Bus 005 Device 004: ID 050d:815c Belkin Components 
Bus 005 Device 003: ID 050d:0307 Belkin Components 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 413c:2006 Dell Computer Corp. 
Bus 001 Device 004: ID 413c:1004 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  


ralphie@ralphies-cp:~$ ndiswrapper -l
rt2870 : driver installed
	device (050D:815C) present

ralphie@ralphies-cp:~$ uname -m
x86_64


ralphie@ralphies-cp:~$ lsmod | grep ndis
ndiswrapper           243872  0 
usbcore               169904  9 usb_storage,rt2500usb,rt2x00usb,libusual,usbhid,ndiswrapper,ehci_hcd,uhci_hcd

ralphie@ralphies-cp:~$ dmesg | grep -e ndis -e wlan
[   33.083533] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   33.671909] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   33.671915] ndiswrapper (load_sys_files:210): couldn't prepare driver 'rt2870'
[   33.672335] ndiswrapper (load_wrap_driver:112): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[   33.709342] usbcore: registered new interface driver ndiswrapper
[   51.628374] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   80.858759] wlan0: Initial auth_alg=0
[   80.858764] wlan0: authenticate with AP 00:14:bf:33:13:93
[   80.859529] wlan0: RX authentication from 00:14:bf:33:13:93 (alg=0 transaction=2 status=0)
[   80.859532] wlan0: authenticated
[   80.859534] wlan0: associate with AP 00:14:bf:33:13:93
[   80.860717] wlan0: RX AssocResp from 00:14:bf:33:13:93 (capab=0x411 status=0 aid=3)
[   80.860720] wlan0: associated
[   80.861761] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   85.612935] wlan0: no IPv6 routers present
[   97.946529] wlan0: no IPv6 routers present
[  133.518770] wlan0: RX deauthentication from 00:14:bf:33:13:93 (reason=7)
[  133.518774] wlan0: deauthenticated
[  133.971928] wlan0: authenticate with AP 00:14:bf:33:13:93
[  134.062705] wlan0: authenticate with AP 00:14:bf:33:13:93
[  134.153483] wlan0: authenticate with AP 00:14:bf:33:13:93
[  134.244258] wlan0: authentication with AP 00:14:bf:33:13:93 timed out
[  135.131683] wlan0: Initial auth_alg=0
[  135.131690] wlan0: authenticate with AP 00:14:bf:33:13:93
[  135.139903] wlan0: RX authentication from 00:14:bf:33:13:93 (alg=0 transaction=2 status=0)
[  135.139907] wlan0: authenticated
[  135.139909] wlan0: associate with AP 00:14:bf:33:13:93
[  135.140889] wlan0: authentication frame received from 00:14:bf:33:13:93, but not in authenticate state - ignored
[  135.141659] wlan0: Initial auth_alg=0
[  135.141663] wlan0: authenticate with AP 00:14:bf:33:13:93
[  135.143142] wlan0: RX authentication from 00:14:bf:33:13:93 (alg=0 transaction=2 status=0)
[  135.143145] wlan0: authenticated
[  135.143147] wlan0: associate with AP 00:14:bf:33:13:93
[  135.145892] wlan0: RX ReassocResp from 00:14:bf:33:13:93 (capab=0x411 status=0 aid=3)
[  135.145897] wlan0: associated
[  135.149395] wlan0: authentication frame received from 00:14:bf:33:13:93, but not in authenticate state - ignored
[  135.150377] wlan0: association frame received from 00:14:bf:33:13:93, but not in associate state - ignored
[  163.811622] wlan0: RX deauthentication from 00:14:bf:33:13:93 (reason=7)
[  163.811625] wlan0: deauthenticated
[  164.263918] wlan0: authenticate with AP 00:14:bf:33:13:93
[  164.354695] wlan0: authenticate with AP 00:14:bf:33:13:93
[  164.445467] wlan0: authenticate with AP 00:14:bf:33:13:93
[  164.492233] wlan0: RX authentication from 00:14:bf:33:13:93 (alg=0 transaction=2 status=0)
[  164.492236] wlan0: authenticated
[  164.492238] wlan0: associate with AP 00:14:bf:33:13:93
[  164.581638] wlan0: associate with AP 00:14:bf:33:13:93
[  164.672407] wlan0: associate with AP 00:14:bf:33:13:93
[  164.763186] wlan0: association with AP 00:14:bf:33:13:93 timed out
[  165.138252] wlan0: Initial auth_alg=0
[  165.138257] wlan0: authenticate with AP 00:14:bf:33:13:93
[  165.143000] wlan0: Initial auth_alg=0
[  165.143004] wlan0: authenticate with AP 00:14:bf:33:13:93
[  165.143283] wlan0: RX authentication from 00:14:bf:33:13:93 (alg=0 transaction=2 status=0)
[  165.143286] wlan0: authenticated
[  165.143287] wlan0: associate with AP 00:14:bf:33:13:93
[  165.143675] wlan0: authentication frame received from 00:14:bf:33:13:93, but not in authenticate state - ignored
[  165.144355] wlan0: authentication frame received from 00:14:bf:33:13:93, but not in authenticate state - ignored
[  165.144752] wlan0: authentication frame received from 00:14:bf:33:13:93, but not in authenticate state - ignored
[  165.146682] wlan0: authentication frame received from 00:14:bf:33:13:93, but not in authenticate state - ignored
[  165.147817] wlan0: RX ReassocResp from 00:14:bf:33:13:93 (capab=0x411 status=0 aid=3)
[  165.147820] wlan0: associated


So i just ran through all of those commands whats the problem??? I noticed it said that the driver isnt 64B so ill reinstall that but im sure i had the 64B driver installed and it didnt work then either. 

Im lost.

---

### Post by 1993cb7 on 2008-09-29
Ok so i rebooted with a 64B driver(the one for Vista64) and it works but as usual its horribly slow. Im sure it will drop out after a while. 

So whats going on?

---

### Post by 1993cb7 on 2008-09-29
How come i cant get any responses?!!

102 views?

I know im a noob and this issue has been talked about 210 times on here but im stuck. I don't know enough about linux to go running through the night aimlessly and possibly screw something up. 

Im trying not to give up, i had Ubuntu on the same partition as XP before and couldn't figure this out and gave up since i had Xp. 

Now i have Vista and i bought an 80G HDD just for Ubuntu. Vista works like a charm so i don't need this but i want to really give it a shot. 

Well im sure ill eventually figure it out but any help would be appreciated. 

Like i said i installed the 64b driver, i have ndiswrapper installed, and i get an internet connection but it is like really slow and drops out. 

Suggestions?

---

### Post by 1993cb7 on 2008-09-29
LOL awesome!

---

### Post by melojo on 2008-09-30
What happens if you turn off security on the router?

---

### Post by 1993cb7 on 2008-09-30
> **melojo said:**
> What happens if you turn off security on the router?

Thats not an option as i dont own the router and ultimately if it works with Windows fine, the owner isn't going to want me messing with it because im configuring a new OS. 

Like i said i have internet but its very slow and almost doesn't load sometimes.......

---

### Post by pterandon on 2008-09-30
Okay, here's my advice.  I'm almost a still a n00b myself, so take this with a grain of salt. But I have found a lot of incorrect advice on the web, advice that failed on my box.

First of all, it's my opinion that it's not the best advice to tell someone to go straight to the ndiswrapper, if you have an atheros chipset in your wifi card.

One way to check to see if your system already has a driver for your card and recognizes it. Try 

```
iwconfig
``` 

and see what the response is. If it gives you an indication that it sees an "ath0" or "wlan0" or the like, but just isn't "associated", you may merely lack the right command syntax to get it going. I found that Network Manager has been buggy since 7.04.  If you do see a lot of words next to "ath0" or "wlanO", try this.  In that case, edit as root your /etc/networking/interfaces file.  I find the easiest way to do that is to right click on the file in a file browser, then go under Actions to "Edit as root".  Make your file look like this:
 
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
auto ath0
iface ath0 inet dhcp
wireless-essid [insert your wireless essid]
wireless-key [insert your wireless key]
```

and then do:

```
sudo /etc/init.d/networking restart
```


My ornery advice is that if you don't have an atheros wireless card, go buy one that is.

---

### Post by 1993cb7 on 2008-09-30
> **pterandon said:**
> Okay, here's my advice.  I'm almost a still a n00b myself, so take this with a grain of salt. But I have found a lot of incorrect advice on the web, advice that failed on my box.

First of all, it's my opinion that it's not the best advice to tell someone to go straight to the ndiswrapper, if you have an atheros chipset in your wifi card.

One way to check to see if your system already has a driver for your card and recognizes it. Try 

```
iwconfig
``` 

and see what the response is. If it gives you an indication that it sees an "ath0" or "wlan0" or the like, but just isn't "associated", you may merely lack the right command syntax to get it going. I found that Network Manager has been buggy since 7.04.  If you do see a lot of words next to "ath0" or "wlanO", try this.  In that case, edit as root your /etc/networking/interfaces file.  I find the easiest way to do that is to right click on the file in a file browser, then go under Actions to "Edit as root".  Make your file look like this:
 
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
auto ath0
iface ath0 inet dhcp
wireless-essid [insert your wireless essid]
wireless-key [insert your wireless key]
```

and then do:

```
sudo /etc/init.d/networking restart
```


My ornery advice is that if you don't have an atheros wireless card, go buy one that is.

Ok well im not sure if i have an Atheros card....i dont think i do...mine is Ralink i believe. 

But nonetheless i dont have a wireless card i have a wireless USB adapter. 

So ill try those options but the last time i edited the network interfaces i ruined it and had to fix it lol.

I think im going to find a USB adapter that works good for both Vista and Linux.

---

### Post by 1993cb7 on 2008-09-30
Ok well i finally got it to work, im posting this from Ubuntu. 

Im excited to explore and learn but i see its going to come down to a lot of reading since responses here are a joke.

---

### Post by pterandon on 2008-09-30
> **1993cb7 said:**
> Ok well i finally got it to work, im posting this from Ubuntu. 

Im excited to explore and learn but i see its going to come down to a lot of reading since responses here are a joke.

Can you tell me how you got it to work, in case my advice were wrong and I should never repeat it to anyone again? :oops:

---

### Post by MyNameIsDerek85 on 2008-09-30
> **1993cb7 said:**
> I'm excited to explore and learn but i see its going to come down to a lot of reading since responses here are a joke.

I (kind of) agree with you on Linux's highly praised "community support", but I'm still not completely sure what to think of the forum support. The thread I posted has a total of one user helping me and as much as I appreciate his (very helpful) support, things would go a lot smoother if others would take the initiative to help a new person so that I'm not always bugging him to give me answers. I mean, I want to be able to say this whole forum is helpful, not just one user. 

At any rate, this is a web community and we can't FORCE people to help us. They aren't being paid to help us and Linux isn't making any money on us so they really don't have to provide customer support if they don't want to. Therefore, we can't really get mad at the community, just the lack of support for the operating system. Unfortunately, it's one of the area's that Linux lacks in.

---

### Post by 1993cb7 on 2008-10-01
> **pterandon said:**
> Can you tell me how you got it to work, in case my advice were wrong and I should never repeat it to anyone again? :oops:

I installed Ndiswrapper, loaded the XP 64 driver and followed this write up

[http://blog.delgurth.com/tag/ubuntu/](http://blog.delgurth.com/tag/ubuntu/)

Some of the steps didn't work but i kept going untill i reached the end and restarted and clicked on the network i wanted to connect too, it loaded and was fast as all hell. 

It works fine but leaving it on overnight it was disconnected this morning and to get it to be recognized i had to shut down and restart. For me this won't be a problem as any overnight downloading ill do in Vista but i want to be able to login to Ubuntu and use it and to do that i need internet so im content now. 


When i find a solution to it disconnecting overnight and it not loading automatically ill post it here for those who actually need the help.

---

### Post by 1993cb7 on 2008-10-01
> **MyNameIsDerek85 said:**
> I (kind of) agree with you on Linux's highly praised "community support", but I'm still not completely sure what to think of the forum support. The thread I posted has a total of one user helping me and as much as I appreciate his (very helpful) support, things would go a lot smoother if others would take the initiative to help a new person so that I'm not always bugging him to give me answers. I mean, I want to be able to say this whole forum is helpful, not just one user. 

At any rate, this is a web community and we can't FORCE people to help us. They aren't being paid to help us and Linux isn't making any money on us so they really don't have to provide customer support if they don't want to. Therefore, we can't really get mad at the community, just the lack of support for the operating system. Unfortunately, it's one of the area's that Linux lacks in.

Yea the way i look at it is they rave and rant just like the Apple folks but in the end theyre not impressing anyone. 

This OS is probably all most people here use or need but i was just suprised that when a Windows user comes on here, proclaims they want to explore and learn Ubuntu when they don't really have to since they have a flawless Vista running already with all the bells and whistles but still wants to see what a strong OS can do, they are kind of left to themselves. 

I would think that people would see initiative and want to help out. I guess they feel people want to be spoonfed but with me thats hardly the case. I just needed a little explanation and some pointers and thats it.

---

