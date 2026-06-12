---
title: "Can I downgrade from 11.04, to 10.10?"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by NonStop on 2011-05-04
I';m having issues with 11/04 at the moment, and if they can't be fixed, I'll need to revert back 10.10. How can I do this? I have all my data stored on the laptop harddrive, and don't want to run the risk of deleting it. I can't copy any of my data either to an external harddrive because I am rather poor!

---

### Post by matt_symes on 2011-05-04
Hi

Do you have separate home and data partitions or just one large partition ?

How much important data do you have ?

Kind regards

---

### Post by NonStop on 2011-05-04
One large partition, and tens of gigs of data.

---

### Post by TBABill on 2011-05-04
If your root partition is separate from your /home partition, then you can reinstall 10.10 but do NOT select to format the home partition. This is very risky no matter how great your machine or you are if you do not back up your data in some way. Can you copy to DVD or some other media? At least your most important files? Any glitch along the way can bork the entire thing and you'd be very upset if you lost data over an OS. I'd recommend sticking to 11.04 if you have no way of backing up your data first. You can go into Synaptic and install any desktop you want (LXDE, XFCE, KDE, etc.) so if you don't like Natty you can still use another. I personally installed Lubuntu and really am enjoying how fast it is and how basic it is. This is a far safer alternative unless you are confident you'll get it right and that if you lose your data you can tolerate the loss.

---

### Post by MasterProg on 2011-05-04
Why do you want to downgrade? Do you really need to do that?

---

### Post by matt_symes on 2011-05-04
Hi

If you dont have separate data or a home partition then you are out of luck unless you can back to DVD's or somesuch as TBABill highlighted.

Next time create a separate home and maybe some data partitions for your data.

What issues are you having with 11.04 ? Maybe the best way is to fix those.

Kind regards

---

### Post by bowens44 on 2011-05-04
Wouldn't that be an upgrade?   ;-)

---

### Post by NonStop on 2011-05-04
Thanks for the replies people saving data seems key, will look into that. How would I check what partitions I have? 

And finally, this is why i want to downgrade, no one has been able to solve my issue; [http://ubuntuforums.org/showthread.php?p=10768968#post10768968](http://ubuntuforums.org/showthread.php?p=10768968#post10768968)

---

### Post by wolfen69 on 2011-05-04
> **NonStop said:**
>  How would I check what partitions I have? 



```
df -h
```

---

### Post by dwhite on 2011-05-04
Much less technical but maybe relevant....perhaps try booting into ubuntu classic (get the gnome desktop back that way) and see if that helps with the problems you are having.

---

### Post by TBABill on 2011-05-04
In the event you cannot reinstall without borking your data, just open a terminal window, type in ```
sudo lshw -C network
``` and yes, that's a capital C, then press enter. Copy what the terminal responds with and paste it back here. Also do the same with ```
lspci
``` if it's an internal wireless device and ```
lsusb
``` if it's USB. That will at least identify some info we'd need to help get the wireless going instead of reinstalling. I think you just didn't have the right responses to your post to get it going. Hang in there...plenty of experienced users to help you get it going.

---

### Post by NonStop on 2011-05-05
> **TBABill said:**
> In the event you cannot reinstall without borking your data, just open a terminal window, type in ```
sudo lshw -C network
``` and yes, that's a capital C, then press enter. Copy what the terminal responds with and paste it back here. Also do the same with ```
lspci
``` if it's an internal wireless device and ```
lsusb
``` if it's USB. That will at least identify some info we'd need to help get the wireless going instead of reinstalling. I think you just didn't have the right responses to your post to get it going. Hang in there...plenty of experienced users to help you get it going.

Thank you man, really need help on this, here is what you said for the first one, wans't sure whether to go for the firts ro second one after that:

ian@ian-laptop:~$ sudo lshw -C network

[sudo] password for ian: 

Sorry, try again.

[sudo] password for ian: 

  *-network               

       description: Wireless interface

       product: AR2413 802.11bg NIC

       vendor: Atheros Communications Inc.

       physical id: 5

       bus info: pci@0000:04:05.0

       logical name: wlan0

       version: 01

       serial: 00:19:7e:57:9e:45

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg

       resources: irq:19 memory:c3000000-c300ffff

ian@ian-laptop:~$

---

### Post by Tanargbob on 2011-05-11
I also intend to go back to Ubuntu 10.10. Tried 11.04 and have to use Gnome classic as I have a modern graphics card and Unity does not work. My microphone stopped working and it worked fine before the upgrade, now I am having problems logging onto the PC.
I think that I should downgrade before I lose everything. I thought that Ubuntu was becoming easier for Windows users with every release, but 11.04 has smashed that theory.

---

### Post by CaptainMark on 2011-05-11
however much data you have that cant lose, if you have this amount of space also free then you can use a live cd to shrink your main partition, make another and move your data over to it, then reinstall 10.10 on your main partition, urgh, its long winded but basically if less than half of your hard drive is full then your able to reinstall 10.10 without losing everything

or you could do the cheeky thing of setting up a bunch of free cloud storages and saving all your data online, ubuntu one, dropbox, etc most of them give about 2gigs free
(presuming you can hardwire to the interweb thingy for the transfer of course)

---

