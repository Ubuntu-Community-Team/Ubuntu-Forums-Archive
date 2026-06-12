---
title: "Networking issues on every version of Ubuntu..."
date: 2011-07-18
forum: New to Ubuntu
---

### Post by sideaway on 2011-07-18
Hi fellas, if anyone knows anything about linux and networking I could really use your help.

I've built a new computer and dual booting Windows 7 and Ubuntu 11.04 and just recently 10.04, and 11.10

Intel i7 2600k
Gigabyte Z68-UD4-B3
8gb ddr3-1600
120gb Intel 320 series SSD
MSI HD5870
Corsair 650w modular

Pretty nice machine. Boots in under 20 seconds from on button to useable desktop, applications open like they were minimised, reading files is instant, but damn the network is slow on Ubuntu. Internet, Network shares, even SSH is nigh on unusable. It'll struggle to pull 100 kb/s on a gigabit connection to a local PC.

It's rediculous. Networking is setup like the following;


```

Router >>|  Netgear Gigabit Switch >>| Linksys Wireless switch >>| Laptop
                                     | File Server               | Laptop
                                     | Desktop                   | Laptop
                                     | Desktop                   | Phone
                                     | Desktop                   | Phone
                                     | Laptop                    | Phone

```
The laptop will download files at thrice the speed of the ubuntu box. If you reboot into windows however, it's fine. I thought it might be 11.04, so I rolled back to 10.04. No cigar, networking is just as crap as before.

Next I tried a newer version of the kernel, so I downloaded Oneiric Ocelot and installed running kernel version 3.0-3 and blasted the network card. This is the result;

[[IMG]http://i.imgur.com/Ou3t2l.png[/IMG]](http://imgur.com/Ou3t2)

As you can see it's peaking at around 60kb/s for approximately 2 seconds... everything likes to time out as you can imagine. My now two month old computer has had next to no use as it's pretty much unusable for almost everything lol. About the only thing I can see that's causing the issue is that I'm using 64bit...? Could that possibly be the issue?

PC is almost exactly two months old.

Also, is there any reason that it's keeping the PC using an i7 constantly at 20% usage? That's odd behaviour.

---

### Post by pawhtiobo on 2011-07-18
Hi,

I can advice you to do some testings with the MTU settings in the network config of Ubuntu, try to set it to max 1500 and then test the results, another thing that can be happening is that the driver is not negotiating correctly the speed of your network card, try to force the speed, first 100 Full Duplex or 54G, i didn't understand if that PC is using wired or wireless networking... and then do some testing... 
About the CPU is always at 20%, have you checked out what process is eating the CPU usage?

See ya...

---

### Post by amjjawad on 2011-07-18
I'm not an expert for sure but I could give some advices that might help :)


1- I had an issue with my Wireless USB Adapter. It was disconnecting frequently and the browsing speed was bad. It happened that the issue was a wrong driver or actually a conflict with many drives were trying to work at the same time. I fixed the conflict and it's working as it supposed to. No disconnections AT ALL anymore :)

2- Ubuntu 11.10 is on Alpha stage, hence it is NOT recommended to "install it" on your HDD. If you'd like to play with it, do that on external media such as external HDD or USB Drive.

3- CPU Usage 20%? so? what's the big deal? you bought something like that to use it so don't worry too much about that ;)
I wouldn't if I were you.


This is how I managed to fix my issue: [http://ubuntuforums.org/showthread.php?t=1643545](http://ubuntuforums.org/showthread.php?t=1643545)

---

### Post by sideaway on 2011-07-18
> **pawhtiobo said:**
> Hi,

I can advice you to do some testings with the MTU settings in the network config of Ubuntu, try to set it to max 1500 and then test the results, another thing that can be happening is that the driver is not negotiating correctly the speed of your network card, try to force the speed, first 100 Full Duplex or 54G, i didn't understand if that PC is using wired or wireless networking... and then do some testing... 
About the CPU is always at 20%, have you checked out what process is eating the CPU usage?

See ya...

Hi, I'm sorry, I said gigabit connection, I thought that implied a cable connection - should have made that more clear sorry!

All that avice sounds great, but I have no idea how to do all that - is there some kind of guide avaliable?

---

### Post by alphacrucis2 on 2011-07-18
Some basic things. Make sure you aren't getting tx/rx errors.

```
ifconfig
```

Will give you the stats. 

Your ping times look ok but I would try pinging with large packets.

eg.

```
ping -s 1400 192.168.1.11
```

Another thing I just thought of, make sure you don't have a duplexing mismatch.

```
sudo apt-get install ethtool
sudo ethtool eth0
```

Will display the negotiated speed & duplex. I have seen bad performance problems, where one end of a link is running hdx and the other end fdx. This wont show up as a problem with pings as they don't load the connection sufficiently but will throttle file transfers horribly.

---

### Post by decoherence on 2011-07-18
I think pawhtiobo was on to something by suggesting a speed auto-negotiation mismatch. It would cause the crappy networking you are experiencing and it's feasible that it would be a problem for Linux and not Windows if it is a driver issue.

Confirm that the port on the switch is set to gigabit/full then in Ubuntu's network settings, set the network adapter to gigabit/full and see if that solves your problem.

---

