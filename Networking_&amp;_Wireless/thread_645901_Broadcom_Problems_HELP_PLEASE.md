---
title: "Broadcom Problems HELP PLEASE"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by raven05 on 2007-12-20
Ok so I have an HP Pavilion dv6000 with a Broadcom 43xx chipset family and I have the Firmware turned on. It doesn't seem to want to work and I've tried all kinds of things that have been listed in the forums but it doesn't work. Could someone please give me some advice or point me in the right direction I'd really like this fixed.

---

### Post by jan quark on 2007-12-20
me too having the same problem. have also an bxm43xx chip and have read a lot in this forum but nothing worked. so i cry for help too:confused:

---

### Post by raven05 on 2007-12-21
bumping

---

### Post by gfd_2 on 2007-12-21
similar if not same problem... HP dv6633us with Broadcom 4311 card... wireless network is seen but can't successfully connect.

---

### Post by Cybermax on 2007-12-21
The forum is full of threads regarding broadcom and BCM43xx chips.

Sadly all i have found out so far.. it just doesnt work.

However, there are also threads regarding the use of ndiswrapper and some howtos to this that can provide a workaround that you need (if you just want the laptop to come online via wireless).

Do a search for "ndiswrapper" on the forums for a link of some howtos.

C

---

### Post by gfd_2 on 2007-12-21
neither ndiswrapper nor the restricted-driver suggestions seem to work.  right now the card seems to be active, connects to my network but will not send/ recieve.. .

---

### Post by Vadi on 2007-12-21
Is the network secured (with wep or wpa)?

---

### Post by gfd_2 on 2007-12-21
in my case no WEP/ WAP... wired card works every time.... wireless does not.

I've seen a number of threads about disabling ipv6.. what does this do and could it be a potential source of contention with a wireless card?

---

### Post by Salazar420 on 2007-12-21
Funny, I've gotten this same broadcom chipset or whatever to work with gutsy simply by accepting the proprietary drivers in restricted drivers manager, and also using this tutorial as a troubleshoot [http://ubuntuforums.org/showthread.php?t=405990]("http://ubuntuforums.org/showthread.php?t=405990")

It is currently, however, inoperable, due to excessive tweaking, manipulating, etc. Sometimes it just doesn't register after I tweak it too much, but using such tools as airodump-ng or wireshark, I am able to detect an eth1 wireless interface. Such is not, however, the case for me right now. Fully inoperable. When operable, though, I've connected  such things as safeway's free wifi, etc. The only thing I haven't been able to get to work is kismet, and that's only because I'm too lazy to learn how to patch the kernel... or something. 

Anyway, best of luck to you guys. Godspeed.

---

### Post by Vadi on 2007-12-21
I'm not sure on what does it exactly do, I think it's just the next-generation internet protocol which allows for longer adresses (because the current one, ipv4, is starting to run out of them), but it's not all that used yet.

It could be a potential source though, so try disabling.

Also, I noticed that the ndiswrapper version in ubuntu is very old - it's 1.45, while the latest one is 1.51 (released just 3 days ago too).

So, lets try installing the latest version.

- download the latest release ([click]("http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.51.tar.gz?modtime=1197921854&big_mirror=0"))

- right-click on the archive, select extract here

- then open the terminal, and navigate to the folder with ndiswrapper. In my case it was on my desktop, so

```
cd ~/Desktop/ndiswrapper-1.51
```

did the trick.

- then run

```
sudo make uninstall
```

to remove whatever ndiswrapper you had

- then run 

```
make
```

to, I guess, "make" it,

- and then

```
sudo make install
```

to install it.

So now that we have the latest version (you can do "ndiswrapper -v" to check. It'll say version 1.51), we'll need to get the drivers for the broadcom card.

I poked about the ndiswrapper wiki, here's what can work for the 4311, v1 (that's what the HP dv6000 ships with).

- first off, the driver comes as a .exe, so we'll need a program to extract it. Copy paste/into the terminal again:

```
sudo apt-get install cabextract
```

- download the file:

```
cd ~/Desktop
mkdir drivers
cd drivers
wget ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe
```

- extract them

```
cabextract sp34152.exe
```

- then install the driver:

```
sudo ndiswrapper -i bcmwl5.inf
```

- and it should work at this point. Give it a few for the network manager to detect it - you should be able to right-click on the little inco, and select 'enable wirless', or left-click, and select your wireless network.

Or if it doesn't work right away, try rebooting.

---

### Post by gfd_2 on 2007-12-21
I'll be home by 21:00 tonight and will give this a try... thanks!

---

### Post by berthiggins on 2007-12-21
You will also need to blacklist the firmware driver or it will not work .
Just open /etc/modprobe.d/blacklist with a text editor and add "blacklist bcm43xx" to the bottom of the file and save .
You may also need to add "ndiswrapper" to the bottom of /etc/modules this will ensure that it loads every time, this is not always needed but is a good precaution ymmv.
I have been using ndiswrapper with my broadcom card for some time it is more stable and faster than the firmware implementation at this time.

---

### Post by Vadi on 2007-12-21
Just don't forget to put sudo before those commands, so that you can actually save the files.

So

```
sudo gedit /etc/modprobe.d/blacklist
sudo gedit /etc/modules
```

will open the two files.

---

### Post by berthiggins on 2007-12-21
Indeed you will !

---

### Post by Vadi on 2008-01-01
Yeah, we've tried pretty much every guide we could find, and it still refuses to work.

The card is 4311, v1, if it helps.

---

