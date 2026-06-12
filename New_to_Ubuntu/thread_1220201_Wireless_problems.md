---
title: "Wireless problems"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by lewstherin01 on 2009-07-22
Hi guys I'm new to Ubuntu and have just installed jaunty.  My wireless keeps disconnecting and the only way to get it to reconnect is by restarting.  Any help will be very much appreciated.

---

### Post by Tman5293 on 2009-07-22
What wireless card are you using???

---

### Post by lewstherin01 on 2009-07-22
How can I check?

---

### Post by brookie on 2009-07-22
1. open up a terminal by clicking on
Applications/Accessories/Terminal

2 in the termial type in
lspci | grep Wireless

...and you should get something like this: 

02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

...or just type lspci and read through the list it spits out and find your card.

---

### Post by lewstherin01 on 2009-07-22
I tried that Brookie and the only thing I could find which may be similar is this:

06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139

---

### Post by brookie on 2009-07-22
that's your ethernet card hmmm.
lspci should list your wireless card too

i found this link on how to check other hw drivers but you have to scroll up in your terminal to see the results after running them

[http://ubuntuforums.org/showthread.php?t=320202]("http://ubuntuforums.org/showthread.php?t=320202")

---

### Post by lewstherin01 on 2009-07-22
I went into vista and the wireless card is called 802.11g mini card wireless adapter and it's made by Ralink.

---

### Post by lewstherin01 on 2009-07-22
*-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:0d:48:e4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.54 multicast=yes wireless=IEEE

That was the info that appeared when I typed in lshw

---

### Post by lewstherin01 on 2009-07-22
Any Ideas guys?

---

### Post by Durden on 2009-07-22
It's only doing it in Linux and not Windows?

---

### Post by lewstherin01 on 2009-07-22
Yeah.  My connection is fine in Windows.  It disconnects at random times.  I have been using it now for about 2 hours but earlier it would disconnect after ten minutes.

---

### Post by Durden on 2009-07-22
Wait a while and see if it persists. Disconnects in my experience aren't usually driver related. If it connects int he first place it should just work. You may want to reboot the wifi router and see if it makes any difference. I am by no means an expert on wireless connections though.

---

### Post by lewstherin01 on 2009-07-22
I'll give it a try.  This is the only annoyance I've had since I changed to ubuntu.  It kicks the **** out of vista.  :D

---

### Post by LookTJ on 2009-07-22
what is the output when

```
sudo lshw | grep Network
```
is issued?

lshw - list hardware

:)

---

### Post by lewstherin01 on 2009-07-22
There is no output.  It says PCI (sysfs) then ends with no output.

---

### Post by LookTJ on 2009-07-22
> **lewstherin01 said:**
> There is no output.  It says PCI (sysfs) then ends with no output.
You didn't let the command finish its job ;)

---

### Post by lewstherin01 on 2009-07-22
I did it just came back to start with no output.

---

### Post by LookTJ on 2009-07-22
> **lewstherin01 said:**
> I did it just came back to start with no output.
Interesting how lspci and lshw doesn't show your card.

Did you try ```
lspci | grep Network
``` Instead?
Keep in mind that the command here is case sensitive. :)

If no good, I hope someone will come along to help you :D

Happy adventuring!

---

### Post by dk06 on 2009-07-22
>  My wireless keeps disconnecting and the only way to get it to reconnect is by restarting.Sounds like a Network Manager issue,
Try reinstalling the "**gnome-network-manager**" through the Synaptic Package Manager


Same problem here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/331103](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/331103)

---

### Post by lewstherin01 on 2009-07-22
Thanks for the help fella but it didn't help either lol.  It hasn't disconnected in a while so hopefully i'm past it!

---

### Post by Durden on 2009-07-22
Type "ifconfig" at the terminal and paste the output here. Should at least give us the interface name.

---

### Post by lewstherin01 on 2009-07-22
I'll try that cheers mate.  :D

---

### Post by lewstherin01 on 2009-07-22
eth0      Link encap:Ethernet  HWaddr 00:03:0d:5b:e5:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1968 (1.9 KB)  TX bytes:1968 (1.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:db:0d:48:e4  
          inet addr:192.168.1.54  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fe0d:48e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79806 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:128819796 (128.8 MB)  TX bytes:11684926 (11.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-DB-0D-48-E4-38-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Durden on 2009-07-22
wlan0 Link encap:Ethernet HWaddr 00:19:db:0d:48:e4
inet addr:192.168.1.54 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::219:dbff:fe0d:48e4/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:99495 errors:0 dropped:0 overruns:0 frame:0
TX packets:79806 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:128819796 (128.8 MB) TX bytes:11684926 (11.6 MB)

This one is your wireless, so at least we know it's functioning. Wait a while and see, could be the disconnects were just a fluke.

---

### Post by dk06 on 2009-07-22
> **lewstherin01 said:**
> Thanks for the help fella but it didn't help either lol.  It hasn't disconnected in a while so hopefully i'm past it!


Ok fella, here is some documentation ...just in case 

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by MarkTX on 2009-07-22
Hey Lewstherin01, i've been having those very same problems.  I could connect to my wireless router in Jaunty on one laptop but it would kick my other (Vista) laptop off the network.

I think they were fighting over the same IP for some reason, but when i tried to change that in Jaunty i must of messed something up because now i can't enable wireless at all.

I'm a beginner Linux user.  I have the drivers enabled for the card (Broadcom BCM4318 Airforce one type) and it has worked only a couple days ago, but now the "Wireless Networks" option is permanently greyed out.

ANY HELPERS?

---

### Post by lewstherin01 on 2009-07-22
Sounds bad dude.  Lucky there are plenty of helpful people on here.  :D  Don't think I have the same problem as you.  There is currently three laptops running in my house and my connection hasn't gone off in a long time now.

---

### Post by MarkTX on 2009-07-22
Ahh.  I have the two laptops and a wired pc (vista again).  Wish i could get it running smooth, i love what linux stands for and all the cool apps i've seen online for it.

I will endeavour and i will learn linux!!!

In the meantime, i appreciate allll the help i can get!!!


-EDIT

Oddness

So i connected my laptop via a wired connection so i could post here etc from the machine.  Now it seems my wireless is working again.  I have unplugged the network cable and am running through the router now.

Only problem is that my vista machine keeps dropping again now.

---

### Post by gigaferz on 2009-07-22
you can try goin to the routers web page and issue static dhcp  Ip to each computer,

I will not affect if you dual boot because the Ip address is given to a specific MAC address.

But it doesnt mean it will work.

And as for your wireless being all messed up, honestly i recommend backing up your pictures and videos or whatever and do a clean install . Also try doing an advanced installation this time, it works excellent for any future messups

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

i know it looks scary and confusing, but as you said youll have to learn.

so far you need a partition like this 
for /  about 8gig (root,is where your system goes)
for swapfile  1 gig  (this is a pagefile.sys in windows is memory)
for Home the rest of your hard drive , this means whatever happen to the system your files will be safe because they are in a "different" hard drive.

---

### Post by MarkTX on 2009-07-22
I don't plan on doing any dual booting on my ubuntu laptop, however looking at your tutorial it does make perfect sense to seperate ubuntu from personal documents, for cases of recovery etc.  I will probably give that a go here soon.

Thankfully i've only had Ubuntu installed since last weekend, so i don't have any personal items on it yet.

---

### Post by meeples on 2009-07-23
my wifi has a habit of disconnecing everytime i try to download a big file.

very frustrating because im trying to download the ubuntu iso to fix my other computer.

---

### Post by LewRockwell on 2009-07-23
I read through the four pages but must have missed where the wireless router was identified?

To that end, it must be noted that you'll be required to become familiar with your router and its settings.

I've picked up used routers where the DHCP lease time was set incorrectly

why anyone would want a one minute lease is beyond me

FWIW, 1440 minutes is a one day lease(which works fine for my needs)

.

---

### Post by Rockky on 2009-07-23
Well i face the problem of not able to connect to wi fi at all. I dont know if we need drivers for wifi or what do we need to change in internet proxy . I am using Linksys router and already running my vista on same laptop and xp on other

---

### Post by Rockky on 2009-07-23
Plz help me out

---

### Post by lewstherin01 on 2009-07-23
Mine disconnected again.  It seems a lot of people have the same problem.  Going to have to live with it until a solution is found.  :(

---

### Post by LewRockwell on 2009-07-23
> **Rockky said:**
> Well i face the problem of not able to connect to wi fi at all. I dont know if we need drivers for wifi or what do we need to change in internet proxy . I am using Linksys router and already running my vista on same laptop and xp on other

this is a separate trouble-call and should have a thread of it's own

.

---

### Post by LewRockwell on 2009-07-23
> **lewstherin01 said:**
> Mine disconnected again.  It seems a lot of people have the same problem.  Going to have to live with it until a solution is found.  :(

are you sure your router isn't overheating?

some brands and models are more prone to that than others of course

.

---

### Post by kdetech on 2009-07-23
If you are a beginner Kubuntu will be better for you (kubuntu.org) It has a better interface and a great network management utility. You can install it alongside ubuntu by installing kubuntu-desktop package. Chose KDM when prompted. Then restart click session type and chose kde.

---

### Post by lewstherin01 on 2009-07-23
My router is fine.  It's only in Ubuntu it disconnects.  I installed KNemo and now everytime it disconnects it reconnects a couple of seconds later so it's not so bad now.

---

