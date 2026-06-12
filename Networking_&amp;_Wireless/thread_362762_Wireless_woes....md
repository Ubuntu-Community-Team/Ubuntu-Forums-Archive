---
title: "Wireless woes..."
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by Naetholix on 2007-02-16
Well... here's another in the long list of poor saps who can't get their wireless to work with Ubuntu Edgy Eft.

I've had many helping hands along the way, including some one-on-one with a fellow Ubuntu-user (though he's still kinda new at it.)  But my wifi still doesn't work and I hope you guys can help me out.

I've installed Ubuntu Edgy Eft and done the update (both of these done twice.)  I managed to use the Synaptic Package Manager to enable Universe and Multiverse options (as my friend said I needed to do) and I did the whole ndiswrapper install and the bcm43xx-fwcutter stuff.  Both times, with no results.  lspci tells me that my wifi card is indeed properly inserted in the motherboard and my wifi card works perfectly in Windows XP, but in Ubuntu, there's no option for wifi in my network manager or network tools.

The key sequence I've recently tried was this:

[I]sudo apt-get install bcm43xx-fwcutter

sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o

sudo modprobe bcm43xx[/I]

That was done using the wl_apsta.o package that my friend said worked for his computer.  He has almost the same wireless card as I.  (Belkin Wireless G Desktop Card.  For the exact chipset model number, I'll have to write down the next time I log into Ubuntu; can't remember it at the moment.)  My LAN card works just fine for the internet, but I have to cart my whole computer upstairs to our router just to get that.

I've tried the ndiswrapper command with a few different drivers I've found off the net.  All with null results.

Added onto this now is the fact that my computer freezes whenever I pop in a CD in Ubuntu.  The CD drive starts up and hovers at the same (low) RPM and the whole thing locks up.  Is this a kernel failure?

I wonder if it's even worth pursuing with Ubuntu, or whether I should try Kubuntu or Xubuntu.  I'm a really persistent bastard when it comes to this kind of thing, so I'd love to find a way to make peace between Ubuntu and my wifi card.  But if it's not possible, why keep pursuing it?

Any input whatsoever is greatly appreciated.  Thanks!

---

### Post by gradedcheese on 2007-02-16
> I wonder if it's even worth pursuing with Ubuntu, or whether I should try Kubuntu or Xubuntu

you'll have the same results: your problems are below the 'desktop' layer, and changing desktops won't make any difference.

when you try these steps (ie: modprobe the driver to load it) do you see anything useful when running "ifconfig" or "iwconfig"?  Perhaps the driver does work but the device isn't configured yet?

---

### Post by Naetholix on 2007-02-16
Here's what I'm getting after I unpack wl_apsta.o and use modprobe:

[I]naetholix@Ubuntu:~$ sudo ifconfig
Password:
eth0      Link encap:Ethernet  HWaddr 00:60:67:3D:00:22  
          inet6 addr: fe80::260:67ff:fe3d:22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:774 overruns:0 frame:9889
          TX packets:0 errors:22 dropped:0 overruns:0 carrier:38
          collisions:323 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5274 (5.1 KiB)
          Interrupt:11 Base address:0x1060 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:324 (324.0 b)  TX bytes:324 (324.0 b)

naetholix@Ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
[/I]

If there's valuable security info in there, I don't really care.  If it helps someone help me, then I'll even post my password if I have to.

---

### Post by Naetholix on 2007-02-16
Oh, and here's part of the data that *lspci* gives me.  It's only the part involving my wifi card.  If extra data would help, I can post it here on request.

***00:10.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)***

---

### Post by gradedcheese on 2007-02-16
no, there's nothing security-related there, and you will never have to post any passwords (don't do that).  anyhow,

iwconfig tells us that there's no WiFi interface.  Lets make sure that the ndiswrapper module is at least loaded:

```

lsmod | grep ndis

```

should return something.  Now you should look at the ndiswrapper guide for troubleshooting steps: there are commands for checking which drivers ndiswrapper has available, and commands for adding/removing as needed.  Unfortunately I can't help much there because I don't use ndiswrapper.

---

### Post by gradedcheese on 2007-02-16
> **Naetholix said:**
> Oh, and here's part of the data that *lspci* gives me.  It's only the part involving my wifi card.  If extra data would help, I can post it here on request.

***00:10.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)***

Wait!  ok, that's useful info!  Atheros chipset, not broadcom... why are you installing broadcom drivers?  Also, that chipset is **supported** out of the box in Ubuntu.  I'm typing this and posting via the same chipset right now!

> 
07:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)


---

### Post by Naetholix on 2007-02-16
Cool!  That means you should know EVERYTHING about your chipset and you can guide me through this easy! XD

How did you get yours to work?

The reason I'm using Broadcom drivers is that Atheros and Broadcom both made versions of the Belkin Wireless G Desktop card.  And the other half of that is that my friend (who has way more computer knowhow than I do) told me that it should work.  Obviously I just got raped.

So if Atheros is supported "out of the box" by Ubuntu, why isn't there even an icon for my wifi card in my networking manager!?

---

### Post by Naetholix on 2007-02-16
Oh, and another bummer is that my GUI freezes whenever I pop in a CD.  I tried using the synaptic package manager to download my ndiswrapper utility, and when it prompted for the CD, I did just that.  The CD goes in, turns on to a low RPM, and the whole desktop locks up.  Might be something wrong with my kernel between Linux and my CD drive?

---

### Post by gradedcheese on 2007-02-16
The way my card works is I plug it in, and everything works automatically :)

Alright, lets solve this WiFi problem first, but as a side note (for the future) you'll now be more proactive: when looking at a WiFi issue, you'll first run lspci to see what chipset you have, then you'll go from there.  The trouble is that network card brands/models don't guarantee a particular chipset, so you have to be careful.  You might need to undo whatever ndiswrapper installation might have done now, though it should be ok I'd guess.

Please take a look at the output of "lsmod" and see if the Atheros module is loaded.  Try:

lsmod | grep ath

and also

lsmod | grep mad

If it's not, we need to modprobe it at least once to see if it will load up and work.  When I get home, I'll check what module supports my chipset, though you can google "linux AR5005G" for now if you want.

(also, we'll get this CD issue resolved, but let do the WiFi first)

---

### Post by Naetholix on 2007-02-16
This is an excerpt from another forum that I came across when I did a google search:

[I]You download the source then extract it, navigate a console to the extracted folder and then type the instructions in the 'INSTALL' file which should be something like (as root) :
```
 ./configure
make
make install
```


after you have done that type (as root) :

```
modprobe ath_pci

```

your wifi adapter should now be ready for use, try to onnect to your access point using the Network Manager in the system tray.[/I]

And another excerpt from a different forum:

[I]1) Have the Alternate CD ready for use.

2) Open a terminal command prompt and type the following:

```
$ sudo apt-get install linux-restricted-modules-`uname -r`
```

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter.

Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.[/I]

Both of these options failed.  The first one gave me an error message fifty miles long:

```
**root@Ubuntu:~/Desktop/madwifi-0.9.2.1# make**
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/naetholix/Desktop/madwifi-0.9.2.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  HOSTCC  /home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:27:19: error: errno.h: No such file or directory
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:29:20: error: string.h: No such file or directory
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c: In function 'uudecode_usage':
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c: At top level:
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:40: error: expected ')' before '*' token
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:70: error: expected ')' before '*' token
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c: In function 'main':
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:121: error: for each function it appears in.)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:188: warning: implicit declaration of function 'open'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/naetholix/Desktop/madwifi-0.9.2.1/ath/uudecode] Error 1
make[2]: *** [/home/naetholix/Desktop/madwifi-0.9.2.1/ath] Error 2
make[1]: *** [_module_/home/naetholix/Desktop/madwifi-0.9.2.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [modules] Error 2
**root@Ubuntu:~/Desktop/madwifi-0.9.2.1# make install**
sh scripts/find-madwifi-modules.sh 2.6.17-11-generic 
for i in ./ath ath_rate/sample ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/naetholix/Desktop/madwifi-0.9.2.1/ath'
test -d //lib/modules/2.6.17-11-generic/net || mkdir -p //lib/modules/2.6.17-11-generic/net
cp ath_pci.ko //lib/modules/2.6.17-11-generic/net
cp: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/naetholix/Desktop/madwifi-0.9.2.1/ath'
make: *** [install-modules] Error 1

```

And the second one did exactly as I said above, even in just the Terminal mode.  I began the installation, popped in the CD, and the whole thing locked up.

So that rules out two options, for now.

---

### Post by gradedcheese on 2007-02-16
you need linux-headers-[name of your kernel here] to build modules.

uname -r

gets you the 'name', now:

sudo apt-get install linux-headers-[put name here]

and then build via 'make' again.

---

### Post by Naetholix on 2007-02-17
YES!!!  With your help, GC, and the help of a few others, I finally managed to get my wifi card working.  It was thanks to all the ideas and suggestions that I kinda stuck 'em all together and made it work.

I ended up using the command you suggested: 
```
apt-get install linux-restricted-modules-2.6.17-11-generic
```
And this time, I popped it in with the Terminal window open.  The processor slowed down, as it did before that, but the cursor kept blinking in the Terminal, so I left it on faith that this bucket of silicon would work.  Sure enough, the CD started spinning at high RPMs and it loaded the restricted modules.  Immediately after, I went to the Networking window, and my Wifi card was visible!  Yay!  I enabled it and rebooted.

However, I had a few troubles with actually getting it to work properly and allow me to use my internet.  I pinged my router and it responded, so I knew I was getting a signal (even though the LED on my wifi card wasn't brightly lit, like it is in Windows).  For one thing, in "Network Tools," when I select my ath0 or wifi0 (it says unknown interface), the "Configure" button lights up, but when I clicked it, it claimed that I didn't have permission to use it (even though I'm the admin of my computer.)

Played around with DHCP and Static IP.  Still nothing more than evidence of a signal.  I only got through when I disabled all of the security settings on my router and deactivated and reactivated my card in Network.  I turned all of my security settings back on, and everything seemed to buzz to life.  I am currently posting via my Atheros AR5005 card on Ubuntu!

Thanks a bunch, GC, for all your help and suggestions, and anyone else who helped along the way.

---

### Post by gradedcheese on 2007-02-17
you're welcome, good job on getting it working.  I haven't upgraded to the -11 kernel yet, so I guess that's why my (identical) card works fine while yours needed a driver compile.  Why the driver compile?  There's an ABI change, among other things, in the -11 kernel, so drivers need to be recompiled specifically with the new kernel's headers (that's that last step you did) in order to work.

---

