---
title: "Internet connection vanished"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Sanzennin on 2009-04-24
Hi, Im quite new to ubuntu (got 8.1 just a week or two ago) but managed to get it fully working for brief time. Then my internet connection vanished right into thin air. I tried to search if there would be solution that I could find in the internet and in the ubuntuforums, but either I lack the skill of finding or my problem is unique...

Anyways, so far I have confirmed that the reason lies within my own computer (tested the wire on another computer) and I think the problems not the hardware either (I added another networkcard when the problem occured, gives me green lights and ubuntu seems to see it)

I have cheched the /ect/network/interfaces just contains
auto lo
iface lo inet loopback

I tried adding stuff like 
auto eth0
iface eth0 inet dhcp

which did not work, the two lil computer screens said the device is unmanaged as soon as I added that... I removed it and back to square one.

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:5b:aa:0d:d7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xe400 

eth1      Link encap:Ethernet  HWaddr 00:10:5a:30:e1:4c  
          inet addr:192.168.0.131  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:5aff:fe30:e14c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5920 (5.9 KB)  TX bytes:1152 (1.1 KB)
          Interrupt:18 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

Im open to all the suggestions...

---

### Post by Hospadar on 2009-04-24
Couple things:

Thanks for posting your ifconfig

You shouldn't have to edit /etc/network/interfaces nowadays network connections are all made by network manager, and they won't show up in interfaces.  This makes things a lot more flexible (you plug in a new network card, get a wireless broadband deal, etc, etc).  If you want, you can just remove network manager alltogether and configure things old-school in interfaces (I do this on my server), but it shouldn't be needed.

It appears as though eth1 is in fact connected to something (your router or modem I suspect)
> eth1      Link encap:Ethernet  HWaddr 00:10:5a:30:e1:4c  
          inet addr:192.168.0.131  Bcast:192.168.0.255  Mask:255.255.255.0You can tell because the "inet addr" only ever gets filled out when you are actually connected to something.

You mentioned adding another network card recently, could you be more specific?  Do you know your router's IP address? can you ping it from a terminal? (If you don't know what I'm talking about just ask)

Are there any other machines on your local network that you might be able to test ping?

---

### Post by Sanzennin on 2009-04-24
This new card I added is that eth1 I believe. Unfortunately I do not know my routers IP address, nor do I know how to get that from terminal. Whats the command for it?

And yes, I currently have it (the new card) connected, the green lights show... uhm, green from both modem and the card. Or actually the card wouldnt be exactly "new" as its ancient, but working nevertheless.

---

### Post by lukeinvancouver on 2009-04-24
> **Sanzennin said:**
> Hi, Im quite new to ubuntu (got 8.1 just a week or two ago) but managed to get it fully working for brief time. 

Im open to all the suggestions...

This is exactly my experience except that you obviously know more about Linux than I do.

But I had a similar, or identical problem, and some kind soul saved me after less than a day of struggling unsuccessfully, with it.

What CPU does your machine have? (Is it an Intel Atom ?)

Boot up from the CD-ROM drive with the CD in it. (You can put it in the drive before shutting down. Make sure your BIOS is configured to boot from the CD-ROM.)

Does it connect to the net automatically? (Mine did but not anymore after I updated. That bug has been fixed but I see some similarities.)

Click on the network icon. Is auto tho checked?

I'll dig up the link to the page where my problem was discussed in the next post.

---

### Post by Sanzennin on 2009-04-24
> **lukeinvancouver said:**
>  
What CPU does your machine have? (Is it an Intel Atom ?)

Boot up from the CD-ROM drive with the CD in it. (You can put it in the drive before shutting down. Make sure your BIOS is configured to boot from the CD-ROM.)

No, athlon.
But that CD trick just might work, going to look for the CD... I know I have it somewhre here... :P

---

### Post by lukeinvancouver on 2009-04-24
My problem was discussed here:

[http://ubuntuforums.org/showthread.php?t=1117139](http://ubuntuforums.org/showthread.php?t=1117139)

Good luck. 

If all fails you might consider starting from scratch. I did six so far in 2 weeks but finally I'm getting somewhere with Linux after several attempts over 2 or 3 years.

Ubuntu and this community are both incredible IMO.

---

### Post by Sanzennin on 2009-04-24
Ok, so far, with CD inside it works, CD out and doesnt.
Thanks, I guess that link could help me then, looking at it

EDIT:
Lukeinvancouver, that didnt work =(


So I still need help, if anyone has any ideawhat to do, please do tell me

---

### Post by lukeinvancouver on 2009-04-24
> **Sanzennin said:**
> 

So I still need help, if anyone has any ideawhat to do, please do tell me

Reinstall?

---

### Post by Peter09 on 2009-04-24
Just a check, right click on the network manager icon and edit your connection, check that you do not have a static IP set up, I would think you should be using DHCP.

---

### Post by lukeinvancouver on 2009-04-24
> **Peter09 said:**
> Just a check, right click on the network manager icon and edit your connection, check that you do not have a static IP set up, I would think you should be using DHCP.

I'm not really qualified but in my case it was a not-so merry go around. Auto etho could not be enabled. (If you are curious, see above link) and I think it should be.

Is "auto etho" checked when you left click the network manager?

---

### Post by JK3mp on 2009-04-24
I've had similiar problems at one point. Just shutdown normally. Keep it off for a minute and boot back up usually fixes it. if not try using WICD. Its an alternative Wirelss and wired connection manager to the gnome network manager. if that doesn't work i'd try reinstalling or making sure your wireless drivers are indeed working proper.

---

### Post by Sanzennin on 2009-04-25
Yeah, auto eth1 or auto eth0 are checked depending on in which network card do I plug the wire, however, neither of these works and as in your case, it says "never" when I go to check when was it last used (in network manager). I can always create a new connection too, that it will say is used, but I still cant connect. Oh, and hey, the only connections there are are auto eth1 and auto eth0, I checked all the tabs there's nothing in the otherparts, should there be?

And yes, I have checked and doublechecked that all settings are put to dhcp and I am not using static IP or anything.

I wouldnt want to reinstall, as it is rather likely that I will bump into the same problem again (as you did, right?)

---

### Post by Sanzennin on 2009-04-25
> **JK3mp said:**
> I've had similiar problems at one point. Just shutdown normally. Keep it off for a minute and boot back up usually fixes it. if not try using WICD. Its an alternative Wirelss and wired connection manager to the gnome network manager. if that doesn't work i'd try reinstalling or making sure your wireless drivers are indeed working proper.

Naturally, I have tried that already... 
And I dont have wireless, I have wired. And as said, hardware is working properly, for example if I boot from CD my connection works.

(Sorry for doublepost, for some reason the edit button doesnt seem to work atm)

---

### Post by Peter09 on 2009-04-25
Just a thought - are you telling us that you have two ethernet connections active on the same machine, are they both connected to the LAN?

Can you type
```
route
```
in a terminal and post the output.

---

### Post by Sanzennin on 2009-04-25
Well, just one of them should be connected, or so I think, however, this is what route gives:

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

And as JK3 suggested, I installed WICD, which didnt help me either. On the positive side, the places where the problem could be are running out... bound to find it soon.

---

### Post by Peter09 on 2009-04-25
According to route, you are using eth1. Can you do ifconfig again so that we can check that you have the correct setup. If you are using DHCP can you check what IP range your router is allocating.

---

### Post by Sanzennin on 2009-04-25
Ummm... How do I check the IP range that my router is allocating?

---

### Post by Peter09 on 2009-04-25
Well, if you know what any other machine on the LAN's ip is we can have a good guess. Ideally you could log into your router and look at the DHCP settings, however if you have not done that before best to leave it.

---

### Post by Sanzennin on 2009-04-25
ifconfig
eth1      Link encap:Ethernet  HWaddr 00:10:5a:30:e1:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)


Hmm, I see eth0 vanished

---

### Post by Peter09 on 2009-04-25
This is getting complex because of your two interfaces, have you got the ethernet cable plugged into the active interface?

---

### Post by Sanzennin on 2009-04-25
Naturally (and just in case, I have changed it quite a few times.)
Oh, and by the way, WICD (tried that as someone suggested to see if my problem would go away) says that I am connected to a network (the only one it finds) but I cant access internet at all, cant download packages and so...

---

