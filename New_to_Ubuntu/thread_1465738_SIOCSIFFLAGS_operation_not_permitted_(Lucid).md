---
title: "SIOCSIFFLAGS: operation not permitted (Lucid)"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Julita on 2010-04-29
Hi! I am trying to establish my wireless connection! I have installed successfully ndiswrapper driver, but wireless (ralink 3090) wouldn't connect. Every time (as a root)
```
ifconfig wlan0 up
``` I get this error. I am not the only one with this problem, and the solutions about iwconfig wlan0 txpower auto, adding .dat file to /etc/wireless/RT*, renaming said directory also did not help, especially when the latter did not exist... I did not have this issue with previous releases, and I don't have access to wired network; ndiswrapper driver works flawlessly.
The funny thing is that I can put the network down, but the error occurs when I try to "up" it. Please help.

By the way, with previous builds I was able to install the driver from launchpad, since it required only dkms package. In this release, dkms requires gcc dependency. I can't download the whole bunch of dependencies, so thank God that ndiswrapper supports my card.

Please help! I would like to know if there is anyone else experiencing the same problem with this release.

---

### Post by cariboo on 2010-04-30
What happens if you try:

```
sudo service networking restart
```

---

### Post by Julita on 2010-04-30
Thank you! Everything is settled now! I saw via lsmod that there was pre-installed driver - rt3090sta, so I removed it from the kernel; then ndiswrapper module was functioning, and I am now writing through this connection :)

---

### Post by itsme2day on 2010-05-14
> **cariboo907 said:**
> What happens if you try:

```
sudo service networking restart
```

I tried entering the above code and received the following response:

restart: Unknown instance:

---

### Post by Julita on 2010-05-14
> **itsme2day said:**
> I tried entering the above code and received the following response:

restart: Unknown instance:

What is your actual problem? What type of connection do you have?

---

### Post by pkadetiloye on 2010-09-05
Hmm, this is going to be my first public post on Ubuntu forums...

After battling with the "wireless disabled" problem on my box HP Compaq CQ60, I eventually solved it -and thanks to many forums threads.

Actually, the problem occurred when I hibernated my system and trying to resume, my network appeared grayed and disabled on my gnome network manger.

Various forums had different solutions deleting NetworkManager.state file in /var/lib/NetworkManager, installing wicd....blah, blah. But none never worked for me.

Infact, running lshw -C network shows *network disabled. Of course, If you try enabling the network interface,
$sudo ifconfig wlan0 up 

you get the error message SIOCSIFFLAGS: operation not permitted unknown code 132...

well, I eventually got the wireless working when I read a post on a forum and I'm going to post it here as the authoritative solution to the problem. (Sorry, I can't figure the original URL, but you can always paste it here for due credit!).

$sudo rmmod ath5k (you may have to replace with your driver module e.g ath9k)
$ sudo rfkill unblock all
$sudo modprobe ath5k (you may have to replace with your driver module e.g ath9k)

I found out that the rfkill program is not installed on my ubuntu 9.04 so I had to download the package and installed it manually.
Now, everything works fine!!!

):P

---

### Post by Julita on 2010-09-06
Thank you for pointing this out! In fact, it seems to be the problem of pre-installed modules. The "original" ones wouldn't load because of some incompatibility issues with the hardware. Sometimes ```
lshw -C network
``` differs depending on the module that is currently loaded. Thank God who brought us Linux!

Offtopic: I installed XP on my friend's Compaq notebook, newest model. The sound card wouldn't be recognized, of course (no drivers for XP). So, first thing to check: ran Xubuntu 10.04 live CD, everything works out of the box. Not hardware issue. I had to install 2 drivers before I found the one for Vista that worked! I mean, I spend about an hour or so, instead, I would prefer to install Ubuntu ;) But, of course, I am the only one around who uses all kinds of Linux distros... The situation in the nearest future wouldn't change, sadly! Thanks to the community, however, we become more and more ingenious! YES!

---

### Post by ario on 2010-10-17
> **pkadetiloye said:**
> 
$sudo rmmod ath5k (you may have to replace with your driver module e.g ath9k)
$ sudo rfkill unblock all
$sudo modprobe ath5k (you may have to replace with your driver module e.g ath9k)

I found out that the rfkill program is not installed on my ubuntu 9.04 so I had to download the package and installed it manually.
Now, everything works fine!!!

):P

Mine is DWA-125. By installing driver for rt3070sta from ralink, no problem exists and no need for above commands.
Hope it helps someone.

---

