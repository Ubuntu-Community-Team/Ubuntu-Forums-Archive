---
title: "can see wireless networks, but can't connect"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-21
the gods have decided that i don't need internet...but i'm trying to write a paper!

my wireless worked perfectly before i hibernated it. in fact, it's been about 6 months since i install the ath5k drivers. 
now it doesn't work at all. i'm being punished for turning my laptop off.

I tried restarting it (usually fixes it)
I tried turning the WIFI switch on and back off.
I tried recycling the "enable wireless" option in network manager
i tried "sudo ifconfig wlan0 up"
            i get "resource temporarily unavailable"
i tried iwlist scan
            wlan0: no scan results

what is this? why did it choose right now to break? why is software so unreliable? usually something has to be messed with for this to happen. instead, it just happens sporadically. 

here are my specs:
ACER Aspire 4720Z Laptop
Pentium Dual-Core 2GB RAM 120GB hard disk
Atheros wireless card AR5BXB63
Ubuntu 9.04 
"Support for 5xxx series of Atheros 802.11 wireless LAN cards." is Activated in hardware manager. 

any ideas?

---

### Post by abyssius on 2009-04-21
First, take a deep breath... then try following this thread.

[http://ubuntuforums.org/showthread.php?t=1123014]("http://ubuntuforums.org/showthread.php?t=1123014")

I hope this helps you.

---

### Post by asuastrophysics on 2009-04-23
alright i have connection again, but the internet is ungodly slow. in fact, it's totally unusable now. i am at 100% signal strength and ipv6 is disabled and blacklisted. 
EDIT: i tried sudo modprobe ath9k. this didn't really have an effect on the speed, but it's good to know in case sudo ifconfig wlan0 up doesnt work! 

also for a note, my cpu now throttles at 100% all the time. adding CPU Frequency Scaling monitor to gnome panel gives me this message:
> You will not be able to modify the frequency of your machine. Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

this is odd, because it used too...

so since the last jaunty update, my wifi driver has been broken, there noveau driver still doesnt work, and i have no power management. 
...great update!

---

### Post by Fredizdman on 2009-05-05
I have a very similar problem. My HP dv6000 atheros card (242x) is doing the same thing. It has done this a few times before the Jaunty update, but seems to be MUCH worse afterwards. Basically when I boot the machine everything works fine. Then completely randomly the wireless will drop the connection, the circular connecting image in the tray just sits there and circles with one green dot...forever. Occasionally a box will pop up asking for the Encryption key (which is already filled in and I have connected to it already), so I click Connect. Still nothing.......a few more minutes the box comes back, etc.

If I shutdown the machine it starts to work again, although even this does not work 100%. A simple restart NEVER works, and definitely not a wireless or gdm restart.

When I attempt to:

sudo ifconfig wlan down
sudo ifconfig wlan up

I get :

SIOCSIFFLAGS: resource temporarily unavailable

This is the error that remains until shutdown, even after

sudo /etc/init.d/networking restart

and 

sudo rmmod ath5k
sudo modprobe ath5k

I can't think of anything else, and am unsure why the frequency of this bug is so much greater with Jaunty.

Any ideas?


I am at school at the moment and will not be able to troubleshoot until later this evening. Thanks

---

### Post by Fredizdman on 2009-05-06
bumpity bump bump

---

### Post by crom.osec on 2009-05-06
I've had same problem on kubuntu 9.04.

My solution was:
I've removed the network manager and I've changed myself the /etc/network/interfaces file as follows (for wep security):

auto wlan0
iface wlan0 inet static
address xxx.xxx.xxx.xxx
network xxx.xxx.xxx.0
netmask 255.255.255.0
gateway xxx.xxx.xxx.1
wireless-essid <Your Essid here>
wireless-key s:<your Essid password here>
dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx


hope that helps.

---

### Post by asuastrophysics on 2009-05-06
i figured out my problem! BOINC runs in the background all the time. at every system startup, i have to enter in: ```
sudo killall boinc
```
or else the cpu throttles really high

and i can't remove BOINC manager from add/remove programs!

it says it's already uninstalled, but it still runs in the background.

this OS is no better than windows. for a while, i at least took comfort in knowing that programs were easy to remove...WRONG. 

why is BOINC still running in the background even though it's program is removed?

---

### Post by milasch on 2009-05-18
> **asuastrophysics said:**
> alright i have connection again, but the internet is ungodly slow. in fact, it's totally unusable now. i am at 100% signal strength and ipv6 is disabled and blacklisted. 
EDIT: i tried sudo modprobe ath9k. this didn't really have an effect on the speed, but it's good to know in case sudo ifconfig wlan0 up doesnt work! 

also for a note, my cpu now throttles at 100% all the time. adding CPU Frequency Scaling monitor to gnome panel gives me this message:


this is odd, because it used too...

so since the last jaunty update, my wifi driver has been broken, there noveau driver still doesnt work, and i have no power management. 
...great update!

How did you get to disable ipv6 anyway? I read so many guides saying the same thing: set /proc/sys/net/ipv6/conf/all/disable_ipv6 to 1 or add ipv6.disable=1 to the kernel line, but they both don't work.

---

### Post by Fredizdman on 2009-05-22
I still haven't been able to find a solution to my problem above. Unfortunately, removing the network manager is just not a viable solution for me since I would like to be able to connect to more than one network and *new* networks with ease. This problem does seem to be happening more often in jaunty, and I didn't notice it all in Gentoo, although in Gentoo I did not use nm-applet at all, which is mostly the reason I switched to Ubuntu, I could never get a good wireless network manager to work in Gentoo. Is no one else having this problem?

---

### Post by Dafunkybhudda on 2009-06-07
yes I am having exactly the same problem, did you resolve it bud?? am sitting here dumbfounded.

---

