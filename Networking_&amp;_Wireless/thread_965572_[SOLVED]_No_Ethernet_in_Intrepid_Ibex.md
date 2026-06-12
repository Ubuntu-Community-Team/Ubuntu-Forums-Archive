---
title: "[SOLVED] No Ethernet in Intrepid Ibex"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by klausner on 2008-10-31
[SIZE="4"]I have a Sony Vaio VGN-Z530N with the final release version of 8.10, Intrepid Ibex installed (actually, I had the beta, and then installed all the updates last night.) Wireless worked from the start, but I can't see the Ethernet port. If I boot an older Hardy Heron live CD, it sees the Ethernet, but the wireless would (I presume) require configuration and setup. 

When I do an ifconfig, there are no eth ports shown at all. If I go to network setup from the menu, no wired ports show up. I know there was an Ethernet driver bug in the Intrepid beta, but I thought it was going to be fixed before final release.

How do I get the box to see the Ethernet port?
:confused:[/SIZE]

---

### Post by JFo NZ on 2008-10-31
After upgrading to 8.10 my ethernet stopped. You might have the same problem. This is how I fixed it.

Edit /etc/network/interfaces

```
sudo gedit /etc/network/interfaces
```

Add 2 new lines to "/etc/network/interfaces"

```
auto eth0
iface eth0 inet dhcp
```

Then restart machine. Fixed.

---

### Post by river2884 on 2008-10-31
sorry, this distribution is pathetic for networking.

---

### Post by ruminant1 on 2008-11-02
thanks a bunch for the fix.  Same thing happened to me.  I could get the interface up manually, but this fixed it automagically on boot.

Now if only I could get X to work - so far Ibex isn't a winner for me.

---

### Post by Deadowl87 on 2008-11-02
I have the same problem but it's both wireless and wired not working, and it looks like I already have those 2 lines in there.  any advice?


EDIT

it looks like I can browse the home network, but no internet connection, which is odd since I haven't changed anything

---

### Post by klausner on 2008-11-03
> **JFo NZ said:**
> After upgrading to 8.10 my ethernet stopped. You might have the same problem. This is how I fixed it.

Edit /etc/network/interfaces

```
sudo gedit /etc/network/interfaces
```

Add 2 new lines to "/etc/network/interfaces"

```
auto eth0
iface eth0 inet dhcp
```

Then restart machine. Fixed.

Nope. did the above. Still no ethernet.

---

### Post by Wolfhere on 2008-11-04
I read through the bug reports on this. If you edit the /etc/network/interfaces file to simply read -  

auto eth0

with no interface (iface) line as mentioned above. then reboot...Wired Connection works...at least for me.

:guitar:

---

### Post by klausner on 2008-11-04
> **Wolfhere said:**
> I read through the bug reports on this. If you edit the /etc/network/interfaces file to simply read -  

auto eth0

with no interface (iface) line as mentioned above. then reboot...Wired Connection works...at least for me.

:guitar:

Thanks, but that made no difference. Still no wired connectability.

I did discover that if I enter:> sudo lshw -C network
 it tells me that the eth0 port is UNCLAIMED, which suggests a missing driver, but I have no idea where to get a Linux driver for this box from, or how to install it

---

### Post by klausner on 2008-11-05
I think I solved it. Installed the latest set of patches for 2.6.27-7 last night, and now the interface comes up and seems to be working. Reading through the thread for my controller on Launchpad suggests that it wasn't fixed until the -7 release, and experience suggests that it was actually the recent update that really did it.

---

### Post by farazhussain on 2008-11-10
> **Wolfhere said:**
> I read through the bug reports on this. If you edit the /etc/network/interfaces file to simply read -  

auto eth0

with no interface (iface) line as mentioned above. then reboot...Wired Connection works...at least for me.

:guitar:


This worked in one go for me ... thanks!

Best Regards.

---

### Post by klausner on 2008-11-10
FWIW, there seem to be at least two separate problems with Ibex and wireless. Some are solved as above, but systems with the Intel 2200BG networking can't do encryption with 8.10. See [these]("http://ubuntuforums.org/search.php?searchid=51297568") threads.

---

### Post by charonred on 2008-11-10
throwing my 2 cents in;
 did a variance on above instructions;

first edit the network interface
> sudo gedit /etc/network/interfaces

changed the auto lo entry to eth0
> auto eth0
iface lo inet lo

when I rebooted my USB stick (8.10 live CD installed) I had network connected; but checking the settings again and it had reverted to
> auto lo
iface lo inet lo
strange, but network connection keeps working even after several reboots.

---

### Post by Deadowl87 on 2008-11-11
I've tried everything so far with no luck.  However, when I type
```
sudo lshw -C network 
``` it says the interfaces are disabled.  Is there some command to enable it?  when I look at the Network configuration GUI and try to edit the settings, it says 'Never' next to it (which I guess means never connect?) and then I try to edit it, and it tells me it's read only.  Also, is there a way to install the updates without internet?  I'm hoping maybe a recent update has fixed it.

---

### Post by Baldorcete on 2008-11-12
I think i have your some problem, Deadowl, see here: [http://ubuntuforums.org/showthread.php?p=6154891](http://ubuntuforums.org/showthread.php?p=6154891)

¿Seems the same?

---

### Post by Deadowl87 on 2008-11-12
Looks like it.  I guess I'll wait for a solution over there.

---

### Post by tsucol11 on 2008-11-12
> **JFo NZ said:**
> After upgrading to 8.10 my ethernet stopped. You might have the same problem. This is how I fixed it.

Edit /etc/network/interfaces

```
sudo gedit /etc/network/interfaces
```

Add 2 new lines to "/etc/network/interfaces"

```
auto eth0
iface eth0 inet dhcp
```

Then restart machine. Fixed.

Problem fixed. I needed both lines to get connected to the web. Tried the first line alone but with neg results. I can't see the network yet but hey work in progress.

I appreciated  the "sudo gedit /etc/network/interfaces" line as I am on a steep learning curve.

Thanks
Brian

---

### Post by Deadowl87 on 2008-11-12
Well Having the 2 extra lines helped the wired, however, I tried to do the same thing to the wireless, by just typing wlan0 instead of eth0 and it still doesn't work.  Also, under Network connections, wireless is listed under wired as:  ifupdown (wlan0). does that explain anything?

---

