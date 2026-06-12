---
title: "help with ndiswrapper, permissions"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by drumkitcat on 2007-02-09
Hi,

I am having the same problem with 2 versions of Ubuntu... please help:

First, here are the two versions:

1. Xubuntu 6.1 running on a pII 266 with 192mb Ram, and Linksys wireless (broadcom chipset)

2. Ubuntu 6.06 running on an AMD K6-2 450 with 384mb Ram, and Netgear wireless (Atheros chipset)

I am trying to get each of these machines to access my router and hence, on the internet.

I am very new to Linux, so it's a slow learning process, but, here's what I do know and have:

1. I do have the proper INF and SYS files for each wireless card.
2. My home network is DHCP based with 5 computers, 2 now are Ubuntu and the other 3 are Windows XP Home.  The Internet connection is wireless highspeed, going from a cable modem to the router.

3.  I can get each box (the Ubuntu and Xubuntu) to show the wireless card using the "lspci" command - each sees it, however neither gets the card running by itself.

4. I tried to install the latest version of NDISWRAPPER but I get a common error on both machines saying something about fatal error, need permission or something like that.

- How do I "get" permission to run NDISWRAPPER,  I printed off some commands yesterday that seem to show how to run the program but I get an error saying "ndiswrapper command not found" - when I'm running it from the same directory I copied it into... ?? wtf?  

As I said, I have the drivers for each wireless card - and I've created a directory on each machine and put the drivers in that directory.   How do I go about getting it installed from there?  

Please, any help would be most appreciated, I don't know frigall about Linux, so this is very frustrating.  I really really like how slick Ubuntu is, but I also really really need the Internet access.

---

### Post by drumkitcat on 2007-02-09
Forgot to mention; in both cases also, I have the network manager set up with the correct SSID and WEP key information.. it appears to be just a matter of changing the permissions to install Ndiswrapper, and the related drivers...

---

### Post by ukripper on 2007-02-09
paste your lspci here or chipset info:)

---

### Post by drumkitcat on 2007-02-09
sorry I can't do that - I'm at work and both computers are at home.  I won't be able to post that easily, as both machines are not dual boot, only Ubuntu/Xubuntu so getting a screen shot may be impossible.

I know that each computer sees the wireless card just fine when I use lspci,

is there any other information you can provide without seeing the screen info?

---

### Post by ukripper on 2007-02-09
you don't need to take the screenshot, just copy text from terminal on here. I just needed chipset info such as bcm43......  so that I can refer to the best guide for you including ndiswrapper.
Also, iwconfig will be great help if you paste that as well.

or perhaps you can tell atleast full INF and SYS name you are using that wil give me the chipset info.

---

### Post by drumkitcat on 2007-02-09
ok, I can get you that, but it will be sometime Saturday as I won't be able to get to the computers until Saturday morning most likely..  sorry..

Thanks, and I'll post it as soon as I can

---

