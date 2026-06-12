---
title: "Getting jumbo frames working"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by omion on 2006-09-15
Hi everybody

I just got a gigabit switch which supports jumbo frames, and I wanted to get it set up on both my computers. My Windows box was easy, but I'm having a bit of trouble with Ubuntu. Here's what I've done so far:

I thought that a simple "ifconfig eth1 mtu 9000" would do the trick, but that always came back with "SIOCSIFMTU: Invalid argument". It apparently doesn't like an MTU > 1500.

Well, I wanted to try out compiling a new kernel anyway, so I got 2.6.17.13 and deleted the check that was giving the error. (yes, I am very well aware that I shouldn't be hacking the kernel, but it's my test box anyway :grin: )

Now I can set the MTU to anything I want, but if I send any more than 2038 bytes in one frame it will freeze the network connection. I assume there's some buffer somewhere that's 2KB long, and I'm overflowing it.

Not wanting to completely hose my system when I make another guess, I have to ask: is there a better way to do this?


PS. I have an nForce4 chipset, and I'm using the forcedeth drivers. I see in the changelog that version 0.36 added jumbo frame support, but for some reason it's just not working. Maybe there's a setting I'm missing in the driver somewhere?

---

### Post by omion on 2006-09-17
A little update:

I just got a new Mac Mini, and getting jumbo frames set up was just as easy as Windows. I'm now throwing around 9K frames between those two computers.

So now it's only my Ubuntu box that doesn't work with jumbo frames. It's a bit annoying as I really thought Linux would have better support for this kind of stuff than anything else.

Oh, and my nasty hacked kernel for some reason didn't let Apache work correctly, so I'm back to the standard kernel and an MTU of 1500. :( I guess I kind of expected it; I'm still surprised it even booted!

---

### Post by cobray on 2006-10-10
The ethernet card on your ubuntu computer has to be able to support jumbo frames also, in addition to your switch.
it wasnt clear from what i read that you said your interface card supported it.  
maybe thats why you cant set the mtu

sudo ifconfig eth0 mtu 9000

worked for me.

---

### Post by mips on 2006-10-10
And if your card does not support Jumbo frames you should set all your other cards to the lowest common denominator.

---

### Post by WeAreMany on 2008-06-27
Agreed...Same error


sudo ifconfig eth0 mtu 9000

returns 
SIOCSIFMTU: Invalid argument
 

I am using a Chelsio 10GB nic going to a DXS-3250/DEM-442 10GB.  It works fine in Win2k3.

---

