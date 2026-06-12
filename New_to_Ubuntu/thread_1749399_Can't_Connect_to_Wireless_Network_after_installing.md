---
title: "Can't Connect to Wireless Network after installing 11.04 - Major Help Needed"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by NonStop on 2011-05-04
I thought I had fixed this, but it turns out I haven't, my wireless is definitely on; there is a button on the side of the laptop, and if I press it wireless turns off, and vice versa.

My wireless internet was working fine for my laptop which had 10.10 installed. But I have just upgraded to 11.04, and I can't connect to my network.

For starters, the network is listed under Connect to hidden wireless networks, and if I try and connect it takes ages and ages, before coming up with a password prompt. I enter in the same password (it hasn't changed), and again it takes ages and ages, before the same password prompt.

It thus refuses to connect to the network, instead continuously prompting for a password, even though under Edit connections, the original password that i keep re-typing is entered in there!

Any help please?

EDIT: I deleted my two auto connects under edit connections in the hope that would do something, but nothing. It just didn't picking up my wireless connection at all. One in every 50 goes it might randomly pick it up. But the rest of the time, nothing. So disappointing, and I really need this to be fixed.

I REALLY need this fixed.

---

### Post by _0R10N on 2011-05-04
I had pretty much the same problem with ubuntu 9.10. I made a fresh install of 11.04 a couple of days ago and it doesn't happen anymore (at least that's what it seems). Let me guess, you have a broadcom adapter.If so, then each time you have this problem you must disable networking and enable it back.

It's so annoying and I haven't found a solution so far.

---

### Post by NonStop on 2011-05-04
I don't know what adaptor I have, how would I find it out?

I deleted my two auto connects under edit connections in the hope that would do something, but nothing. It just didn't picking up my wireless connection at all. One in every 50 goes it might randomly pick it up. But the rest of the time, nothing. So disappointing, and I really need this to be fixed.

EDIT: All I know is the machine giving off the wireless has Thomson written on it (I'm sucha newb). Any help?

---

### Post by beew on 2011-05-04
> **NonStop said:**
> I don't know what adaptor I have, how would I find it out?



Try the command 
```
  lshw -C network
```

Post the output.

---

### Post by NonStop on 2011-05-04
I'm very much the newb, so where do I go to do this? And do I literally write that command in and press enter? 

I'll have to copy the text and save it to my usb as I'm using the downstairs XP computer at the moment.

---

### Post by halibaitor on 2011-05-04
> **NonStop said:**
> I'm very much the newb, so where do I go to do this? And do I literally write that command in and press enter? 

I'll have to copy the text and save it to my usb as I'm using the downstairs XP computer at the moment.

Click on Applications/ Accessories/ Terminal

Then type the command into the terminal and see the result...

---

### Post by fremantle on 2011-05-04
hy

can you go to software center and install wifi radar? the same thing happened to me in 10.10. It could be an issue with net work manager, coz when i used wifi-radar, i was able to easily connect to networks.

if wifi-radar doesnt work, try with wicd.

---

### Post by NonStop on 2011-05-05
> **halibaitor said:**
> Click on Applications/ Accessories/ Terminal

Then type the command into the terminal and see the result...

Sorry for the late reply, here it is. To the others, I don't have internet access, I can't get wired internet either, so i can't download anything.

ian@ian-laptop:~$ lshw -C network

WARNING: you should run this program as super-user.

PCI (sysfs)  



  *-network               

       description: Wireless interface

       product: AR2413 802.11bg NIC

       vendor: Atheros Communications Inc.

       physical id: 5

       bus info: pci@0000:04:05.0

       logical name: wlan0

       version: 01

       serial: 00:19:7e:57:9e:45

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg

       resources: irq:19 memory:c3000000-c300ffff

WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by computerandu on 2011-05-05
Hi,

Was wireless connected when you were installing Ubuntu 11.04?

Did it ask you to download additional driver Broadcom STA?

Its a very common problem with Broadcom network adapter. 

Here is what you need to do. Use other  Broadcom drivers. Download these  drivers (from Windows or through wired  network or a friend’s computer  or from wherever you are reading this  article [IMG]http://s0.wp.com/wp-includes/images/smilies/icon_smile.gif?m=1300809663g[/IMG]  ). Install these instead of the one provided by Ubuntu 11.04. For 32 bit: [http://ie.archive.ubuntu.com/ubuntu/...untu5_i386.deb]("http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb")
 For 64 bit: [http://ie.archive.ubuntu.com/ubuntu/...ntu5_amd64.deb]("http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb")
 Now remove the previous drivers using: *sudo apt-get remove bcmwl-kernel-source*
 Now install the appropriate driver.  Restart your computer. If  restarting doesn’t work try shut down and then  start it (strange…but  works). Enjoy [IMG]http://s0.wp.com/wp-includes/images/smilies/icon_smile.gif?m=1300809663g[/IMG]




I wrote it on my blog as well....

Source: [http://computerandu.wordpress.com/20...-ubuntu-11-04/]("http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/")

---

### Post by NonStop on 2011-05-05
Hi, wireless was fine on 10.10, it was working fine, I downloaded and installed 11.04 via wireless, no prompts to download additional driver Broadcom STA. Out of interest how do you know this is a Broadcom issue?

1) Other questions are how do I find out of my laptop is 62bit or 32bit?

2) How exactly do I install the new driver - I plan to download it to my USB, and transfer it to my laptop via it - step by step explanation would be much appreciated.

3) Should I uninstall old drivers, then restart and install new ones then reboot, or uninstall old driver and install new ones all in one session before rebooting?| I'm sure its the latter, just want to clarify.

Thank you so so much for your time and patience.

---

### Post by computerandu on 2011-05-05
> **NonStop said:**
> Hi, wireless was fine on 10.10, it was working fine, I downloaded and installed 11.04 via wireless, no prompts to download additional driver Broadcom STA. Out of interest how do you know this is a Broadcom issue?

1) Other questions are how do I find out of my laptop is 62bit or 32bit?

2) How exactly do I install the new driver - I plan to download it to my USB, and transfer it to my laptop via it - step by step explanation would be much appreciated.

3) Should I uninstall old drivers, then restart and install new ones then reboot, or uninstall old driver and install new ones all in one session before rebooting?| I'm sure its the latter, just want to clarify.

Thank you so so much for your time and patience.


Your lshw -C network gives "**vendor: Atheros Communications Inc."** ..that means your network adapter is Atheros (not Broadcom)..that further means that the solution i suggest to you will not work...

1) Other questions are how do I find out of my laptop is 62bit or 32bit?

go in the terminal and type: **uname -a**   press enter...
my result is: Linux takshak-Inspiron-N4010 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 **x86_64 x86_64 x86_64** GNU/Linux
i.e. my operating system is 64 bit..

Since your network adapter is not Broadcom ...don't follow the previous instructions....

I am looking for a better solution...will give in some minutes..

---

### Post by computerandu on 2011-05-05
Hi...

Please follow this thread.,...

[http://ubuntuforums.org/showthread.php?p=10772130](http://ubuntuforums.org/showthread.php?p=10772130)

a bit technical for a starter...but thats all i could find at the moment....its almost 12'o clock and i need to go to bed...


all the best

---

### Post by Onitek on 2011-05-06
Hi. 

I have the exact same problem. It's not that the wireless connection won't work, is disabled or won't start. It findt my wireless router without problem. But it won't connect to it. When I try it simply continues trying to connect for some time, and then it asks for the password again (which is correct). Sometime (bit out of nowhere) it suddenly connects. I had no problems at all in 10.10 (or any other version since 7.10) 

When i run lshw i get the following (again, Atheros)

sudo lshw -C network
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:04:05.0
       logical name: wlan0
       version: 01
       serial: 00:19:7d:b3:59:0c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.101 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:c3000000-c300ffff


Please Help!

---

### Post by NonStop on 2011-05-07
> **Onitek said:**
> Hi. 

I have the exact same problem. It's not that the wireless connection won't work, is disabled or won't start. It findt my wireless router without problem. But it won't connect to it. When I try it simply continues trying to connect for some time, and then it asks for the password again (which is correct). Sometime (bit out of nowhere) it suddenly connects. I had no problems at all in 10.10 (or any other version since 7.10) 

When i run lshw i get the following (again, Atheros)

sudo lshw -C network
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:04:05.0
       logical name: wlan0
       version: 01
       serial: 00:19:7d:b3:59:0c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.101 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:c3000000-c300ffff


Please Help!

Exactly the same for me. If we don't get any responses, we should repost for a new thread

---

