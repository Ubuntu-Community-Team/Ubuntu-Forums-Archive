---
title: "spyware with linux"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by jacob01 on 2007-09-16
is it possibe to get any spyware with linux using firefox.

for some reason my downloads are really slow 50kb/s compared to 180kb/s usually. and then my network usage says like double that of the download. like 130kb/s   and also my internet is really slow.

if their are any spyware removers for linux can you give me a link

what could cause this problem?

---

### Post by NightCrawler03X on 2007-09-16
That is (if connected to a router through wireless) probably something interfering with the signal, or someone else on the netwrok, downloading something (i.e. hogging all the resources)
If it's wired, it's probably just network traffic from some applications you may be running

Linux does not get spyware. It was anti virus software for it, but this is only for linux clients that serve files to windows clients.

(In fact, I find asking for a -linux- spyware remover rather offensive)

---

### Post by jacob01 on 2007-09-16
yea i know thats why i hesitated about asking about spy ware. but i have no other ideas what could be happening it like im being limited and my network traffic says over twice as much as the download says and the downloads are slow. Im pretty sure its not other network traffic since it still does it when the other com is completely turned off. i do have a wirless router but im pretty sure there is a wep protection and another weird thing is that when i stop the download the network traffic stops.

my download say 60kb/s and network traffic says 137kb/s then when i stop it the network traffic stops. it is really confusing i have no idea what it is and its really bothering me. i had friend who had a similar problem were his downloads were going really slow and he fixed it by doining a clean install but id rather not go through the hassle of reinstalling ubuntu and the video drivers and backing every thing up but i am willing to if it will fix the problem.

i have had this problem for about 4 days.

my other comp runs fine but this one doesn't want to

i know its not the download source since i tried the ubuntu repository and that is also slow at around 50kb/s compared to 180-190kb/s

if you need any more info just ask

please help

---

### Post by NightCrawler03X on 2007-09-17
hmm, sounds like a low signal to me.
Do the following at your shell:
su (to run commands with root permission)
iwconfig
And copy pasta the results here

By reading that, I can determine whether or not it is just a low signal causing the slowdown.

*ONLY read the below if you have a low signal*
If this is the case and you want download speeds back up, you'll either have to connect to your router with wires, or move your computer closer to it.

If you have things like microwave ovens or mobile phones (they give off radiation) operating on the same channel as your router, that might also be what is interfering with the signal, in which case you could try simply changing the channel that your router operates on.

anyway, just do what I've said here, and from there I'll try my best to help you.

PS:
About the fresh install thing, that's not really a problem, but only do it as a last resort, and if you do, BACK EVERYTHING UP. Seems much simpler than downloading everything again from scratch.

---

### Post by zach12 on 2007-09-17
2.4ghs phones (landline)
they will slow a wifi network down fast!

---

### Post by jacob01 on 2007-09-17
im not running any 2.4 gigahertz phones but unless some one down the road is using up most of the band width but that still would not explain why my network says 130kb/s and the download says 50 kb/s. also im not sharing it with any one else and that makes it kinda weird.

---

### Post by jacob01 on 2007-09-17
> **NightCrawler03X said:**
> hmm, sounds like a low signal to me.
Do the following at your shell:
su (to run commands with root permission)
iwconfig
And copy pasta the results here

By reading that, I can determine whether or not it is just a low signal causing the slowdown.

*ONLY read the below if you have a low signal*
If this is the case and you want download speeds back up, you'll either have to connect to your router with wires, or move your computer closer to it.

If you have things like microwave ovens or mobile phones (they give off radiation) operating on the same channel as your router, that might also be what is interfering with the signal, in which case you could try simply changing the channel that your router operates on.

anyway, just do what I've said here, and from there I'll try my best to help you.

i tried what you said but that is for a wireless network adapter and im using a wired connection

yea the clean install will be my last resort.

PS:
About the fresh install thing, that's not really a problem, but only do it as a last resort, and if you do, BACK EVERYTHING UP. Seems much simpler than downloading everything again from scratch.

im not using wireless, im on a wired network but i do have a wireless router

---

### Post by whoboo on 2007-09-17
It sounds like network retransmissions are a possible cause.
I recently had to adjust MTU on landline connection - out of the blue.
There is or at least was an issue with window size (transmit window) that would degrade performance.
Search the forum and you will find the threads.

---

### Post by jatos on 2007-09-17
Try this

go into a console, and type 'sudo ps -A'

Post the output here, if you find dpkg or apt-get they are probably the source of your problem. I have feeling you system is just downloading updates in the background.

Also you might want to download the program 'ethereal' from the repositories. Its a packet sniffer and will tell exatly what is going in and out of your computer.

---

### Post by Gremlinzzz on 2007-09-17
Firefox add on
[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

---

