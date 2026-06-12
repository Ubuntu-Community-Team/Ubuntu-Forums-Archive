---
title: "Belkin Wireless Adaptor and Ubuntu"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by ade_1 on 2007-01-01
Hi, 

I was wondering if someone could help me with a problem I am having with my wireless USB adaptor...

I have tried running Ndiswrapper via a package on packages.ubuntu.com and I have inserted the driver inf file and it says Hardware Detected (something like that) : Yes. So it has been detected yet still I cannot use the internet as I cannot connect to anything...

If someone could help it would be great as I am banging my head against a brick wall for god knows how long. ](*,)

I am using Ubuntu 6.1

---

### Post by ade_1 on 2007-01-02
Anyone have any ideas?:-k

---

### Post by CalumII on 2007-01-02
I'm using a PCI card, rather than a USB dongle, but you might find my recent post gets you at least part of the way:

[http://www.ubuntuforums.org/showthread.php?t=328852](http://www.ubuntuforums.org/showthread.php?t=328852)

You sound like you have a working piece of hardware, but you just need to configure the connection - maybe you could try network-manager and see if you get anywhere wth that?

Cheers,
Calum

---

### Post by ade_1 on 2007-01-02
Thanks for that Callum, I shall take a look.

Regarding the network manager, I only have 2 options. Wired connection or Dialup. Neither of which I am using.

I will pop up a screenshot of what I am actually getting to give you and others a better idea of my problem.

---

### Post by [L2G] Slapshot on 2007-01-02
Hi ade_1

Also take a look at this thread Which I helped someone with

[http://ubuntuforums.org/showthread.php?t=323481]("http://ubuntuforums.org/showthread.php?t=323481")

I use a Belkin wireless g usb stick with ndiswrapper using the original windows xp drivers and inf files.

Cheers
Jacko

p.s
Just remember the rt73 ralink driver is plug and play so remove the usb stick the reboot the p.c without it and after logging in and all activity has finished insert the usb stick and wait about 10 seconds for it to be detected.

---

### Post by ade_1 on 2007-01-02
Thanks Slapshot I will take a look :).

Here is what I am currently getting. By the sounds of it I may have added the wrong driver...

(Apologies for the image, it had to be taken with my phone as the battery on my camera is currently recharging and I couldn't put the screenshot on my USB stick as I was denied permission)

[http://img377.imageshack.us/img377/4035/photo0030lg5.jpg](http://img377.imageshack.us/img377/4035/photo0030lg5.jpg)

---

### Post by [L2G] Slapshot on 2007-01-02
Ade_1

Can you type in the command line lsusb and copy and paste the output here in a post and we can identify the vendor and the code it gives to determine what driver you need if it's compatible.

Thats LSUSB  but in lowercase just to show you it's a letter L 

Cheers
Jacko

p.s. do you have the install cd for windows that came with the adaptor

---

### Post by ade_1 on 2007-01-02
I will do that for you :).

Just a quick question, did you happen to view my image of the driver I have "installed" for Ndiswrapper ?

Yes, I do have a windows installation CD for my adaptor. I got the driver from that. It is shown on the image. (There is a link a few posts up)

---

### Post by ade_1 on 2007-01-02
The output of lsusb are as follows: 

Bus 005 Device 004:ID 050D:705C Belkin Components
Bus 005 Device 001:ID 000:0000
Bus 003 Device 002:ID 413C:2005 Dell Computer Corp.
Bus 003 Device 001:ID 0000:0000
Bus 001 Device 001:ID 0000:0000
Bus 004 Device 001:ID 0000:0000
Bus 002 Device 003:ID 413c:3200 Dell Computer Corp.
Bus 002 Device 001:ID 0000:0000

(That is typed up accurately) I was unable to copy and paste as I have no way of getting the text from Ubuntu onto Windows.

Thanks

Aidan

---

### Post by dsimpson on 2007-01-02
Have you tried Wireless Assistant, I used it on mty Belkin wireless G Router installation and it worked without a problem. I ran the Wireless assistant on the computer that has the card and it searched and found the router which was wired into the modem and connected to my other computer via ethernet. I am running Dapper 6.06 on both computers though and don't know if it will affect the way it installs when Microsucks is thrown into the mix. I will check back on your posts to see if this helps any.

---

### Post by [L2G] Slapshot on 2007-01-03
Hi Aidan,

Check this thread out based on the reported device id of your usb adapter.

The reported id is this bit in red  Bus 005 Device 004:[COLOR="Red"]ID 050D:705C[/COLOR] Belkin Components,

That shows it to be a Belkin F5D7050 ver 4000 (ZyDas zd1211b driver)

Here's the link mate I hope it gets you there:-

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29")


Please let us know if it works as others who follow will know it works also, but if it doesn't I'll keep checking back mate. I am a Linux noob myself but I'll try to help and others who are more knowledgeable will usually jump in along the way.

Cheers
Jacko

---

### Post by ade_1 on 2007-01-03
Thanks very much for the link Slapshot, it is much appriciated. I will try that out later today/tomorrow. I will post back my results. I hope I will be successful. 

Dsimpson - Where abouts can I find the Wireless assistant, it may be useful if I fail on the step by step guide that Slapshot provided.


Thanks

Aidan

---

### Post by [L2G] Slapshot on 2007-01-03
Hi Aidan,

I also use wireless assistant to manage my usb stick ( it's different from yours ), it even copes with wep encryption, but get it working without encryption first its easier lol.

just do a search for this in synaptic or adept whichever you use.

  wlassistant

By the way this is for kde not gnome, so it may want to install quite a few dependant packages related to kde, the package installer should handle it though and sort it all out. You can I believe run kde or gnome bits and bobs together.

Take care
Jacko

---

### Post by ade_1 on 2007-01-03
I am having a little bit of problem with the guide.

What does 'uname -r' mean? I guess it means my username of the account on Ubuntu but what does the -r stand for and what do I have to replace it with?

If I do not have to replace it with anything then I am expreiencing problems when doing step 2.

Thanks for the help

Aidan.

---

### Post by [L2G] Slapshot on 2007-01-03
Aidan

Thhe uname -r is the command you type here is my code it is for getting the version of kernel you are running so you can download any headers for the kernel so you can compile drivers etc. There are that many kernel versions, type that and you have the exact version you are running.

Here is mine as an example just type           uname -r                    

jacko@jacko-desktop:~$ uname -r
2.6.17-10-generic
jacko@jacko-desktop:~$

2.6.17-10-generic              the answer returned from the command is the kernel version that is mine, yours might be different. Then if I rember the way they wright, put the text you get back from the uname -r command inside the quotations but remover the quotations, example step 2 for me would be


user@ubuntu:~$ sudo apt-get install linux-headers-2.6.17-10-generic
user@ubuntu:~$ sudo ln -s /usr/src/linux-headers-2.6.17-10-generic /lib/modules/2.6.17-10-generic/build

The second line is creating a symbolic link or if you like a link between the files hence the first bit sudo ln -s  this lets the files know the path to the build directory for compiling, ie so it knows where it is and can find the info it needs to build the driver and the info it needs from the headers or if you like the main kernel info repository with all the files for compiling. LOL you are now getting to my limit of knowledge but well get you there


Hope this helps.
Jacko

---

### Post by apapww on 2007-01-03
Thanks ever so much[.](http://hk.yahoo.com)[.](http://www.ec2biz.com)[.](http://www.rthk.org.hk)[.](http://www.ads28.com)[.](http://www.ec2biz.com)[.](http://www.top1.com.hk)[.](http://www.ads28.com)

---

### Post by ade_1 on 2007-01-03
Thanks Slapshot, that has helped a lot. I will give it a go :)

---

### Post by ade_1 on 2007-01-05
The guide worked a treat although I am stuck on one bit...

I got up to step 7 and configured the settings in Networking although this is where the problem comes in... When I look at my desktop in the top right it has a symbol with 2 monitors on, I am assuming that is the wireless, and when I hover over it, it says No Network Devices Found...

And when I type iwconfig I get the following -

```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"MY_ESSID"   
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated  
          Bit Rate:1 Mb/s   
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=40/100  Signal level=12/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:2
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And when I go onto Firefox I can't display any websites as it isn't connected.

Thanks 

Aidan

---

### Post by ade_1 on 2007-01-05
Just to add I have installed WiFi Radar and my router is being picked up. At the bottom of the WiFi Radar window it says Connected to "My Router" ip (127.0.0.1) - I believe that IP is causing the problems. (It's just a thought)

---

### Post by [L2G] Slapshot on 2007-01-06
Hi Aidan

Sorry but I've been working mate, yes the ip addy you have there is actually the loopb back adapter address. You need to put in in the network manager the ip addy of your router and your ip addy of your machine or just your router ip if you are using dhcp as the router will automagically assign you an ip at connection time. Your routers ip addy should be something along the lines of 192.168.2.1 or something very similar. Check your documentation for this address. It will be given as it's the addy you would type into your browser without the http stuff so you can log on and make changes to your router. Unfortunately I use the KDE desktop not Gnome so I'm not familiar with where you put the addy, but it will be in network manager. In KDE and It'll be the same in gnome it is called the default gateway ip address. It's the gateway to the outside world in effect. i.e yor routers ip.

Hope this helps
Jacko

---

### Post by ade_1 on 2007-01-06
Thanks Slapshot, I will have a look for the routers IP, although I remember I used to be able to access it via an ip address however now it is only accessible by typing in in words i.e. bthomehub.home - rather odd I know...

And by the way, there is no need to apologise, I am in no rush :P.

---

### Post by [L2G] Slapshot on 2007-01-06
hehehehe

Good let me know how you get on mate.

Jacko

---

### Post by ade_1 on 2007-01-06
I am actually struggling editing the IP addresses. I a connected to my BTHomeHub but by the ip 127.0.0.1 which is my local host. I don't seem to be able to change this.

If someone who has past experience of using the Networking application from the Administration menu could possibly assist me with doing this it would be much appriciated.

(sorry if it isn't well described!)

If anyone can help it would be much appriciated.

Thanks in advance,

Aidan

---

### Post by ade_1 on 2007-01-08
bump

---

### Post by [L2G] Slapshot on 2007-01-09
Hi Aidan

It's me again, have you tried configuring the device via the command line to use dhcp etc. If not then I'll look at the command line stuff to try to do that for you.

Cheers
Jacko

---

### Post by [L2G] Slapshot on 2007-01-09
Aidan

Also check out this wireless troubleshooting walk through guide in the docs section it looks pretty good from everything from config to sorting out ip addresses.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Cheers and let me know how you go

Jacko

---

### Post by ade_1 on 2007-01-09
> **'[L2G] Slapshot said:**
> 

have you tried configuring the device via the command line to use dhcp etc. 



The answer to that would be no... I never thought of doing it that way, although truth be told I don't know how to do it that way lol. I am guessing that there is a guide somewhere in the documentation/troubleshooting stuff on Ubuntu.com ?

O and by the way, sorry for wasting so much of your time Slapshot....

Thanks in advance 


Aidan

---

### Post by [L2G] Slapshot on 2007-01-09
Hey mate I'm learning aswell now :-)

It's all valuable oh and by the way I've found out that most routers only use a certain set of internal ip addresses so perhaps just trying to put in the most common ones one at a time might work or if you could give us the exact model of bt router you have I can find it on the web somewhere.

Cheers
Jacko

---

### Post by [L2G] Slapshot on 2007-01-09
Hehehe

Just found out that nearly all bthomehub.home. have as their internal ip or your gateway ip as 

192.168.1.254

So try putting that one in the default gateway or whatever it is in gnome and then selecting dhcp so the hub will assign the ip addy for your p.c at connection to the hub.

Jacko

---

### Post by gmanigault on 2007-01-09
Sorry to hear that you have problems.   I have ubuntu loaded on two systems.  One desktop as a server but with no wireless.  The other is on a laptop.  I have a Belkin AP 54g and went out and bought a D-link wireless card foe the laptop.  Plugged it in loaded Ubuntu and it worked right off the bat.....


Gary M. 

GWShark

---

### Post by ade_1 on 2007-01-10
I tried to pop the gateway address in.... Although I have done something bad....

When I was messing around the other day trying to get it working I accidentally, well purposefully deleted the 127.0.0.1 loop back address in an attempt to get it to recognise the address I had put in as it was defaulting to the loopback address. I did this without knowing the consequences. I should have found out before I did it but I was stupid enough to not bother.

I now need to somehow sort out my "Networking" program as every time I open it a bug report opens instead... 

For anyone that can help I go to Administration>Networking and use that program to sort my internet.

Thanks for all the help

Aidan

---

### Post by ade_1 on 2007-01-12
bump

---

