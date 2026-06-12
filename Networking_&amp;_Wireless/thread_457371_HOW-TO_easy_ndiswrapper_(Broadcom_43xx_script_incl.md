---
title: "HOW-TO: easy ndiswrapper (Broadcom 43xx script included)"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by bmartin on 2007-05-28
[COLOR="Red"]If you're running Hardy Heron, I recommend using the driver in the **Restricted Drivers Manager**. It works quite well![/COLOR]

Please see [this thread](http://ubuntuforums.org/showthread.php?t=405990).

---

### Post by Knightstormz on 2007-05-28
great idea but this assumes you have a wired connection the the computer you are running the script on.

---

### Post by Jimmy The Clown on 2007-05-29
A++++ Great poster!!! Would do business again!

But seriously your timing was perfect. Just wiped my old breezy partition and clean installed Feisty. Using a Broadcom 4306 rev 02 on a hp nx9010. 

One note, seems like I didn't enable the community repo before I ran your script. Got no error on cabextract install, but the command failed later in the script. I realized my mistake pretty quick.

Also got 

```
./auto-ndiswrapper.sh: line 57: [: too many arguments
```

during the ndis script. Everything seems to be working fine connecting to a WEP wireless at 54 mbps.

JTC

---

### Post by benmoreassynt on 2007-05-30
sorry poisted in wrong place

---

### Post by hoistyler on 2007-06-09
I have a problem..

This is what I get when I type 

sudo ./auto-ndiswrapper.sh

```

* Backing up current configuration
* Installing the necessary compilation libraries
* Removing old ndiswrapper module
./auto-ndiswrapper.sh: 56: pushd: not found
* Removing old ndiswrapper
make: *** No rule to make target `uninstall'.  Stop.
make: *** No rule to make target `uninstall'.  Stop.
make: *** No rule to make target `uninstall'.  Stop.
* Compiling ndiswrapper
make: *** No targets specified and no makefile found.  Stop.
* Installing ndiswrapper
make: *** No rule to make target `install'.  Stop.
./auto-ndiswrapper.sh: 67: popd: not found
* Configuring ndiswrapper
./auto-ndiswrapper.sh: 71: pushd: not found
./auto-ndiswrapper.sh: 72: ndiswrapper: not found
./auto-ndiswrapper.sh: 73: ndiswrapper: not found
./auto-ndiswrapper.sh: 74: ndiswrapper: not found
./auto-ndiswrapper.sh: 75: popd: not found
* inserting ndiswrapper module
*** Installation is complete. You may need to restart your computer for the changes to take effect.

```

---

### Post by bmartin on 2007-06-09
Are you running a shell other than BASH? pushd and popd are BASH built-in commands.

Edit: there's an extra line at the beginning of the script. I fixed the problem. You can either remove it yourself using gedit or pico, or download the new script.

---

### Post by DreamcastJack on 2007-06-10
why not just install the broadcom through syneptic? i have  a 4306 chip in mine and it worked perfect for me. it only connects at a 11mps but thats better than going through so much trouble.  if I need alot of speed for a d/l i'll just hook it up to ethernet..

---

### Post by bmartin on 2007-06-10
> **DreamcastJack said:**
> why not just install the broadcom through syneptic? i have  a 4306 chip in mine and it worked perfect for me. it only connects at a 11mps but thats better than going through so much trouble.  if I need alot of speed for a d/l i'll just hook it up to ethernet..
You're thinking of the firmware, which doesn't work for everyone. The person who's currently trying to use this method was unsuccessful with the firmware. It only works for a few chipsets, such as 03 and 06.

My connection ( 4318 ) is flaky with the firmware. It works perfectly w/ ndiswrapper.

---

### Post by DreamcastJack on 2007-06-10
> **bmartin said:**
> You're thinking of the firmware, which doesn't work for everyone. The person who's currently trying to use this method was unsuccessful with the firmware. It only works for a few chipsets, such as 03 and 06.

My connection ( 4318 ) is flaky with the firmware. It works perfectly w/ ndiswrapper.

ah okay, my apologies.

---

### Post by wayno on 2007-06-10
hey there everyone, does this method work for Netgear PCI adapters because then i put in the following

```
sudo ./auto-ndiswrapper.sh
```

I got
ERROR: No inf file found in driver directory!

i put the WinXP .inf and .sys fies in ~/Desktop/autondiswrapper/drivers
are they meant to go there or ~/Desktop/autondiswrapper/ndiswrapper-1.45/drivers

ps. i'm new to linux ~ 3 hours

---

### Post by bmartin on 2007-06-10
The driver should be in ~/Desktop/autondiswrapper/driver, not ~/Desktop/autondiswrapper/drivers.

---

### Post by dudenamedsteve on 2007-06-26
first off, let me just say good job.  i've had previous success with the [BCM43XX firmware script]("http://ubuntuforums.org/showthread.php?t=405990") that you and Darkn00b busted out for all us fine n00b type folks.  But now i'm working on another system with a different Wireless card and i thought i'd use this AutoNDISwrapper that you so kindly made.  i'm getting the following error:

```

* Backing up current configuration
* Installing the necessary compilation libraries
* Removing old ndiswrapper module
* Removing old ndiswrapper
* Compiling ndiswrapper
* Installing ndiswrapper
* Configuring ndiswrapper
**couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper line 217.**
* inserting ndiswrapper module
*** Installation is complete. You may need to restart your computer for the changes to take effect.
```

i'm using your NDISWrapper1.47 script with a USRoboticx MAXg 5411, which is listed as unstable with the BCM43XX firmware.  I'm using the Windows XP driver from the USRobotics website, specifically the two files **BCMWL5.SYS** and **USRMAXG.inf** which i placed in the **\autondiswrapper\driver\** directory.  This is a brand new fresh and clean install of Feisty Fawn.  Any one got any ideas?  Am i just being stupid or what?

oh, and feel free to dumb down any response as i'm still quite n00blike and totally ok with it.
Thanks in advance!

---

### Post by dudenamedsteve on 2007-06-26
Haha, i kid!!

Works just fine, and at a blistering 48Mb/s no less!  Just goes to show that you should probably reboot when told to....silly steve.

again, thanks a super bunch!

---

### Post by McLovin on 2007-07-05
Thanks alot. This actually worked and I can actually move fast.

---

### Post by meth on 2007-08-05
I have used this script and all works fine, but i cant see my wireless card in network manager.

I get:
> 
$ sudo ndiswrapper -l
bcmwl5 : driver installed



> 
$ cat /var/log/syslog | grep ndis
[   31.864000] ndiswrapper version 1.47 loaded (smp=yes)
[   31.936000] usbcore: registered new interface driver ndiswrapper


I have an laptop hp nx9010, using Ubuntu Feisty.

> 
$ lspci
00:09.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)


Any help?? i have used bcm43xx driver for linux and ndiswrapper and no work.

Please help.

---

### Post by bmartin on 2007-08-05
Please see [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by Mancman on 2007-08-07
Hi, I've just updated from Edgy to Feisty, and then found my Broadcom 4306 wireless didn't have the inclination to work any more, even with Ndiswrapper.  (I was using Ndiswrapper on Edgy and working at 54Mbps without any problems)
I then tried the firmware trick from the other post  and finally had it working, but only at 11 Mbps.

So when I saw this post I reckoned I had nothing to lose, so went the Ndiswrapper way again.
The script was stalling at 'Removing old Ndiswrapper files'......probably because they don't exist (??), so I commented out the offending lines and ran it again. This time it completed, and after rebooting...I still only have 11 Mbps, according to iwconfig   :(    

Would it be worth me removing everything and starting again, but with the same version of Ndiswrapper I used on Edgy, or will I be wasting my time ??
It's not urgent, I can live with 11Mbps...but would prefer it to be 'right'.

Thanks in advance.

---

### Post by bmartin on 2007-08-07
Please see [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990). If you need 54Mbps, use the GTK installer program to remove the firmware, then install ndiswrapper.

---

### Post by dkrepitD on 2007-08-09
Hi, I have a Dell Inspiron 8500 (Service tag: 85D7N21) with the Broadcom 4306 in the True Mobile 1300 Mini-PCI Card.
```
Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card
        Flags: bus master, fast devsel, latency 32, IRQ 5
        Memory at faff6000 (32-bit, non-prefetchable) [size=8K]

```
This is what I get after installing the fw, using the method described in the other [post]("http://ubuntuforums.org/showthread.php?t=405990").
```
[   23.120000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   23.120000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   23.120000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
...

```
I can see networks but just can't connect to them. bummer..
So, I try to use the ndiswrapper option, and I get this:
```
* Backing up current configuration
* Installing the necessary compilation libraries


```
and it freezes.
I am not sure, but in your [FONT="Courier New"]install-ndis-broadcom.sh [/FONT]script  are you using the machine's network environment when you execute the apt-get commands? The reason I ask is that I am behind a proxy and I have no other way to connect to the Internet. If not, it would be as if I am not connected to the Internet, and maybe that is why it is freezing? At first I thought that it was just taking a long time, so I left it for 7 hours (went out for a while) but when I got back it was still as described above.
Any ideas:confused:?
Thanks.

---

### Post by bmartin on 2007-08-09
> **dkrepitD said:**
> Hi, I have a Dell Inspiron 8500 (Service tag: 85D7N21) with the Broadcom 4306 in the True Mobile 1300 Mini-PCI Card.
```
Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card
        Flags: bus master, fast devsel, latency 32, IRQ 5
        Memory at faff6000 (32-bit, non-prefetchable) [size=8K]

```
This is what I get after installing the fw, using the method described in the other [post]("http://ubuntuforums.org/showthread.php?t=405990").
```
[   23.120000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   23.120000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[   23.120000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
...

```
I can see networks but just can't connect to them. bummer..
So, I try to use the ndiswrapper option, and I get this:
```
* Backing up current configuration
* Installing the necessary compilation libraries


```
and it freezes.
I am not sure, but in your [FONT="Courier New"]install-ndis-broadcom.sh [/FONT]script  are you using the machine's network environment when you execute the apt-get commands? The reason I ask is that I am behind a proxy and I have no other way to connect to the Internet. If not, it would be as if I am not connected to the Internet, and maybe that is why it is freezing? At first I thought that it was just taking a long time, so I left it for 7 hours (went out for a while) but when I got back it was still as described above.
Any ideas:confused:?
Thanks.
Okay... first of all, the firmware should work for you. If it got to the point where you could see networks but not connect to them, then you're at the point where most people end up having serious problems. Usually working from a fresh install of Ubuntu helps.

Also, I literally run the apt-get (or aptitude) command in bash (the normal terminal) to install the compilation libraries. Without them, you can't compile ndiswrapper. So if you can execute **sudo apt-get install (package)** from your computer successfully, then the script shouldn't have any problems. I'm not using anything unorthodox to install ndiswrapper; it's the same series of steps that you'd find listed on a walkthrough.

You'll find more help if you post to the other thread instead of this one.

---

### Post by dkrepitD on 2007-08-09
Thanks, I will try to re-install Feisty.. although the install is quite fresh :). But I have to admit that some odd things have happened since I installed the OS.
I'll be back... Thanks again.
D

---

