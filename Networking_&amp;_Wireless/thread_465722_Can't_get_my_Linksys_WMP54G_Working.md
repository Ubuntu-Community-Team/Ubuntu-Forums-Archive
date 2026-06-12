---
title: "Can't get my Linksys WMP54G Working"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by Stormweaver on 2007-06-06
Ok - I'll try to get all this info right the first time

**WARNING** I am having to input all this from my Laptop as the comp in question will not connect to the internet.

I just installed a Linksys WMP54G Wireless card in my Edgy 6.10 (with all the latest updates through Sat)

I choose that card as its Linksys and on the approved list as "out of the box".

While i can sometimes hit the network, I cannot connect to the internet at all.  I have both the serialmonkey.com driver and the synaptic package for RT2500 (thats what came back with ifconfig) installed - Doing this got the card to be seen as a G card instead of a B card.  But none the less I still cannot see the net.


```


This is iwconfig

ra0       RT2500 Wireless  ESSID:"default"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-120 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

This is ifconfig


ra0       Link encap:Ethernet  HWaddr 00:12:17:8B:C3:AD  
          inet6 addr: fe80::212:17ff:fe8b:c3ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:487708 (476.2 KiB)
          Interrupt:74 Base address:0x4000 




 
```


Aight guys, tell me what more you need, or whats up -- I am away from home by many hours, with wireless  my only access.  I feel a little lost without my linux box connected.  If you need something done out in terminal, tell me the command and tags for it and I will run it and type the response here.

I'll be checking this every couple of hours.

Thank you to all who help in advance!


Stormweaver

EDIT 1: Put the stuff from terminal in Code tags to make readable

---

### Post by weblordpepe on 2007-06-06
One very odd thing I have noticed is that Ubuntu 6.10 has some kinda networking issue.
I and two others have had an interesting experience with the LAN connection just not connecting to the internet, even though all settings are correct.

We couldn't resolve the issue, and it only started spontaniously after 7.04 was released. Upgrading to 7.04 fixed it.
Dunno if that helps, dude! :D

---

### Post by Stormweaver on 2007-06-09
I don't know that I could upgrade and still have everything working right... Thats what worries me, I use Wine to Play World of Warcraft and I am still trying to get this box set up the way I want.... The idea of upgrading and having it all go to pot right now worries me.  If no one else has an idea, as its been 2 days since a reply other then 1, I guess I will look into the upgrade... Assuming I can get the software to the comp while I am on the road.. Otherwise I will spend all of this trip without access to my machine to do things.  I don't know where to go from here.

Stormweaver

---

### Post by stevo1977 on 2007-06-30
some good tips here.  one really frustrating thing for me is that because of these issues i have no access to the internet while i'm in ubuntu (one excellent thing about having xp still on my system), so i can't get any synaptic packages that people recommend would help.  is there a way that i can dowload the .deb version of a package (specifically the one for the rt2500 chipset) in windows and then transfer it over to ubuntu manually?

on a side note, i went back and installed 6.06 (i won't go into all the reasons).  when i get the network up and running, will updates and packages get me up to date, or would you guys recommend that i just scrap it and get the newest release?

---

### Post by weblordpepe on 2007-06-30
Oh just jump right into 7.04, dude. Its much cooler. Things are much easier to install and its driver support is better. It has a new networking applet thingie as well which makes wifi/network selection easy peasy weasy pants.

Why dont you have internet in Ubuntu? Ya heard about NDISwrapper?

---

### Post by stevo1977 on 2007-06-30
yeah, i tried to use ndiswrapper, but i can't find the drivers that windows is using for my wireless card.  and wireless is my only option in the house where my computer is (ethernet cables are only so long).

you're right.  i'll just get 7.04 and reinstall.  thanks for the reply.

stevo

---

### Post by weblordpepe on 2007-07-01
Maybe someone else on the forums has the same wifi adapter. Many people report wifi problems in linux.

---

### Post by bikeboy on 2007-07-01
Hi Stormweaver,

I am surprised your card isn't working in Edgy, but in Feisty it's a little tricky to get going. What I've learnt from that might help here.

Firstly, refresh my memory, does Edgy have NetworkManager installed by default?

---

### Post by kevdog on 2007-07-01
Lets really check the chipset of the device:

Please list the output of the following:
lspci

Also lets see what driver is currently associated with your card:
lshw -C network

And please post the following file:
/etc/modprobe.d/blacklist

Thanks

---

### Post by database_dan on 2007-07-01
you dont need the serial monkey drivers
you dont need Synaptic's drivers for RT2500
you dont need ndiswrapper
 
i have this card, and it works out of the box with no problems in Feisty. I had no luck getting it to work in Edgy. and besides, Feisty is waay better than Edgy in all regards.

But just in case...
See also: [http://ubuntuforums.org/showthread.php?t=434952](http://ubuntuforums.org/showthread.php?t=434952)
See also: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Good Luck,
~Dan

---

### Post by Tprice on 2007-07-01
If any one could get a fix to this problem it would help out a lot!

thanks!

---

### Post by stevo1977 on 2007-07-01
okay, so i've got 7.04 installed now and it recognizes the card immediately and offers me the local networks to choose from.  however, it won't connect to any of them.  i click on the one that i want and put in the encryption key, and then those circles just keep chasing each other, and when i hover over them it says "waiting for network encryption key' and then gives up after a few seconds.  any help would be greatly appreciated.

Results of 'unmame -a':
Linux 2.6.20-15-generic #2 SMP UTC 2007 x86_64 GNU/Linux

(i'm running this on an amd64 2400 processor.)

**Results of 'lspci':

00:0b.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
(rev a1)


**Results of 'lshw -C network':

  *-network:0
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: b
       bus info: pci@00:0b.0
       logical name: ra0
       version: 01
       serial: 00:14:bf:77:a2:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=32 link=yes multicast=yes wireless=RT2500 Wireless
       resources: iomemory:fb010000-fb011fff irq:19
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@00:0d.0
       logical name: eth0
       version: 10
       serial: 00:04:61:a9:64:5e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:d000-d0ff iomemory:fb013000-fb0130ff irq:19

**Contents of 'modprobe.d/blacklist':

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

---

### Post by database_dan on 2007-07-01
is the network WPA or WEP encrypted? If WEP did you select WEP Key (hexadecimal)?

> **stevo1977 said:**
> okay, so i've got 7.04 installed now and it recognizes the card immediately and offers me the local networks to choose from.  however, it won't connect to any of them.  i click on the one that i want and put in the encryption key, and then those circles just keep chasing each other, and when i hover over them it says "waiting for network encryption key' and then gives up after a few seconds.  any help would be greatly appreciated.

Results of 'unmame -a':
Linux 2.6.20-15-generic #2 SMP UTC 2007 x86_64 GNU/Linux

(i'm running this on an amd64 2400 processor.)

**Results of 'lspci':

00:0b.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
(rev a1)


**Results of 'lshw -C network':

  *-network:0
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: b
       bus info: pci@00:0b.0
       logical name: ra0
       version: 01
       serial: 00:14:bf:77:a2:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=32 link=yes multicast=yes wireless=RT2500 Wireless
       resources: iomemory:fb010000-fb011fff irq:19
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@00:0d.0
       logical name: eth0
       version: 10
       serial: 00:04:61:a9:64:5e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:d000-d0ff iomemory:fb013000-fb0130ff irq:19

**Contents of 'modprobe.d/blacklist':

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

---

### Post by bikeboy on 2007-07-01
Not sure if there are any issues with 64bit and rt2500, so if there is this won't help.

Currently, rt2x00 and NetworkManager don't work together.
What I do to get my rt2500 working after a fresh Feisty install is open up a terminal (Applications > Accessories > Terminal:
```

ifconfig ra0 down
iwconfig ra0 essid "your essid here"
ifconfig ra0 up
dhclient3 ra0

```
That is with encryption  turned off (don't need it where I am). If that works for you, NetworkManager can be removed and we can give you instructions for making sure the connection is made at boot time, so you never have to enter those commands again.

The good news is, the next version of Ubuntu (due in October) has new drivers for these cards, there was a mistake in the current alpha, but I installed the drivers myself (easy to do) and it worked with NetworkManager 100% fine.

---

### Post by stevo1977 on 2007-07-02
database_dan,

  yeah, the network is wep encrypted (which seems to be easier to work with, from what i've read so far), and that is what i select from the choices network manager gives me (WEP hex).  still no go.

bikeboy,

  unfortunately, the network i'm trying to get on is encrypted.  do you think it's a problem with the driver that ubuntu is using?  should i install other drivers?  by the by, i tried what you suggested anyway, and it said:
"No DHCPOFFERS received.
No working leases in persistent database - sleeping."

thanks, all, for the replies so far.  i really do appreciate it.  i am very anxious to get this going so that i can really start getting into linux.  i feel like i'm pretty competent when it comes to computers and stuff, but i don't know jack about networking.  i'm pretty spoiled on windows' automation in that department.

p.s.  this doesn't have anything to do with wireless cards, but ubuntu always loads up with the screen shifted about 20 pixels to the right.  is there a reason for that?

---

### Post by database_dan on 2007-07-02
now that i think about it, you are running 64 bit ubuntu on a 64 bit cpu right? i think the 64 bit install might be the problem. my roommate uninstalled his 64 bit in favor of the 32 version, he has never been happier. i am not saying this is 100% the problem, but there seems to be some short comings for 64 bit ubuntu. i would highly recommend setting up a another partition to test a 32 bit install.

is this your router? if its a public router, then perhaps they have MAC address filtering on?

if it is your router then i would turn off WEP and just try to connect on an open network period. then add WEP into the equation. as far as the hex key will be 10 characters long if it is 64 bit crypto or 26 characters if 128 bit crypto....are you entering the correct key?

it looks like you have the same card, chipset, and even revision as me. i couldn't get this RUtil to work, but perhaps you will have better luck, worth a shot...
[http://ubuntuforums.org/showthread.php?t=434952](http://ubuntuforums.org/showthread.php?t=434952)

> **stevo1977 said:**
> database_dan,

  yeah, the network is wep encrypted (which seems to be easier to work with, from what i've read so far), and that is what i select from the choices network manager gives me (WEP hex).  still no go.

bikeboy,

  unfortunately, the network i'm trying to get on is encrypted.  do you think it's a problem with the driver that ubuntu is using?  should i install other drivers?  by the by, i tried what you suggested anyway, and it said:
"No DHCPOFFERS received.
No working leases in persistent database - sleeping."

thanks, all, for the replies so far.  i really do appreciate it.  i am very anxious to get this going so that i can really start getting into linux.  i feel like i'm pretty competent when it comes to computers and stuff, but i don't know jack about networking.  i'm pretty spoiled on windows' automation in that department.

---

### Post by stevo1977 on 2007-07-02
dan,

funny thing, i actually installed my 64bit ubuntu over the original 32bit install because of this very problem.  so i don't think that switching back is going to solve anything.  and unfortunately, this is not my router, it's belongs to the guy who owns the house i live in.  but i'm using the same key that worked fine in windows and on this mac laptop that i'm using now, so i don't think that's the problem either.  am i missing something, or was the forum you linked to detailing how to set up a WPA encryption?

> **database_dan said:**
> now that i think about it, you are running 64 bit ubuntu on a 64 bit cpu right? i think the 64 bit install might be the problem. my roommate uninstalled his 64 bit in favor of the 32 version, he has never been happier. i am not saying this is 100% the problem, but there seems to be some short comings for 64 bit ubuntu. i would highly recommend setting up a another partition to test a 32 bit install.

is this your router? if its a public router, then perhaps they have MAC address filtering on?

if it is your router then i would turn off WEP and just try to connect on an open network period. then add WEP into the equation. as far as the hex key will be 10 characters long if it is 64 bit crypto or 26 characters if 128 bit crypto....are you entering the correct key?

it looks like you have the same card, chipset, and even revision as me. i couldn't get this RUtil to work, but perhaps you will have better luck, worth a shot...
[http://ubuntuforums.org/showthread.php?t=434952](http://ubuntuforums.org/showthread.php?t=434952)

*edit* i've been reading around elsewhere, and i'm going to try and uninstall network manager and install wicd.  i'll let you know if there are any fruits to report. *edit*

---

### Post by bikeboy on 2007-07-02
> **stevo1977 said:**
> database_dan,
bikeboy,

  unfortunately, the network i'm trying to get on is encrypted.  do you think it's a problem with the driver that ubuntu is using?  should i install other drivers?

That's ok, the instructions I gave still apply, you just need one other step to set the WEP key. Unfortunately, since I don't use WEP I can't remember what it is :(

I will have a look to find what it is that you need to add.

edit:
Ok try this. After the part about essid, enter this command:
```
wireless-key abcdef01234567890
```
The key has to either be the hexadecimal version or s:thewepkey

---

### Post by stevo1977 on 2007-07-02
bikeboy,

  hey, it works!  the only thing is that the line i needed to add was:
iwconfig ra0 key "abcdefghij"
since wireless-key' wasn't recognized.  does this mean that network manager will work?  or will this fix only work until the next restart?  if you have a bit of time and the inclination, i'd love it if you could maybe explain what it is we did, or point me to somewhere that would explain it.

thank you so much for your help and patience.  i really appreciate it.

> **bikeboy said:**
> That's ok, the instructions I gave still apply, you just need one other step to set the WEP key. Unfortunately, since I don't use WEP I can't remember what it is :(

I will have a look to find what it is that you need to add.

edit:
Ok try this. After the part about essid, enter this command:
```
wireless-key abcdef01234567890
```
The key has to either be the hexadecimal version or s:thewepkey

---

### Post by bikeboy on 2007-07-02
Ah sorry about that, glad you were able to work it out from there though, well done! The wireless-key part was just a mistake on my part, "iwconfig ra0 key" was correct.

At this stage, you won't be able to use Network Manager, simply because the drivers don't support it (Ubuntu 7.10 should), but there most certainly is a way to make sure the connection is there at boot every time, so you don't have to do anything to get onto the network.

Alt+F2 > gedit > put in all those commands, without the sudo. It will look something like this:
```
#!/bin/dash
ifconfig ra0 down
iwconfig ra0 essid "your essid"
iwconfig ra0 key "abcdefghij"
ifconfig ra0 up
dhclient3 ra0

```

Save the file in your home folder as .wireless-up or something like that. The . makes it hidden so it's out of the way, ctrl+H in the file manager will show it again. Now, you just make a link to that file in the initialisation scripts that run during boot up.

```

cd /etc/rc2.d/
sudo ln -s /home/stevo1977/.wireless-up ./S14wireless-up

```

Where I put "stevo1977" should be your actual username, and I have presumed .wireless-up is just in your home directory, not a sub-directory. Now you could just reboot, but entering 'sudo /etc/init.d/networking restart'  should apply the changes without doing that.

One more important thing, the instructions I just gave are a bit insecure. Because you can simply edit the /home/stevo1977/.wireless-up file, you could make anything run at boot time. If someone compromised your system, they could take advantage of this. There is an alternative, that takes away a bit of convenience if you want to change your WEP key or essid regularly.

For better security, put the wireless-up file in /etc/init.d/
To create/modify the file you would enter:
```
gksudo gedit /etc/init.d/wireless-up
```
It will be owned by root rather than yourself, so to maliciously edit the file someone would need root access. If it got to that stage, you would have greater things to worry about :P

---

### Post by stevo1977 on 2007-07-03
awesome.  thanks so much, bikeboy.  i'm out of town right now, but i'll let you know how the implementation goes as soon as i can try it.  i really appreciate all your help.  thanks, too, for the thorough explanation; you're also helping me deal with future hiccups.

stevo1977

---

### Post by ubanchaos on 2007-07-05
well im real new to linux and i got a wmp54g linksys pci adapter and i wont connect to fiesty fawn i looks like this happend to alot of people does anyone kno how to fix it

---

### Post by bikeboy on 2007-07-05
Hi ubanchaos, there is (I think) more than one hardware revision of the wmp54g, so one guide won't necessarily work for them all. We need to know the exact chipset your wireless card uses. For that, the quickest way is for you to open up a terminal with Applications > Accessories > Terminal. Then copy and paste this into there.
```
lspci
```
Copy and paste the results into the forum here or a pastebin and we will be able to see.

If it turns out you have a Ralink rt2500 or similar, I have [written about it in depth](http://www.vickersf.dyndns.org:8080/blog/2007/07/03/howto-ralink-ubuntu-feisty/) on my site now. Should be able to copy & paste for most of it.

Stevo1977, please do let us know how it went when you get the chance, hope it all works well now.

---

