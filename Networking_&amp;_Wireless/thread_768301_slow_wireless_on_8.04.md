---
title: "slow wireless on 8.04"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by corneel on 2008-04-26
Why is my wireless slow on 8.04? It has always worked good on Ubuntu. I have a linksys wireless on this desktop. My wireless on a HP laptop works good on ubuntu 8.04.

It's a (Linksys) Ralink RT 2500 G 802.11 and the same computer on windows partition and 7.04 partition it works well.

My Linksys wireless usb netwerk works wel on 8.04 (the one now in use to send this message)

---

### Post by TheHoff on 2008-04-26
I'd like to add that I'm having the exact same problem. I upgraded to 8.04 (fresh install, actually) and my RT2500 is very slow. (~10k/sec). My network quality thing is always at about 40%, whereas it used to be around 100% (the location of my machine and router have not changed, of course).

-- John

---

### Post by macafyc on 2008-04-26
Hello

I had the same problem. That's because the bit rate is set to 1 Mb/s

Type iwconfig. If you see in your wireless interface Bit Rate 1 Mb/s type sudo iwconfig xxxxxx rate 54M

xxxxxx should be the name of your wireless interface

---

### Post by Rohaq on 2008-04-26
> **macafyc said:**
> Hello

I had the same problem. That's because the bit rate is set to 1 Mb/s

Type iwconfig. If you see in your wireless interface Bit Rate 1 Mb/s type sudo iwconfig xxxxxx rate 54M

xxxxxx should be the name of your wireless interface

Same issue here, RT2500 chipset network adapter. Above fix seems to work for me, but network manager is still reporting my signal fluctuating wildly. Used to get 74% signal, now drops into the 30s, then shoots back up again.

Gutsy had no problems whatsoever.

---

### Post by egwest on 2008-04-26
I was getting the same slow problem, the fix seemed to help that, but I use to have a 80%-90% signal strength, now I am bouncing between 30% and 60%.

---

### Post by uk1320 on 2008-04-26
Same problem here - RT2500 based Linksys router. Very slow, reports a 1mb/s connection, and a weak signal - pre update I had a 100% signal. PC and router are inches apart! I'll try the iwconfig fix and report back later (typing this on a Mac at the moment, from a different location).

---

### Post by uk1320 on 2008-04-26
OK, it kind of works....

I entered the iwconfig commands and although it still showed the connection as 1mb/s it ran at it's normal high speed pace. Looked like problem solved.

But, when I rebooted, it went back to the very, very slow pace. Re-entering the iwconfig commands speeded it up again.

Is there a way to make the change permanent so I don't have to enter the iwconfig commands after every reboot?

---

### Post by TheHoff on 2008-04-26
Yep, changing the rate to 54M fixed it. Thanks!

---

### Post by linuxpower on 2008-04-26
Hello,

i have the same Problem, but your Solution doesn't work.

For have 54M from beginning you can add **pre-up iwconfig wlan0 rate 54M ** in **/etc/network/interfaces** and then restart your wireless by **sudo /etc/init.d/networking** restart. Then your wireless should work from beginning with full speed. 

Do you use WPA or WEP? I only can use this solution with WEP. With WPA it doesn't work.

There is also a bug report [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660")

greets
linuxpower

---

### Post by egwest on 2008-04-27
> **linuxpower said:**
> Hello,

i have the same Problem, but your Solution doesn't work.

For have 54M from beginning you can add **pre-up iwconfig wlan0 rate 54M ** in **/etc/network/interfaces** and then restart your wireless by **sudo /etc/init.d/networking** restart. Then your wireless should work from beginning with full speed. 

Do you use WPA or WEP? I only can use this solution with WEP. With WPA it doesn't work.

There is also a bug report [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660")

greets
linuxpower


Thanks! This worked a lot better, it actually slightly boosted my signal strength.
Though the signal strength is still bouncing up and down, it now goes from 55% up to 85% instead of 30% to 60%.

Hopefully there is a fix for that soon.

Thanks again!

---

### Post by TVRTim on 2008-04-27
I have a Ralink RT2500 internal and I am trying to follow the instructions above. iwconfig shows my rate to be set to 1mb so I entered 'sudo iwconfig RT2500 rate 54M' but am told that there is no such device. 
As you can proberbly tell I am quite new to the whole linux world so any help that uses simple commands would be much appreciated.

Tim

---

### Post by uk1320 on 2008-04-27
**linuxpower** was asking about WPA or WEP - I'm using WPA.

**tvrtim** - instead of rt2500 use whatever address the iwconfig command says is your wireless unit. In my case it's RA0. So in my case the command is **sudo iwconfig RA0 rate 54M**

---

### Post by ogregore on 2008-04-27
Tim,

Try sudo iwconfig wlan0 rate 54M

Cheers
Ogre

---

### Post by linuxpower on 2008-04-27
Well, here it first doesn't work with WPA, but now its works. I don't know why, but today its just working.

I heard that it maybe could be better if you choose 36M instead of 54M. Here I have full speed with 54M, but I only use it for internet with DSL 6000 and I don't know how fast it would be if I would send something inside my Network.

---

### Post by TVRTim on 2008-04-29
Thanks a lot guys. It turned out to be wlan0. 

Tim

---

### Post by corneel on 2008-04-29
This Ubuntu suprise is the last suprise for me. On every update there are some problems with Ubunty. I now have Freespire on my computer and if this works for me I buy Linspire. I do not like to be a testuser for Ubuntu. When I pay for a distro I can complain if there are troubles. Bye Ubuntu!

Thanks all

---

### Post by Rohaq on 2008-04-29
> **corneel said:**
> This Ubuntu suprise is the last suprise for my. On every update there are some problems with Ubunty. I now have Freespire on my computer and if this works for me I buy Linspire. I do not like to be a testuser for Ubuntu. When I pay for a distro I can complain if there are troubles. Bye Ubuntu!
Nobody cares.

Seriously, there should be a rule banning people for posting useless statements like this.

---

### Post by corneel on 2008-04-29
> **Rohaq said:**
> Nobody cares.

Yes, this are real Ubuntu people...

---

### Post by unMourned on 2008-04-29
Replying to the speed issue.  I ought to have posted this in the 'Networking & Wireless' forum.  Oops.

Hardy Heron, bcm4318 comparison to xp drivers:

> **unMourned said:**
> Disclaimer:  Tests taken roughly 15m apart.  Things happened, and I couldn't immediately reboot to Ubuntu to run the test as closely as possible to the XP run.

Nevertheless, what the graphics below show is that, despite the fact that Hardy Heron shows my bcm4318 card at 1Mb/s, real world speed is comparable (_or is it_?) to XP.  Testing to NYC is 204 miles, according to [http://www.dslreports.com/speedtest?java=1](http://www.dslreports.com/speedtest?java=1), and testing to the NYC site has generally shown better results than the New Jersey site (which is 182 miles, by comparison).

XP:
[IMG]http://www.dslreports.com/im/50002312/34248.png[/IMG]

Ubuntu:
[IMG]http://www.dslreports.com/im/50003068/96995.png[/IMG]

Deltas (Ubuntu/XP):
Down:  81.2%
Up:    47.0%

It'll likely take a pool of tests to create a solid average and standard deviation--but this is a start.

-Paul

By the way, this is outta the box (b43-fwcutter) solution [here]("http://ubuntuforums.org/showthread.php?t=769603").

I've not yet tried to tweak speed/strength, but after reading of the results in this thread, will try today.

Thanks for the great support!

-Paul

---

### Post by unMourned on 2008-04-29
XP test2
[IMG]http://www.dslreports.com/im/50012874/64165.png[/IMG]

Ubuntu test2
[IMG]http://www.dslreports.com/im/50024767/69356.png[/IMG]

Interesting that the second Ubuntu test (still at 1Mb/s) approaches the XP results, both up and down.  

Deltas, again (Ubuntu / XP):
Down:  93.2%
Up:    96.7%

I realize the two tests are several hours apart--I'll get this right, eventually.

On another note, I could not get the [sudo iwconfig wlan0 rate 54M] command to work.  As soon as I set that, I lost wireless.  I tried 36M, too.  I enabled WEP also, no no avail.  Running open wireless now is my only option for connecting to bcm4318. :(

Also, if nobody is interested in the bcm4318 versus xp tests, let me know...or if you would like to see more of this, let me know, too.

-Paul

---

### Post by mrblonde1369 on 2008-04-29
many thanks, the "iwconfig rate 54M" trick worked well (or at least, it really seems so!) on my newly upgraded Kubuntu 8.04

this is my first post, have been a Kubuntu user for more than 6 months right now and these forums have been more than useful for my journey into the linux world!

---

### Post by arandall on 2008-04-29
the iwconfig trick isn't working - do you know of anything else I could do?

---

### Post by backupdevice on 2008-05-02
For me it works, is there a way to make it permanent? Because with me the speed goes up and down.  For a long time it goes normal speed, and then it fals back to 30kb....

---

### Post by colsandurz on 2008-05-02
I was having the same problem, and I use the iwconfig trick just fine... it's just that I have to run the command every time I reboot.  Can I write a start-up script that will run the command every time or is there some tpye wlan0.config that I can edit to change this?

EDIT:
Can I do this by changing /etc/network/interfaces?

---

### Post by Rohaq on 2008-05-03
> **colsandurz said:**
> I was having the same problem, and I use the iwconfig trick just fine... it's just that I have to run the command every time I reboot.  Can I write a start-up script that will run the command every time or is there some tpye wlan0.config that I can edit to change this?

EDIT:
Can I do this by changing /etc/network/interfaces?

Add ```
pre-up iwconfig wlan0 rate 54M
``` to */etc/network/interfaces* then run ```
sudo /etc/init.d/networking restart
``` to restart your network interfaces, this should run the command on startup of your network interfaces.

---

### Post by norwegianblue on 2008-05-03
I've been experiencing similar problems with my Comtrend RT2500 card. Even after using *iwconfig ra0 rate 54M* speed and signal strength were fluctuating wildly, to the extent that the connection sometimes drops altogether. This, I could just about cope with, but this morning I went back to a wired connection to perform some large downloads and suddenly the quality problems we'd been having with our WiFi telephone disappeared altogether.

So I'll stick with the wired connection until theres a proper solution to this problem.

---

### Post by Fenris_rising on 2008-05-03
hi all  i to had this problem infact only just found out after reading this post. i have done the direct change but i cant seem to get into the /etc/network/interfaces to add the fix. i can find the interfaces document but am unable to save it when i edit it with gedit. as i am not root. can someone tell me how to approach this in the correct manner. im running HH 8.04.

regards

fenris

---

### Post by norwegianblue on 2008-05-03
> **norwegianblue said:**
> I've been experiencing similar problems with my Comtrend RT2500 card. Even after using *iwconfig ra0 rate 54M* speed and signal strength were fluctuating wildly, to the extent that the connection sometimes drops altogether. This, I could just about cope with, but this morning I went back to a wired connection to perform some large downloads and suddenly the quality problems we'd been having with our WiFi telephone disappeared altogether.

So I'll stick with the wired connection until theres a proper solution to this problem.

I've just tried the ndiswrapper solution and it's worked perfectly.

---

### Post by Rohaq on 2008-05-03
> **Fenris_rising said:**
> hi all  i to had this problem infact only just found out after reading this post. i have done the direct change but i cant seem to get into the /etc/network/interfaces to add the fix. i can find the interfaces document but am unable to save it when i edit it with gedit. as i am not root. can someone tell me how to approach this in the correct manner. im running HH 8.04.

regards

fenris

Press Alt + F2 to bring up the 'Run' window, type "gksudo gedit" (no quotes) and enter your password.

Still really disappointed at this: New kernels are great and all, but there should be some kind of way to switch to the method Gutsy was using if we want to, since that seemed to work without a hitch.

---

### Post by Fenris_rising on 2008-05-03
cheers for that rohaq. ive noted that for future reference. i have gone the ndiswrapper way with blacklist to. worked like a charm nice one norwegianblue, i should have tried it first i had already used it on my laptop to get my usb wireless adatper going........it has to be said this community rocks!!!!!!!!!

regards

Fenris

---

### Post by corneel on 2008-05-03
I do not use 8.04 anymore. I'm back to 7.10 till I find a distro without so many bugs. This bug is known for weeks and weeks. Nobody on Canonical is interested for this bug. I find this the most stupid bug in history of Ubuntu.

'Slow wireless' is the most written thread on the forum.

---

### Post by unMourned on 2008-05-04
[IMG]http://www.dslreports.com/im/50319549/3.png[/IMG]

That's darn near what I get testing with XP.

And my Wireless Network Connection shows 1Mb/s.

It doesn't perform as slowly as it shows.

-Paul


Edit:

Here's a test down to Miami, FL:

[IMG]http://www.dslreports.com/im/50319771/2982.png[/IMG]

---

### Post by BBirdtree on 2008-08-28
Thanks:popcorn:

---

### Post by kidcharles on 2008-08-31
I had this problem too and was able to fix it with the iwconfig command. Okay, now here's a question: why does this bug exist? Why is the default setting 1M?

---

### Post by jammin2222 on 2008-09-20
> **Rohaq said:**
> Add ```
pre-up iwconfig wlan0 rate 54M
``` to */etc/network/interfaces* then run ```
sudo /etc/init.d/networking restart
``` to restart your network interfaces, this should run the command on startup of your network interfaces.

could you elaborate on how to put this into the network interfaces folder? i don't know how to add a command to a folder. using the terminal. a step by step guide would be great :) Total newbie here :(  sorry 

Thanks

Ben

---

### Post by mgmiller on 2008-09-25
Open a terminal....  Applications > Accessories > Terminal

Enter the following command...
```
gksu gedit  /etc/network/interfaces
```Give it your normal login password when prompted.

Enter the following as the last line of text...
```
pre-up iwconfig wlan0 rate 54M
``` Click save in the upper left corner.

Close gedit, leave the terminal open.

Enter the following command in the terminal to restart your networking...
```
sudo /etc/init.d/networking restart
```Close the terminal
That should do it.

---

### Post by nicole13 on 2008-09-30
That worked really well for me! :D

---

### Post by doctorj on 2008-09-30
Thanks. Works well.

---

### Post by bilbobaggans on 2008-09-30
Hi Guys,

That didn't work here either.  When I run iwconfig I don't get 1M I get 11M which should be enough:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"HomeNetwork"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:00:C5:FA:89:58   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=100/100  Signal level=-51 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

And no change after running sudo iwconfig wlan0 rate 50M

My signal strength looks good but I only get .5Mb when I do an online bandwidth test.

My net info is as follows:

  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:9a:70:43
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.43 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

Logical name is reported as wmaster0 but wlan0 seems to be the interface I'm using it that a problem?

Thanks...

---

### Post by bilbobaggans on 2008-10-03
Hi,

I found the solution here -> [http://intellinuxwireless.org/bugzilla/show_bug.cgi?id=1669](http://intellinuxwireless.org/bugzilla/show_bug.cgi?id=1669)

iwconfig wlan0 power off

Got me back some of my bandwidth, I get about 4Mb I should get 5Mb but it is better than 0.5Mb :D

They also recommended:

echo "Turning off power mgmt..."
iwconfig wlan0 power off
echo "Setting Tx power to 0dBm..."
iwconfig wlan0 txpower 0

which didn't do much for my system but it may work for others.

Cheers....

---

### Post by TutonicMonkey on 2008-11-19
This worked for me on 8.10 when my rt2500 was stuck at 1mbs 40% ish range
Nic: rt2500pci


sudo iwconfig wlan0 rate 54M

then restart connection


-now im at 54mbs with 70%ish range
Man this was driving me nuts!!!

Thnx :)

---

### Post by citrusheightskid on 2009-01-17
I'm having issues with slow internet speed as well. I have a Netgear WG311v3 PCI card installed and its working fine however, I'm only getting a 1MB bit rate. When I've had this installed on XP Pro, I've always had a strong connection. Btw, my router is a Linksys WRT150N.

here's my settings for iwconfig:

erik@erik-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"thisbitch2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:7E:D9:20:97   
          Bit Rate=2 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I've tried the sudo iwconfig wlan0 rate 54M and that isn't working. Any clues or ideas would be awesome! And yes, I'm new to this stuff.

---

### Post by neoroses on 2009-01-20
mine was alredy set to 54 mbps :( so that fix didnt work, any ideas?

---

### Post by ls8 on 2009-02-11
unfortunately this is still not fixed in 8.10 intrepid:(

---

### Post by edwardTheGreat on 2009-02-12
> **linuxpower said:**
> Hello,

i have the same Problem, but your Solution doesn't work.

For have 54M from beginning you can add **pre-up iwconfig wlan0 rate 54M ** in **/etc/network/interfaces** and then restart your wireless by **sudo /etc/init.d/networking** restart. Then your wireless should work from beginning with full speed. 

Do you use WPA or WEP? I only can use this solution with WEP. With WPA it doesn't work.

There is also a bug report [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660")

greets
linuxpower

Just letting everyone know this worked for me on my pc with 8.10 using WPA, it brought my rate back up to 54 Mb/s:KS

I have a linksys RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

---

### Post by ls8 on 2009-02-13
Permanent solution for Ubuntu Intrepid Ibex 8.10:

Create a new file /etc/network/if-up.d/wlan-54m, chmod it to 755.

```

#! /bin/sh
# Description:       Set the connection speed of WiFi card to 54m

iwconfig wlan0 rate 54M

```

and restart network

---

### Post by uk1320 on 2009-04-26
Still the same problems on Ubuntu 9.04 - this is really disappointing. How difficult can it be to get the fix implemented?

---

### Post by AJB2K3 on 2009-04-26
Thanks guys the rate54M word for my broad com AF1 card as well.

---

### Post by uk1320 on 2009-04-26
My interfaces file is now as below.


auto lo
iface lo inet loopback


#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


auto eth0

pre-up iwconfig wlan0 rate 54M





When I do the network restart it says:

 * Reconfiguring network interfaces...                                             /etc/network/interfaces:22: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:22: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                            [fail]

---

### Post by khaledkammar on 2009-10-23
sudo iwconfig wlan0 rate 54M 

didn't work for me ! I really searched a lot but could't find anything that works!

---

