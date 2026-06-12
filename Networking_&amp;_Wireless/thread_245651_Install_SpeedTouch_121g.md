---
title: "Install SpeedTouch 121g"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by antmg on 2006-08-28
I need to install wireless SpeedTouch 121g (model 580) in Ubuntu 6.06.
I'm new in Linux. It's impossible for me!
Thanks!

---

### Post by kyke on 2006-09-15
I got it working with ndiswrapper! ;)

1. Install package ndiswrapper-utils:
```
sudo apt-get install ndiswrapper-utils
```

2. Download the 121g driver for Windows from [http://www.speedtouch.com/support.htm](http://www.speedtouch.com/support.htm)
(I got ETSI driver but no idea what FCC version was)

3. Unzip driver file, mine was ST121gR21v0_Setup(ETSI).zip  

4. Enter "ST121g Setup/Driver/" and install .inf file in ndiswrapper:
```
sudo ndiswrapper -i BT4501G.inf
```

5. Check driver installed okay:
```
sudo ndiswrapper -l
```
If will tell "driver present", and also "hardware present" if you got the 121g dongle inserted.

6. Load the ndiswrapper module into the kernel:
```
sudo modprobe ndiswrapper
```

7. Finally check it loaded okay and detected the card:
```
sudo dmesg | tail
```

8' So you have a new network interface, wlan0 . You can configure and activate it with "System / Admin / Network" or with iwconfig and ifconfig console commands.

9. Optional, let the kernel load ndiswrapper automatically when you insert the dongle:
```
sudo ndiswrapper -m
```

Hope this helps.

---

### Post by nabdan on 2006-11-20
Hi all,

I try to install my ST121g , everything seems ok but I encounter a trouble when trying to launch module in kernel:

**sudo modprobe ndiswrapper**

When I enter that command, Ubuntu send me an error message (I have not thew exact one will postr it here soon).

I use Ubuntu EDgy, device seems okay when use:

**sudo dmesg | tail**

Recognize and detected.

Please help :p

---

### Post by nabdan on 2006-11-21
Hi all,

Here my error message:

> FATAL: Error inserting ndiswrapper
(/lib/modules/2.6.17-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko):
Invalid argument

It seems that I am enable to launch drivers in kernel, starnge thing is that drivers and card seems detected :confused: 

Any idea will be really welcome.

Thanks.

NabdaN

---

### Post by nabdan on 2006-11-23
Hi all

Still in troubles here ](*,) 

here the detail of : 

**sudo modprobe ndiswrapper**



nab@nab-laptop:/lib$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
nab@nab-laptop:/lib$ 


**sudo dmesg | tail**

[17179866.644000] ISOFS: changing to secondary root
[17180234.592000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180234.620000] ISOFS: changing to secondary root
[17180366.420000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180366.448000] ISOFS: changing to secondary root
[17254222.848000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17254222.888000] ISOFS: changing to secondary root
[17255197.672000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17255197.692000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17255197.696000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed

**ndiswrapper -l**

Installed ndis drivers:
bt4501g driver present, hardware present 



I hope it can help.

---

### Post by nabdan on 2006-11-26
hi all

It works !

I had just to update ndiswrapper to 1.8 because i m using edgy !

Thanks for tip :)

NabdaN

---

### Post by catman7 on 2006-12-11
hi @ all

I'm having issues with installing the driver for my speedtouch 121g under edgy..
I followed the HOWTO above, but when I check the driver I recieve this:

ndiswrapper -l
Installed drivers: bt4501g invalid driver!

???
alreday thanks in advance!!
catman7 (o:

---

### Post by nabdan on 2006-12-12
Hi,


Be sure to update ndiswrapper to release 1.8 with repositry, it is required for Ubuntu Edgy.

Probably that best option is to delete drivers in NDISwrapper and try to install it again.

Use terminal as root and move to your ndiswrapper folder and delete any bt4501g.

Download again drivers on following link and try install again:

Download the 121g driver for Windows from [http://www.speedtouch.com/support.htm](http://www.speedtouch.com/support.htm)
(I got ETSI driver but no idea what FCC version was)

I wish you best of luck.

Bye

---

### Post by catman7 on 2006-12-12
Heyy Nabdan - was glad to see your answer already this morning!!
I'm just new at Linux (and I already love it!!), I think I just make a stupid mistake somewhere- beacause I still can't make it working ](*,) .

I tried two ways:

\1\
maren@toughbook:/usr/bin$ sudo ndiswrapper -i BT4501G.inf
Installing 4501g
couldn't copy BT4501G.inf a /usr/sbin/ndiswrapper-1.8 line 144

\2\
(had to change folder names)
maren@toughbook:~/setup/driver$ ndiswrapper -i BT4501G.inf
Installing bt4501g
Unable to create directory /etc/ndiswrapper/bt4501g.Make sure you are running as root

But I was root in the first go, wasn't I?
I'm sorry for asking these simple questions- I hope I'm not annoying too much..

;)

---

### Post by nabdan on 2006-12-12
Hi Catman 7

Same here I m a newbie of Ubuntu and i more than like it :) 

all commands should be enter as a root, in Ubuntu you have to type "sudo" before each commands.

My little advice :-k 

use synaptic package manager to uninstall in a clean way ndiswrapper.

install the edgy version : ndiswrapper 1.8 (it should install common ndiswrapper common too).

and retry commands as a root using "sudo" each time (only first command require to enter your root password); use default ndiswrapper folder installation.

I wish you best of luck Catman7 !

NabdaN

---

### Post by catman7 on 2006-12-12
Heyy!

Problem solved- don't ask me how (sat the whole day behind the screen)!

now I'll have to worrk at the configuration problem, but that's an other story ;)

Greetings,
catman7

---

### Post by nabdan on 2006-12-12
Cool !

I try to manage WPA/WPA2 now :-k 

if you find a good tip :)

Bye !

---

### Post by Radovitch on 2006-12-17
Hi,
Another newbie here with exactly the same problem, well almost the same. The adapter I'm attempting to install is the same but I have kubuntu. Does this make a difference? Also, I can't download with apt-get as the speedtouch is my only internet connection. But I'm on a dual boot with Windows and can do it that way.
Thanx

---

### Post by nabdan on 2006-12-18
hi,

You have to find the good software release of ndiswrappper, I do not know for kubuntu, but i think problem is here.


Edgy is: 1.8

You should answer to kubutnu user which one is the best one.

I wish you best of luck, let us know if it works after that.

Nab.

---

### Post by Radovitch on 2006-12-23
Hi,
I decided to switch to ubuntu as I think the gnome comcept will be easier to learn. The problem is that as I have no internet connection in Linux I am unable to use the apt-get command to do the automatic installing. I have managed to download with Windows both the ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb and the speedtouch driver indicated on the first page of this thread. I copied them to the Home file but have been unable to go any further. What I need is the exact terminal commands to enable me to install both of these programs and then I can try to take it from there.  Sorry if this sounds a bit obtuse but up until a week ago I had never even seen the inside of the Linux OS and am still trying to make sense of it all. I never realised how sheltered the Windows world was until now.

Thanx

---

