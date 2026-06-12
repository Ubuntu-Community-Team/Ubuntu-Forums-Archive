---
title: "broadcom: tried every thread here..."
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by stevieb on 2007-04-20
... but no luck.  here's some code:

```
steve@darwin:~$ lspci | grep Broadcom
01:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
steve@darwin:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

steve@darwin:~$ ndiswrapper -l
bcmwl5 : invalid driver!
bcmwl5.inf : invalid driver!
bcmwl5.sys : invalid driver!
steve@darwin:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

before i upgraded to feisty, wireless was working; although dapper and edgy said it was a 4319 card, not 4311.

any help appreciated.

-steve

---

### Post by yotux on 2007-04-20
Have you downloaded the drivers for your broadcom card?  What type of system do you have.

More info and I will try to help.

I have installed my broadcom card in my HP dv6000

Nathan aka yotux

---

### Post by stevieb on 2007-04-21
yes, the driver is there- bcmwl5.inf

feisty says my card is a 4311; dapper and edgy said it was a 4319.

system is a lenovo 3000 c100 laptop
thanks,

-steve

---

### Post by bmt on 2007-04-22
It might be an idea to open up the cover on the back of the machine and see what the wireless card really is.  At least you would then know which direction to go with ndiswrapper.

---

### Post by stevieb on 2007-04-23
well, it wouldn't make any difference, would it?  i mean, no matter which 43xx card you have- 4318, 4319, 4311- whether you use fwcutter or ndiswrapper, you always end up with the same bcmwl5 driver, right?

i have to say, though, that under feisty, this card doesn't perform as well as it did under dapper/edgy.  maybe i'm wrong about the above...

-steve

---

### Post by bmt on 2007-04-23
> **stevieb said:**
>  you always end up with the same bcmwl5 driver, right?
Agreed, but at the moment, you don't know where the fault is coming from.  If we assume that the wireless card is still reporting its pci id correctly, then there is a problem with your pci id lookup list -- should be easy to fix.

Although the same driver is used, I'm sure there are different parts within it that are only applicable to some cards -- selected by pci id, I wouldn't be surprised.

The pci id is not completely infallible -- mine reports itself as a Dell something-or-other card, but it isn't in a Dell and never has been -- it's an OEM (Lenovo) Broadcom 4311, but the pci sub-system information has been attributed to Dell.  These pci ids can be submitted publicly, so errors can creep in, even by innocent (i.e., not malicious) means.  Have a look at the [pci id repository]("http://pciids.sourceforge.net/").

---

### Post by josephus on 2007-04-23
the ndiswrapper drivers are definitely installed incorrectly.  you should remove them using

```
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -e bcmwl5.inf
sudo ndiswrapper -e bcmwl5.sys
```

and when you install the drivers again use

```
sudo ndiswrapper -i <driver_name>
```

the driver_name being the .inf file, and where upper/lowercase counts.  and to check if the driver installed correctly use ndiswrapper -l, and it should output : driver installed, hardware present (in some variation)

---

### Post by stevieb on 2007-04-23
I definitely have a 4319 card in there.  i now remember i got this working in dapper and edgy using bcm43xx-fwcutter and wl_apsta.o.

so now i need to know how i undo what i did before (bcm43xx-fwcutter and bcmwl5), then I think what bmt is telling me is i need to tell feisty that my card is a 4319.

thanks so far for the help; can we keep going on this for me?

-steve

---

### Post by bmt on 2007-04-24
Try this variation of lspci:```
lspci -nv
```
This will give the raw pci id (the main id and the subsystem id) for everything in your system.  One of the sections will have 01:02.0 near the beginning (taken from your lspci output in your original post) and will contain the string '14e4:*xxxx*'.  The '14e4' identifies the device as Broadcom, the 'xxxx' is the card type (or a code for the card type) as reported by the card.  The subsystem details will include a similar string, which may be customised by the OEM.

At this point, I Googled the pci id and went from there, but my 4311 card is widely documented, so it wasn't a very difficult task.  I am no expert, but I'll give moral support where I can! ;)

---

### Post by stevieb on 2007-04-24
lspci -nv:

01:02.0 0280: 14e4:4319 (rev 02)
        Subsystem: 14e4:044a
        Flags: bus master, fast devsel, latency 128, IRQ 23
        Memory at c0002000 (32-bit, non-prefetchable) [size=8K]

So now, how do I get Feisty to recognize it as a 4319?

thanks,

-steve

---

### Post by bmt on 2007-04-24
> **stevieb said:**
> yes, the driver is there- bcmwl5.inf
Just backtracking a bit, you have bcmwl5.sys (or similar) in the same directory, I hope?

---

### Post by stevieb on 2007-04-25
bump...

---

### Post by bmt on 2007-04-26
Yes, still here.  My last post was as a result of a Google search on the 'invalid driver' error.

I can only suggest making sure that you have the latest drivers from the Lenovo website and starting again with ndiswrapper.  Blacklisting the bcm43xx module shoud be sufficient to prevent it from interfering, I think.

---

### Post by bmt on 2007-04-26
I know it's not specifically about your card, but [this Ubuntu document]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?action=fullsearch&value=linkto%3A%22WifiDocs%2FDevice%2FBroadcom+BCM4311+rev+01+%28ndiswrapper%29%22&context=180") has some useful tips for dealing with common problems.

See the part towards the end of Step 5, 'We can also look inside the directory where the drivers get stored by ndiswrapper:'.  It may be possible to force the use of 14e4:4319 that way, for example.

---

### Post by josephus on 2007-04-26
i'm a little bit confused, as i thought the 'invalid driver' error with ndiswrapper had nothing to do with whether your card is being detected as a bcm4319 instead of 4311.  that error is just to do with the fact that the drivers aren't being installed correctly.  for example if i randomly try to install a non-existent driver, it'll give that result.
```

$ sudo ndiswrapper -i tesr2
installing tesr2 ...
couldn't open tesr2: No such file or directory at /usr/sbin/ndiswrapper line 174.
$ ndiswrapper -l
net5211 : driver installed
        device (168C:1014) present (alternate driver: ath_pci)
tesr2 : invalid driver!
```

properly installing a driver that doesn't properly correspond to the hardware returns a different message.  

```
$ sudo ndiswrapper -i bcmwl5.inf
$ ndiswrapper -l
bcmwl5 : driver installed
net5211 : driver installed
        device (168C:1014) present (alternate driver: ath_pci)
```

make sure that you are either in the same directory as where the drivers are located or use the full path when issuing the sudo ndiswrapper -i <driver> command.

---

### Post by stevieb on 2007-04-26
do i need to use ndiswrapper?  i have always used bcm43xx-fwcutter with wl_apsta.o.  if i switch to ndis, do i need to undo bcm43xx-fw, or can i just delete the drivers in /lib/firmware?

thanks,

-steve

---

### Post by deadlines on 2007-04-26
I had issue after issue with my BCM4318 chipset, then I finally ditched the bcm43xx drivers and switched to ndiswrapper & wicd for my connection manager and everything works great now.  To be fair, the fellows working on the bcm43xx drivers state specifically what bcm chipsets have issues with their drivers, and they are reverse engineered so it's a tough haul I imagine.  I may revisit the bcm43xx drivers at a later date.

Btw, this post has a nice ndiswrapper package with an easy install script, worked like a charm for me:

[http://ubuntuforums.org/showthread.p...hlight=BCM4318](http://ubuntuforums.org/showthread.p...hlight=BCM4318)

After I downloaded the ndiswrapper drivers from the post above, I performed the following steps:

Uninstall of bcm43xx package

sudo rmmod bcm43xx (probably not necessary once you reboot)

sudo modprobe ndiswrapper

Installed wicd from the .deb off their site: [http://compwiz18.ig3.net/wicd/wb/pages/releases.php](http://compwiz18.ig3.net/wicd/wb/pages/releases.php)

Added /opt/wicd/tray-edgy.py as a startup program and rebooted

Haven't had any troubles since then, although the wicd systray applet seems a little quirky when you first boot (probably because it's geared for Edgy, I expect an update will clear that up) it just seems to be a refresh issue because as soon as I crank up Opera and the icon appears in the systray, the wicd icon also appears.  Once you get everything installed and reboot, just run a quick "sudo ps -A | grep daemon.py to ensure the wicd daemon started correctly, and you should be ready to rock.

Incidentally, I'm not certain that using wicd as the connection manager makes the difference, I'd be curious to know if simply using ndiswrapper drivers w/ network-manager would work as well.  I really like network-manager-pptp for VPNing, but until I can get stable with it this will suffice.

Good luck.

---

### Post by kyle_fransham on 2007-04-26
> **deadlines said:**
> 
Incidentally, I'm not certain that using wicd as the connection manager makes the difference, I'd be curious to know if simply using ndiswrapper drivers w/ network-manager would work as well.  I really like network-manager-pptp for VPNing, but until I can get stable with it this will suffice.


I'm quickly coming to the conclusion that Network-Manager is the problem.  I did everything I could for my BCM4306 chipset, and my best results were some spotty connections with bcm43xx-fwcutter.  I got fed up and installed wicd, (without changing any ndiswrapper settings) and now I can connect no problem to all of my networks.

stevieb: I'd recommend trying ndiswrapper with network manager first, then if that doesn't work, try it with wicd.  You can just uninstall bcm43xx-fwcutter with
```

sudo aptitude remove bcm43xx-fwcutter

```

Then, just add bcm43xx to your /etc/modprobe.d/blacklist file.  (Just writing "blacklist bcm43xx" (without quotes)  on it's own line at the end of the file is sufficient)  This will prevent the bcm43xx module from being loaded on startup, and has the advantage of being easily undoable.

---

### Post by belekas on 2007-04-27
ndiswrapper installed successfully, says driver ok hardware present. im using same card bcm4318. but still doesnt work i cant scan or do anything manualy or with script help. anyone have a clue? with native driver it dont work so i swithed to ndis but it still dont work, anyone can point me out?

im using fujitsu-siemens laptop, and my wifi led is off i cant turn it on because the wifi button is inactive in linux, in windows it active and works straight. anyone has a solution?

thank you

peace

---

### Post by deadlines on 2007-04-27
Are you using network-manager or Wicd?  If you're not using Wicd, you should give that a shot now that you've got your ndiswrapper drivers set up.  

Just uninstall network-manager: 

```
$ sudo apt-get remove network-manager
```

Then snag the .deb from [Wicd's site]("http://compwiz18.ig3.net/wicd/wb/pages/releases.php") and install.

Oh, and you'll want to add Wicd's systray icon on startup (instructions are in the Wicd page's FAQ section on how to do this).

Good luck to you.

---

### Post by bmt on 2007-04-27
> **belekas said:**
> ... wifi led is off i cant turn it on because the wifi button is inactive in linux ...
It is normally necessary to boot into Linux with the wireless switched on (hardware switch).  I don't think any laptop software switches work well.

Look at the results from iwconfig and iwlist scan -- if the results look wrong, try putting any messages in Google.  (Try Google search beginning 'site:[www.ubuntuforums.org](www.ubuntuforums.org) ...'.)

---

### Post by stevieb on 2007-04-27
Hey guys,

no dice w/ ndiswrapper and accompanying drivers.  wouldn't even list eth1 in ifconfig.  I think the best bet for me (4319) is bcm43xx-fwcutter and wl_apsta.o.  wicd didn't work for me, either- just gave me a blank popup window with no text, no nothing- and the toolbar buttons were inoperative.

another thing I thought of- what about replacing the pci.ids file with the one from Dapper?  would that give me back the better performance of the 4319 under Dapper?

-steve

---

### Post by josephus on 2007-04-27
can you give us more indication of what went wrong with ndis? pls post:

```
ndiswrapper -l
lshw -C network
dmesg

```

for dmesg if you can just post the portion related to loading up the driver.  if you unload and reload ndis (sudo modprobe -r ndiswrapper && sudo modprobe ndiswrapper) then look at dmesg it should be the last couple of lines that we are interested in.

---

### Post by stevieb on 2007-04-27
i've already uninstalled ndiswrapper, but here are the other two things:

lshw:

```
*-network:1
       description: Wireless interface
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@01:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:9c:78:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic ip=192.168.1.6 latency=128 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0002000-c0003fff irq:23
```

dmesg:
```

[   41.772000] eth1: no IPv6 routers present
[  134.584000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  176.880000] SoftMAC: Open Authentication completed with 00:15:05:ec:ad:21
[  176.888000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  182.704000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  183.204000] SoftMAC: Open Authentication completed with 00:15:05:ec:ad:21
[  183.208000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  199.332000] eth1: no IPv6 routers present

```

---

### Post by josephus on 2007-04-27
so what's wrong now?  you  have an ip assigned, can you ping the router?

---

### Post by stevieb on 2007-04-27
well, the wireless is working- the reason for this post is that the reception and speed are not as good as they were in Dapper; I thought this was due to the pci.ids file- it shows eth1 as a 4311, while Dapper read it as a 4318.

-steve

---

### Post by josephus on 2007-04-27
oh. i don't think that was clear from your earlier post.

i don't think that changing pci.ids will help, i'm pretty sure that that file is just to make things human readable.

---

### Post by stevieb on 2007-04-27
sorry about the confusion!

so pci.ids is a file generated by ubuntu, and doesn't tell ubuntu what to do, right?  

-steve

---

### Post by Jorsher on 2007-04-27
Feisty was using the 43xx driver, and it was not working.  When I used ndiswrapper on the linux driver, it would say "no hardware" in ngtk for that driver.  Had to force ubuntu to use the new driver and now I can get online.  I posted about it.

---

### Post by itsjustasensation on 2007-04-28
> **Jorsher said:**
> Feisty was using the 43xx driver, and it was not working.  When I used ndiswrapper on the linux driver, it would say "no hardware" in ngtk for that driver.  Had to force ubuntu to use the new driver and now I can get online.  I posted about it.

(Lenovo 100 C100)

Same, Feisty was using 43xx ... blacklisted that then ran ndiskgtk, attempted to install the windows XP driver for my 4319 which told me "no hardware present" ... Rebooted, wireless light came on:

```
$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4319) present (alternate driver: bcm43xx)

```

So apparently ndisgtk did actually work.

```

$ lspci -nv

01:02.0 0280: 14e4:4319 (rev 02)
        Subsystem: 14e4:044a
        Flags: bus master, fast devsel, latency 128, IRQ 23
        Memory at c0002000 (32-bit, non-prefetchable) [size=8K]

```

Shows up as 4319 as it always did.

```

$ lspci | grep Broadcom
01:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
adam@lenovo:~$ 

```

But that still shows it as 4311 as it always did.

I'm connected wirelessly using WPA & all is working well.

---

### Post by stevieb on 2007-04-28
i had the same result using bcm43xx-fwcutter- 4319 in lspci -nv, 4311 in lspci | grep Broadcom

-steve

---

