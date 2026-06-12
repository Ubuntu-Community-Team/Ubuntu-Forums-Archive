---
title: "Why is Wireless internet Slow in Linux ?"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by tuxy on 2006-09-19
I have Ubuntu Dapper and Windows XP as dual boot on my laptop. I find the wireless internet very slow when I am in ubuntu. But, when i am in Windoze the wireless is pretty quick. i dont know whats the reason behind it!

I am using Broadcom BCM4318 wireless card and my wireless router is Belkin7230.

This is what i get when i do "iwconfig" :
-----------------
lo        no wireless extensions.

wlan0     IEEE 802.11b/g  ESSID:"XYZ"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point:             02:11:50:FF:62:F4
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=183/100
          Rx invalid nwid:0  Rx invalid crypt:23  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
---------------------

Is the "Bit Rate=11Mbps" makes any difference?

---

### Post by Dinerty on 2006-09-19
> **tuxy said:**
> I have Ubuntu Dapper and Windows XP as dual boot on my laptop. I find the wireless internet very slow when I am in ubuntu. But, when i am in Windoze the wireless is pretty quick. i dont know whats the reason behind it!

I am using Broadcom BCM4318 wireless card and my wireless router is Belkin7230.

This is what i get when i do "iwconfig" :
-----------------
lo        no wireless extensions.

wlan0     IEEE 802.11b/g  ESSID:"XYZ"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point:             02:11:50:FF:62:F4
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=183/100
          Rx invalid nwid:0  Rx invalid crypt:23  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
---------------------

Is the "Bit Rate=11Mbps" makes any difference?

you say the internet is slow, do you mean surfing webpages?, downloads?

---

### Post by tuxy on 2006-09-19
Yeah! Surfing webpages-not even downloading stuff from the internet.
The internet accessing thru wireless on Ubuntu is very slow compared to accessing internet wirelessly when I am on Windoze.

I dont have any problem when I access thru hard wired when I am on Ubuntu.

---

### Post by jdmpike on 2006-09-19
I have also wondered why there isn't support for faster bit rates. I have a D-Link DWL-650 which supports 108Mbs when used with my D-Link router.

Is that something the madwifi driver needs to address for the Atheros chipset?

Has anyone had success getting results like what is published on the box? If so, please let me know how so!

Peace, love, and ubuntu,

jdmpike

---

### Post by Melcar on 2006-09-19
I think it depends on the method you use to activate wireless in Linux, meaning that it's a problem with the drivers in Linux itself.  I know that when I use the fwcutter method to get my wireless working it caps at 11Mbps, but ndiswrapper lets me go all the way to 54Mbps.

---

### Post by tuxy on 2006-09-19
Thanx for the quick reply. I have configured my wireless card thru "fwcutter". Do you think I have to try "Ndiswrapper" to make my wireless internet access faster?

---

### Post by Melcar on 2006-09-19
You can give it a try.  A plus I found while working with ndiswrapper is that even if you update/change the kernel your wireless device will still work; under fwcutter you have to add the firmware to the kernel every time you make a change.

---

### Post by tuxy on 2006-09-19
Is there any good "How To" for Ndiswrapper? I know there are million postings in this forums but any recommendations ?

---

### Post by Melcar on 2006-09-19
I used this one for my broadcom chip
[http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper]("http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper")

---

### Post by swanky on 2006-09-19
Hi

I had the same problem. Have you made sure that you have disabled IPv6 protocol, some routers have a problem with it and end up slowing down your data transfer. 

try this:

1. Open a Terminal Window
2. Type sudo gedit /etc/modprobe.d/bad_list/
3. In the gedit window, type: alias net-pf-10 off
4. Save the file and reboot.

(from [http://ubuntuforums.org/showthread.php?p=1509398](http://ubuntuforums.org/showthread.php?p=1509398))

Rich

p.s. Its silly having to do it this way, hopefully someone will make it a tick of a box soon

---

### Post by bionnaki on 2006-09-19
silly? commandline is quick and efficient especially if you use a commandline editor like nano.

> sudo nano /etc/modprobe.d/bad_list/

---

### Post by Melcar on 2006-09-19
> **bionnaki said:**
> silly? commandline is quick and efficient especially if you use a commandline editor like nano.

Command lines rock:cool: .  Now I can't stand to use Windows anymore.

---

### Post by swanky on 2006-09-19
True

Command line is best I know, but there is so much to remember (even after four years like me). Some times its nice to just tick a box.

The poor people coming to linux from else where get such a shock having to remember so much and it scares them away again

:-$ 
:D 

Rich

---

### Post by Melcar on 2006-09-19
> **swanky said:**
> True

Command line is best I know, but there is so much to remember (even after four years like me). Some times its nice to just tick a box.

The poor people coming to linux from else where get such a shock having to remember so much and it scares them away again

:-$ 
:D 

Rich

Yeah, but you get used to it, and after typing in so many commands you eventually memorize a few.

---

### Post by egoldtech on 2006-09-20
Hi, why you say wireless is slow?
did you try to connect via cable and works perfect??
I have before a lot of problem, surfing and connecting to internet, was really really slow,
then I found really good
go to 
about:config   on Firefox
and then network.dns  ipv6 diabled  TRUE
then blaclist or diabled IPv6 modules
and now
goes really really fast .
and on the process I install cache DNS, nice ....
try it ....

Eze

---

### Post by tuxy on 2006-09-20
Thanx for the help guys. I have configured my wireless card with Ndiswrapper it's working great now. Much faster than before(which was conigured with fwcutter). 

Mine is a Broadcom 4318 Airport wireless card. I have tried this post.
[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318+ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318+ndiswrapper)
It worked great and the speed is increased from 11MBPS to 54MBPS.

---

