---
title: "Ubuntu 7.10 Live CD and Fresh Install - differences?"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by jasonbrisbane on 2008-04-14
Hello,

I have a dlink dwl-G510 wireless PCI adapter which detects  (lspci) as ra2500/rt61pci. 
Yes, both drivers appear to be loaded for it. (thats what lsmod says anyway).

When I boot the live cd of ubuntu, the network manager loads the correct driver and connects to the WPA network, and stores the key in ther keyring.
Wonderful, I say, it all works.

I then run a fresh install, repartitioning the HD (no trace of any OLD files remaining from previous Ubuntu installs), and reboot the PC.
When the PC comes back up, it doesnt detect the network. Strange I say, so I left click on NetworkManager and create new network, enter all the details and the network icon just spins - no activity at all.

After 15 mins of trying, it pinged once and connected, stayed up for 8-10 seconds and dropped to 0% connection and thereby dropped again to spin.
I left it for 8 hours and no activity , connection, or error. It never returned with  the monitor with 'x' indicating no connection.
I loggoff and back in again - network manager is an applet running in the session, so restart the session. Now lshw shows multiple connections wlan0, wmaster0 (and localhost, of course). wmaster0 has no driver and no connection (because it doesnt exist AFAIK). The keyring has never worked on this PC outside of the Live CD environment either. Perhaps this is because the networkmanager isnt returning a successful connection, thus the keyring is never given the chance to store it.

So my question is, why would the Live CD work perfectly, first time, as is, and the install work so differently as to be unusable? Is a different driver loading? Should I be blacklisting somedrivers that the Live CD doesnt load?

All testing I have found on the install shows that all details for lspci, lshw, modlist, ifconfig, etc are all correct as to what it should be (ie what it is compared to other dlink wireless card users on this and other forums,...).

Note, however that I cant post the exact output of the commands as the PC doesnt have any working net connection. I could boot into the LiveCD and get the connection, but it isnt showing the details from the non-working connection then, is it!

Any advise on where to go would be **greatly **appreciated...

Regards,
Jason Brisbane

---

### Post by greenstar on 2008-04-14
I found this post that may prove useful to you:
[Useful resources for beginners setting up your wireless connection]("http://ubuntuforums.org/showthread.php?t=596797")

---------------------------------------------------------------------------------------

If that do[COLOR=DimGray]es[/COLOR]n't help you, the following is what I'll need to get started helping.

Is there a way you can connect via ethernet?

Without being able to see the output of the commands, I don't know that I can help much, as I won't have enough to work with. 

We need to see what you can see, to an extent.

The rest of us need to get up to speed on this, so let's find out which chipset your hardware has and which driver is loaded.
Post the output of:
```
lspci
``````
lsmod
```If you must use the live cd to get online and you have a flash drive, you could boot into your install, paste the output of the commands to a text file and copy it to your flash drive so you can access the info and post it here. (That will be a PITA, I know.) Since it's just text, a floppy would probably also do just fine if you don't have a flash drive.

Greenstar

---

### Post by jasonbrisbane on 2008-04-15
OK, here goes.

I'm manually typing the results in on my laptop, which I've moved next to the 'server' which I'm trying to get wireless.

```
$ lspci
00:0e.0 Network Controller: RaLink RT2561/RT61 Rev B 802.11g

$ lsmod
<snip>
rt2x00pci                      11520  1   rt61pci
rt2x00lib                       19584  2   rt61pci, rt2x00pci
rfkill                               8208   1   rt2x00lib
<snip>
eeprom_93cx6           3200    1   rt61pci

```



And I've reformatted and reinstalled the server again to remove any trace of "tampering" that I've done.
I've followed:
all the howto's that are stickied in these forums and also in the linux.org forums too.

I'm at a loss as to how to get the wireless to work.'

I might have to resort to booting off the livecd and trying to get apache/php/mysql to install and run off the Hard drive (which is available as /media/xxxxx), but I dont know how modifying the /etc directory will go(!).

Can you assist?


EDIT:
OK, I've booted into the Live CD but the network connection only stays up for about 10 seconds (without activity) before loosing it, retrying. It connects once or twice but eventually falls over. Not good for a future web server.... (Once I get it DHCP, I'll use the Router to give a consistent IP address (easy to do), and thus I dont have to fiddle with other settings in linux. I just have to get the card staying up.


BTW I'm connecting via WPA - we dont trust too many people here in Australia!

Is any assistance available?

---

### Post by greenstar on 2008-04-17
Whoops! I forgot to click Submit Post. Sorry for the delay.

It's possible that your wifi card is not working correctly. It happens.:( If it were mine, I'd swap out that card and get on with it instead of messing around trying to get a possibly defective card to work until every option is exhausted. I guess your take on that will depend on how you view the time/money equation.

Good luck,

Greenstar

---

