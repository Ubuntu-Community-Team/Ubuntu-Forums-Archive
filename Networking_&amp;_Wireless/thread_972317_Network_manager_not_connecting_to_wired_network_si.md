---
title: "Network manager not connecting to wired network since upgrade to Intrepid"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by Rebajas on 2008-11-05
I've just recently upgraded to Intrepid and coincidentally my wired network now no longer connects.

When I plug the cable in, the taskbar icon spins as if it will connect but then just gives up with a warning balloon. I have tried booting with the cable in and that makes no difference.

I'm a bit new at all this (3-4 years of fumbling around in the dark) so if you need more info I'd appreciate if you tell me what I need to get that info.

Other than that Intrepid seems great - so pleased that my 3G mobile broadband worked automagically that I didn't notice I had no wired network :)


Thanks!

---

### Post by Smeags on 2008-11-06
Rebajas,

Can you give some of your system specs?  I had a problem with my wired connection with the Intrepid Live CD initially.  My problem was solved by updating my motherboard's BIOS.

I don't recommend you try this as your first fix option, but by providing us with some specs maybe we can take a step forward.

---

### Post by superprash2003 on 2008-11-06
post output of ifconfig from your terminal..

---

### Post by RMOP on 2008-11-09
I hope this brings some consolation. I had the same problem, or one very close to yours. Mine is partially solved.

My upgrade just yesterday was actually a full re-installation, and initially my eee PC had no wireless -- no surprise there. Got that working w/o resorting to Madwifi, and both wired and wireless were working fine. If I plugged in my CAT5 cable, it bumped the wireless connection and registered itself with my router. If I unplugged the cable, the wireless kicked in and grabbed an IP address. Life was sweet. For a few hours...

Then I setup my Bluetooth 3G phone/modem connection. In order to use wvdial w/o root privileges, I had to chance permissions on /etc/sbin/pppd. It was only after this that I noticed my wireless was not being bumped when I plugged in my ethernet cable. So, I disabled wireless, hoping that would cure things. But, no. Something had changed. Not sure if my messing with pppd had any effect -- probably not.

A left-click on the top panel's network icon showed an entry under "Wired Network" of "Auto etho," and I could select its radio button. However, I get the same spinning blue "comet" between the green lights, followed by an error message "The network connection has been disconnected."

So, as I was composing this, expecting just to commiserate with you, I opened "Network Connections" and decided to add a NEW wired connection, after first inspecting the properties of the existing, non-working one. What I noticed was that a MAC address appeared in the properties of the existing connection, Auto eth0. I don't remember seeing that before. Hmmm, I thought...and created a new connection "Ethernet" w/o a MAC address, but otherwise the same. And it connected immediately. I unplugged the cable, but had to manually select my wireless AP before it connected, but upon plugging the cable back in, my new wired connection bumped the wireless and connected properly. So, things are as properly automated as they were before, but at least both wireless and wired are working.

There still something flaky going on. Just to make sure all my connections were working, I made a Bluetooth/3G connection (with the ethernet still plugged in). Fine. Then I stopped the modem connection and unplugged the ethernet. The wireless would not connect! Upon inspection of the properties of my wireless connection, I found that the WPA key had been changed to something completely random. I restored my key, and now all three connections seem to work OK. The only residual oddity is that, when I disconnect my ethernet cable, the connection to wireless is IMMEDIATE, w/o an intervening message or network icon animation. However, going from wireless to wired shows the animation and give the "Connection Established" message once the animation ceases. Odd.

So, try creating a new wired connection. And, let me know if you present, non-working one in fact has a MAC address under properties.

Best wishes.

> **Rebajas said:**
> I've just recently upgraded to Intrepid and coincidentally my wired network now no longer connects.

---

### Post by Rebajas on 2008-11-11
```
eth2      Link encap:Ethernet  HWaddr 00:d0:59:81:40:e1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16024 (16.0 KB)  TX bytes:16024 (16.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:92.40.143.71  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1440  Metric:1
          RX packets:1013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:837814 (837.8 KB)  TX bytes:183127 (183.1 KB)

```

Thanks people.

superprash2003: Okay, above you will see the output from ifconfig. I'm currently on the train from London home so am obviously connected to 3G but not Ethernet. I don't have WiFi to muddy the waters though wish I did :)

RMOP: That's an interesting tale! I'll try creating a new wired connection when I get back - I'm sort of hoping that with just 3G and Ethernet everything will be back to normal - I'll let you all know if that is the case.

Smeags: For reference, my poor little laptop is a Compaq Evo N200, it has a mere 192Mb of RAM and a lowly 700Mhz Intel Pentium III processor. You might be surprised to hear that it runs fairly well - testiment to Linux's ability to run on lesser hardware. I have this puppy running Apache, mySQL & PHP and the only pain I have is when I switch apps; though I'd never try anything to rigorous anyway :)

---

### Post by RMOP on 2008-11-11
Rebajas,

The plot has thickened considerably, but I *MAY * have stumbled upon a solution that works for me. My wireless also decided to go out, and it was a thrash to get it back. But, now I've got wireless, wired and bluetooth modem connections all working, and all at once if I like. See my last entry in Network Manager/Mangler Weirdness:

[http://ubuntuforums.org/showthread.php?t=976800&highlight=weirdness](http://ubuntuforums.org/showthread.php?t=976800&highlight=weirdness)

> **Rebajas said:**
> 

RMOP: That's an interesting tale! I'll try creating a new wired connection when I get back - I'm sort of hoping that with just 3G and Ethernet everything will be back to normal - I'll let you all know if that is the case.

---

### Post by Rebajas on 2008-11-12
Okay - I tried deleting the existing Ethernet option and still no joy. I have tried deleting it and creating a new one, deleting it and rebooting the machine & deleting it and pluging the cable in after.

Looks like something else must be stopping it from working.

Any ideas?

---

### Post by RMOP on 2008-11-12
You've probably *already* done all of the gyrations described below after *first disabling wireless*, right? Not that it should matter, but we're not dealing with an entirely rational application, are we?

Somethings just shouldn't be so difficult.

> **Rebajas said:**
> Okay - I tried deleting the existing Ethernet option and still no joy. I have tried deleting it and creating a new one, deleting it and rebooting the machine & deleting it and pluging the cable in after.

Looks like something else must be stopping it from working.

Any ideas?

---

### Post by Iowan on 2008-11-12
[This]("http://ubuntuforums.org/showthread.php?t=974382") How-To may offer a solution.

---

### Post by RMOP on 2008-11-13
The OTHER thing worth trying is to update Network Manager. To do so, you'll need to scour this forum for the link to manually add to Admin->Software Updates. The specific link has to be added because (I think) Network Manager is not included in the standard Ubuntu repositories. Sorry, I just saw it and used it, but can't locate the specific thread, and I'm not on my Ubuntu machine and can't check.

Anyway, updating my Network Manager allowed me to get my VPN connected, which was impossible before the update. Perhaps the update would help resolve your problem.

Let me know if you can't find it.

> **Rebajas said:**
> Looks like something else must be stopping it from working.

Any ideas?

---

### Post by Rebajas on 2008-11-13
Just to add more detail: I'm using DHCP so I'm not concerned that my IP address might be getting reset.

> **Iowan said:**
> [This]("http://ubuntuforums.org/showthread.php?t=974382") How-To may offer a solution.

Also, I don't have wireless on this machine so that won't be a problem :)

Any more ideas?

---

### Post by RMOP on 2008-11-13
SSystem->Admin->Software Sources

Select Third Party tab.

ADD [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) with ''intrepid" as distribution and "main" as component (sans quotes).

Check the box. Update Network Manager through Synaptic (you can uncheck the box later if desired). Maybe that will help. It cured some things for me.

> **Rebajas said:**
> Just to add more detail: I'm using DHCP so I'm not concerned that my IP address might be getting reset.



Also, I don't have wireless on this machine so that won't be a problem :)

Any more ideas?

---

