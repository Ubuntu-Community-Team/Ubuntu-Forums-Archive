---
title: "[SOLVED] NetGear MA401 Not Working"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by crzydimnd on 2008-05-27
Hello everyone,

I am new to Ubuntu, though not entirely new to Linux (though it's been a long time since I've used Linux, so I should probably just be considered a Linux noob).  

I have searched high and low on this question, and have not been able to figure anything out, so here goes:

I just installed the latest version of Ubuntu Desktop (8?) on an HP Pavilion ze4400 Laptop.  First of all, I had trouble with even installing it, because when the wireless card was inserted, it would always freeze starting up.  Once I figured that out, I just removed the wireless card while it was starting up and installing so at least I could get into the OS.

Once in, I figured out that the memory probe was causing problems, so, from a page on the Wiki, I edited /etc/pcmcia/config.opts to change the memory range that it scans.  This fixed the system hanging whenever I inserted the wireless card, but now I just can't get it to detect the card.

Here's my details:
The card is a Netgear MA401 (pretty sure it's just MA401 not MA401RA, but not positive on this, as I can't get any information on the card from Ubuntu)

The card was working fine in Windows XP before I wiped the laptop clean and installed Ubuntu.

On the advice of the hardware compatibility list ([https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)), I installed pcmcia-cs and wireless-tools, and on the advice of another post, I installed wlan-ng.  

I have tried other things, but when they don't work, I revert back so I'm hopefully not causing conflicts.  

If anyone has any suggestions, I would greatly appreciate the help.  Once again, I'm a Linux newbie, but not a computer newbie by any means, so I can understand the technical language.

---

### Post by mapes12 on 2008-05-27
Hi

> The card was working fine in Windows XP before I wiped the laptop clean and installed Ubuntu.

As you probably know this isn't any reassurance in Linux.

The card has a listing here:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)


Please could we have a look at your driver ```
sudo lshw -C network
```

BTW: This is important:

> The card is a Netgear MA401 (pretty sure it's just MA401 not MA401RA, but not positive on this, as I can't get any information on the card from Ubuntu do you have any documentation with the card to confirm either way please.

---

### Post by unutbu on 2008-05-27
Hello crzydimnd, I'm not terribly good at networking questions, but to get us moving in the right direction, please post

```
sudo lshw -C network
```

It will give us info about what linux understands to be your card, and if any driver has been loaded.

---

### Post by crzydimnd on 2008-05-27
Thanks for your replies!  Here is what the command outputs:

 *-network
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a4:c0:b3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half ip=192.168.12.70 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=10MB/s


As you can see, there is no entry for my wireless card.  I did the thing where you type trail (or something like that - still learning the commands), and when I inserted the card into the slot, it detected the card, but didn't give any information on what type of card or anything like that.

And no, unfortunately, I don't have any documentation on this card - the laptop was handed down to me by my mother-in-law, so I don't have much but the hardware itself.  If it's worth anything, the card itself says MA401, not MA401RA.

---

### Post by unutbu on 2008-05-27
Does your card look like this: [http://wiki.splitbrain.org/wlan:netgearma401](http://wiki.splitbrain.org/wlan:netgearma401)

There is a different picture + a short spec sheet here: 
[http://www.fulton.net.au/images/ma401_big.jpg](http://www.fulton.net.au/images/ma401_big.jpg)
[http://www.fulton.net.au/wirelessfaq.htm](http://www.fulton.net.au/wirelessfaq.htm)

---

### Post by crzydimnd on 2008-05-27
> **unutbu said:**
> Does your card look like this: [http://wiki.splitbrain.org/wlan:netgearma401](http://wiki.splitbrain.org/wlan:netgearma401)

Yes it does! So does that mean it's the RA?  That could be why I'm having so much trouble....

btw, I used to be able to run 'cardctl' in my terminal, but now it says that command isn't found.  When I did run cardctl ident, I just got socket 0, no product information.

EDIT:  Mine DOESN't have anything after the model number on the back (no Rev. D or anything else)  Now I'm confused.

---

### Post by mapes12 on 2008-05-27
> On the advice of the hardware compatibility list ([https://help.ubuntu.com/community/Ha...rkCardsNetgear](https://help.ubuntu.com/community/Ha...rkCardsNetgear)), I installed pcmcia-cs and wireless-tools, and on the advice of another post, I installed wlan-ng.


I found this thread:

[http://ubuntuforums.org/archive/index.php/t-109173.html](http://ubuntuforums.org/archive/index.php/t-109173.html)

You seem to have done everything anyone else could do and the card still doesn't work. Like the results others have experienced.

Have you considered getting a supported card:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

---

### Post by unutbu on 2008-05-27
> **crzydimnd said:**
> Yes it does! So does that mean it's the RA?  That could be why I'm having so much trouble....

Let's work under the hypothesis that it is an MA401RA. Manufactures often leave out these details because they are not important for mainstream users, even though it can mean a great deal for linux users.

> 
btw, I used to be able to run 'cardctl' in my terminal, but now it says that command isn't found.  When I did run cardctl ident, I just got socket 0, no product information.


cardctl is part of the pcmcia-cs package. To check that you have it installed, do

```
apt-cache policy pcmcia-cs
```

> 
EDIT:  Mine DOESN't have anything after the model number on the back (no Rev. D or anything else)  Now I'm confused.

If Netgear is willing to leave off an RA, I wouldn't be surprised if they'd leave off Rev. D. We'll just have to make a guess. If it doesn't work, we'll make another guess, and so on...

---

### Post by crzydimnd on 2008-05-27
Yeah, that's the post I was referring to.  So, just so I'm sure, is this the MA401, or the MA401RA?  

I will look into getting a supported card, but if I can get this one working it would be nice (plus, it's a nice re-introduction to Linux for me.)

When I type tail -f /var/log/messages, this is what I get when I insert the card:
May 27 14:31:23 gene-laptop kernel: [ 3998.495313] pccard: PCMCIA card inserted into slot 0
May 27 14:31:23 gene-laptop kernel: [ 3998.495334] cs: warning: no high memory space available!


So it's detecting when I insert it (and the light goes on), it just doesn't know what to do with it, which makes me think I might not have the drivers installed correctly.

---

### Post by unutbu on 2008-05-27
I'm not familiar with editing /etc/pcmcia/config.opts to "change the memory range that it scans". Since the entries on [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear) (for MA401RA) don't seem to indicate such a thing is necessary, I would suggest you try removing that line (or commenting that line out with a pound (#) sign). 

Try instead adding

```
"exclude=irq3"
```

Then reboot. Let's hope the computer doesn't freeze and recognizes the card and loads either the orinoco or hostap driver.

3 out of 4 entries at [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)  say the hostap driver works better than the orinoco driver. So perhaps you should try the advice posted here: [http://ubuntuforums.org/showpost.php?p=979625&postcount=2](http://ubuntuforums.org/showpost.php?p=979625&postcount=2)

If that doesn't work, tell us about it and we'll go from there.

---

### Post by crzydimnd on 2008-05-27
I got the editing config.opts from this location:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Under 3.1.3 "System Locks Upon Card Insertion"

I'll try changing it back to the original, and do exclude=irq3 and see what happens. Will report back...

---

### Post by unutbu on 2008-05-27
I am not an expert, but that advice (to me) sounds suspiciously like saying, "You won't have any more problems with your kernel if you just delete your kernel."

---

### Post by crzydimnd on 2008-05-27
> **unutbu said:**
> I am not an expert, but that advice (to me) sounds suspiciously like saying, "You won't have any more problems with your kernel if you just delete your kernel."

I'm not sure what you mean there.  I tried changing it back to the original settings, and I get the same problem.  Computer locks up when I insert the card.

So, I'm going to put that info back in, cuz it's the only way I can get the damn thing to even work when the card is inserted.

I'll try blacklisting orinoco, but I think I tried that before to no avail.

---

### Post by unutbu on 2008-05-27
Ok, since I don't know the answer, (unless some kind reader has a better idea), getting this thing to work is going to require some luck, some patience and some guessing. If you are game, I suggest editing /etc/pcmcia/config.opts, adding the lines

include memory 0xd0000-0xdffff
include memory 0xc0000-0xcffff
include memory 0xc8000-0xcffff
include memory 0xd8000-0xdffff
exclude irq 3
exclude irq 4
exclude irq 7

Also do the blacklisting stuff described [http://ubuntuforums.org/showpost.php?p=979625&postcount=2](http://ubuntuforums.org/showpost.php?p=979625&postcount=2).

Reboot and test if linux detects your card by typing
```

sudo lshw -C network
```

---

### Post by crzydimnd on 2008-05-27
Well, no dice.  The issue here is that, I don't think Ubuntu is even able to figure out that my card is a wireless card, let alone which driver to use with it. I'm stumped.

EDIT:  I posted this in reply to the earlier message.  I will try your suggestions and get back.

---

### Post by crzydimnd on 2008-05-27
Ok, I did what you said, and now it shows up in lshw!!  However, it's not showing up in the network manager, and it doesn't have a logical name associated with it (like my wired connection is eth0 - there's not logical name listed under the card)

Out of curiosity, what does excluding irq's do?

---

### Post by unutbu on 2008-05-27
> **crzydimnd said:**
> Ok, I did what you said, and now it shows up in lshw!!  
Please post the output of the lshw command?

> 
Out of curiosity, what does excluding irq's do?

You know how on a bus there is a cord you can pull to tell the driver you would like him to stop? 
As I understand it (and I may be wrong) each piece of hardware (your keyboard, mouse, hard drive, wireless card,...) on your computer has a cord (IRQ) which it can pull to tell the kernel it wants to speak to the kernel. When a piece of hardware pulls its cord, the kernel is interrupted. Pull too often (or improperly) and the kernel is interrupted forever -- resulting in a computer that hangs.

There are too many pieces of hardware and too few cords (IRQs run from 0--15 on x86 systems). So various pieces of hardware have to share the same IRQ. Some pieces of hardware do not behave properly when forced to share the same IRQ. The 'exclude irq' lines are telling the computer (BIOS? kernel? I'm not sure) not to assign IRQs 3,4 or 7 to the wireless card.

---

### Post by unutbu on 2008-05-27
The IRQ lines are addressing the hanging issue. To that extent they are serving the same purpose as the modified "include memory" lines that you have been using.

Maybe -- if we are lucky? -- you can remove the "include memory" lines, and the "exclude IRQ" lines will do the job of preventing the hanging problem.

Would you please try that?

---

### Post by crzydimnd on 2008-05-27
> **unutbu said:**
> Please post the output of the lshw command?

Here you go:


*-network               
       description: Card
       product: ISL37300P
       vendor: NETGEAR MA401RA Wireless PC
       physical id: 0
       version: Eval-RevA
       slot: Socket 0
  *-network
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a4:c0:b3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half ip=192.168.12.70 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=10MB/s

---

### Post by crzydimnd on 2008-05-27
Success!!!

Apparently, all I needed to do was insert those 3 lines, excluding irqs 3, 4, and 7.  You rock, unutbu!

Unfortunately, I don't have any wireless networks currently in range to fully test the card, but here's my lhsw output now:

 *-network               
       description: Card
       product: ISL37300P
       vendor: NETGEAR MA401RA Wireless PC
       physical id: 0
       version: Eval-RevA
       slot: Socket 0
       resources: irq:11
  *-network
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a4:c0:b3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half ip=192.168.12.70 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:09:5b:10:cf:a8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.3.6 link=no multicast=yes wireless=IEEE 802.11b



I see that it's using orinoco, which I'll go back and change (I removed the blacklist stuff to make sure I wasn't having problems with that), and we'll see how it goes.  But at least we're off and running!

---

### Post by unutbu on 2008-05-27
Yeah! I have to go now, but if you post I'll try to answer when I get back.

---

### Post by crzydimnd on 2008-05-28
Just coming back to mark this thread as solved.  I set my computer up on my wireless at home (which is a secure network) and it worked like a charm!  The signal strength leaves something to be desired, but that's the card's problem, not the software - it didn't get very good signal strength in Windows either.  I'll probably end up getting a new one when I have the money, but thanks again for all your help!!

---

