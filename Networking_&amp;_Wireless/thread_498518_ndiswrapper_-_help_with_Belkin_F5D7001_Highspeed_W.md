---
title: "ndiswrapper - help with Belkin F5D7001 Highspeed Wireless 128Mbps Desktop Network Car"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by Lunatrix on 2007-07-11
Chipset: BCM4306
pciid: 14e4:4320


this is truly atrocious, i just cant seem to catch a break. im up for 3 days straight and i still cant figure out how to get the internet on my computer runnung linux ubuntu (fiesty fawn) i have done so much research it knocked me back to the 3rd grade. i need help people please!

i have 2/3 thing for ndiswrapper installed the last thing doesent have enough dependincies. 

fa3mir (2:20:03 PM): oh
fa3mir (2:20:42 PM): you got build-essential installed?
WhO Iz LuNaTrIx (2:20:59 PM): nope
WhO Iz LuNaTrIx (2:21:05 PM): not that i know of
fa3mir (2:21:17 PM): might be a problem there
WhO Iz LuNaTrIx (2:21:14 PM): mk
WhO Iz LuNaTrIx (2:21:15 PM): hold
WhO Iz LuNaTrIx (2:21:18 PM): lemme c if i kan get it
WhO Iz LuNaTrIx (2:27:05 PM): ok build is burning to a disk
WhO Iz LuNaTrIx (2:30:06 PM): wow
WhO Iz LuNaTrIx (2:30:16 PM): another error to add onto it
WhO Iz LuNaTrIx (2:30:17 PM): lol
fa3mir (2:30:39 PM): because it needs more dependencies
fa3mir (2:30:48 PM): ******* VENDORS WITHOUT DRIVERS FOR LINUX
fa3mir (2:30:50 PM): sorry.
WhO Iz LuNaTrIx (2:30:47 PM): lmfao

i mean this is like bill gates taking his windows vista case and showing it into a donkey #%$. 

this is so hard just to get the internet working. i need help guys PLEASE!

---

### Post by bkaskar on 2007-07-11
Hi,

I had broken dependencies as well, so first I reinstalled (as it was a fresh install - not sure if you havethat option)

Then used the CD Rom to install the build essentials and other packages basically when you try to install ndiswrapper using 'sudo gdebi <package>' or 'sudo dpkg -i <package.deb>' it tells you what are the dependencies.. 
So first try installing those before trying to install ndiswrapper.

In my case I had the following missing module-assistant packages which in turn had libtext-wrapi18n-perl_0.06-5_all -> libext-charwidth-perl missing..
for debhelper_5.0.42ubuntu1_all had html2text and po-debconf ->intltool-debian -> gettext

Since I did not have a network card (wired or wirelss), I downloaded all the packages in a USB drive and installed them bottom up and then installed ndiswrapper utils and other ndiswrapper packages.
You have to start from [http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9) and get rid of all the broken dependencies before you get ndiswrapper to work.

Now you can either use the driver provided in CD or get the one from Dell ([http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE)) and go to the AR folder (where bcmwl5a.inf and bcmwl5.sys files are)
Then you can do su to root or run each command with sudo 
```

modprobe ndiswrapper
dmesg (to chk if module loaded properly)
ndiswrapper -i bcmwl5a.inf
ndiswrapper -l (its lower case 'L')
ndiswrapper -m

```

After restarting your network services (or rebooting) you should be able to see this card in network manager.

Hope that helps
-B

---

