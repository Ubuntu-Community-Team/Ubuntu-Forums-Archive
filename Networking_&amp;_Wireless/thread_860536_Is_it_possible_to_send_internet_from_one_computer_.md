---
title: "Is it possible to send internet from one computer to the next with this method?"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by robdawg5z59o on 2008-07-15
I have a laptop that runs on either ubuntu or windows xp (i selct at startup).

I have a desktop that only runs on Ubuntu Linux.

My parents will not run an ethernet cable upstairs to my room so here's what i have done so far: I installed a card that goes where the sound card, USB card, ethernet card, etc goes. This card provides a PCMCIA port for me to pop in a wireless LAN card in my desktop computer.

Here's the question:
With the wirless card installed, can i send an internet connection out of my desktop through its ethernet port and send that signal via wire to a ethernet port on my laptop?
I guess it would be like turning the desktop into a router also...any advice?

---

### Post by Felixworks on 2008-07-15
Sorry to be blunt, but couldn't you just buy a router?

---

### Post by coffeecat on 2008-07-15
> **Felixworks said:**
> Sorry to be blunt, but couldn't you just buy a router?

I think there's a router downstairs. :wink: His parents won't let him run an ethernet cable upstairs and, being a parent myself, **I don't blame them**. :)

I'm a bit mystified by your question, robdawg5z59o. Has your laptop got wireless? Is that the problem? Because if your laptop has wireless, and you've enabled wireless in your desktop, the router downstairs should be able to service both wirelessly.

One option, but it's relatively expensive. How generous are your parents? :) It's ethernet over mains. I use it in my house. Saves a lot of hassle. I've got one ethernet cable coming out of the router into a homeplug, plugged into the mains. Then I can plug in another homeplug anywhere in the house and get an ethernet signal. In fact I can plug in more than one. They all 'just work'. In one place I've got an ethernet switch connected to a single homeplug and three network devices connected to the switch. Somehow the router copes with all that through the one ethernet cable.

Worth considering.

---

### Post by issih on 2008-07-15
Yup its doable. It can be set up manually via IP tables which is a bit of a pig, or you can install something like firestarter which does most of it for you.
```

sudo apt-get install firestarter
```

If you need the dhcp server to work on the wireless end, you need to install dhcp3-server package and set up an alias from dhcpd to dhcpd3 as well

Hope that helps

P.S. I'm assuming you meant you want to pipe the internet connection from the hardwire ethernet port to the newly added wireless card (which is now acting as an access point), and then connect to the network on the laptop using the wireless networking, you weren't very clear :)

---

### Post by robdawg5z59o on 2008-07-15
i was unclear (sorry)

i receive internet by a wireless card,
i want to sent out a signal throught the ethernet jack.
if anyone knows anything about this please post

thanx!

---

### Post by xcesarfrancox on 2008-07-16
What you're trying to do is to share a wireless internet connection through your ethernet port in you ubuntu-desktop to your laptop?

Is it what you're trying to do?

---

### Post by dmizer on 2008-07-16
to solve your problem, you will need to purchase equipment.  you will need _one_ of any of the following items:
- a crossover cable
- a second wireless card
- a hub

your least headache inducing method would be to simply purchase a second wireless card, and simply connect both computers to the wireless router directly.  you will have to purchase something any way you go about this.  save your pennies for a second wireless card and go on with life.

purchasing either a crossover cable or a hub will require that you follow this howto: [https://help.ubuntu.com/community/Internet/ConnectionSharing?](https://help.ubuntu.com/community/Internet/ConnectionSharing?)

---

### Post by robdawg5z59o on 2008-07-16
to xcesarfrancox, yes.my desktop is receiving a wireless internet connection, therefore the actual ethernet jack sits unused. i want to send a signal out of that jack so that my laptop which cant receive wireless can also get internet.

---

### Post by xcesarfrancox on 2008-07-16
Actually, I understand what you're trying to do, but I don't really know exactly how to do it

What you have to do is to establish a link between your laptop and desktop via ethernet cable (you need to use crossover cable), verify the link with pinging both sides

Then you need to share your internet connection in your desktop (this is the part where I don't know how to do it under GNU/Linux), look at what issih said in post #4, it might help.

Why are you trying to do this anyway? Isn't easier to get your laptop to use wireless? I mean, via usb wireless card or a pcmcia card or something...

---

### Post by robdawg5z59o on 2008-07-16
well i cant get firestarter to even start if someone wants to contact me AIM my screen name is robdawg5z59o ill probly be on for another two hours after this post but try any time

---

### Post by robdawg5z59o on 2008-07-16
By the way, my network settings window shows a wireless connection with roaming enabled thats called wifi0
it also shows anotherr wireless connection labeled eth1
it shows two more wired connections labeled eth0 and eth2
then of course it shows a modem connection
those are the options displayed. When i went in there to try to figure things out, my observations led me to believe that wifi0 and eth1 are linked in together, actually i can disable eth0 and eth2 but wifi0 appears to be the same as eth1....basicly eth1 cant be disabled. coming close to being very frustrated right now....the only internet im getting comes from some pci bus card and a wireless card attached to it like i said before. please help me ASAP!!

---

### Post by dmizer on 2008-07-16
first things first, do you have the equipment you need?

you will need either a hub or a crossover cable. you can not do anything unless you have one of these.

---

### Post by robdawg5z59o on 2008-07-16
yes i have several crossover cables and an extra cable router

---

### Post by dmizer on 2008-07-17
please post the output of:
```
sudo ifconfig
```

---

### Post by Skinnbin on 2009-01-10
I have the same problem. I buy high speed internet that's wireless. Unfortunately it's MAC filtered. I want to know how to feed internet from my desktop to my windows laptop via ethernet cable. I run ubuntu 8.10 and as far as I know the ethernet port works.
I tried Firestarter however it tells me that "The device eth0 is not ready."
The laptop tells me that the cable is disconected and when it does connect it tells me that the other device isn't responding.

skinner@Alias:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:66:46:79:d9  
          inet6 addr: fe80::219:66ff:fe46:79d9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27874 (27.8 KB)  TX bytes:3896 (3.8 KB)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21200 (21.2 KB)  TX bytes:21200 (21.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:e4:fc:fb  
          inet addr:64.25.169.214  Bcast:64.25.169.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fee4:fcfb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22985831 (22.9 MB)  TX bytes:129601881 (129.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-E4-FC-FB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

skinner@Alias:~$ 

Please help. I'm relitively new to all this.

---

### Post by Skinnbin on 2009-01-10
I think I found the answer. 
[http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)

I still have to test it to see if it worked. But I'm hoping that everything went well.

---

### Post by dmizer on 2009-01-10
Since my last reply, I have updated the Internet Connection Sharing wiki article here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

It contains more updated information and an addional fix that the link you found does not.

---

### Post by Skinnbin on 2009-01-10
Sweet thanks!

---

### Post by Skinnbin on 2009-01-11
Just a follow up. Everything works great however on the windows laptop I just had to set up a home network. Otherwise it wont have internet. Seems simple enough... but it stumped me for a good 2 or 3 hours. Lmao.

---

