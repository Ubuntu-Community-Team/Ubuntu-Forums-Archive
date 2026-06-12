---
title: "eth0 breaks when X loads"
date: 2005-04-05
forum: Networking &amp; Wireless
---

### Post by sharky on 2005-04-05
Hi there,

I have just installed hoary on an ACER 1600 with a Realtek8139. I can ping the machine whilst it's booting (from a second machine -all my machines have static ip's), but as soon as it gos into X it times out. During install it configured eth0 and was able to use it (to contact sources). During boot, it configures the interfaces and checks the DNS and the time without errors.

So, anyhow. I've cat the lot, and eth appears in ifconfig. dmesg looks fine. Route is cool and the eth0 appears with ifconfig. DNS is configured correctly (in resolv.conf) and it thinks it has an eth0. however, eth0 don't work once X is up and running. If I try and ping, it gives me Destination Host Unreachable. 

Pinging the machine works right up until the moment X loads.

Oh, and the only weird thing is when i 

cat messages ¦ grep eth

loads of these messages:

(date and time) (hostname) kernel: NETDEV WATCHDOG: eth0: transmit timed out.

However, the fact that the machine still thinks eth0 is up is too weird.


Please help me so that i can finally recommend Linux to my friends without fear of having to spend the rest of my life supporting them.

Cheers :evil: 

P.S.

Yes, yes i have, yes it is, and yes i did. anything else? Please? does it have to do with ipv6? if so, i don't know how it works. HELP.

UPDATE:

i have been able to apt-get install update by booting into root terminal etc. however, when i gdm it goes tits up agian.

---

### Post by alastair on 2005-04-05
Not sure what's going on, and it's late here but ... rather than just say it all looks OK, please also post details.

i.e.

ifconfig -a
route -n

Have a closer look at :

/var/log/syslog

and make sure nothing odd (ethernet/eth etc.) is printed in there.

You could always stop X/GDM from starting by removing it from the init scripts i.e.

update-rc.d -f gdm remove

and reboot, see what happens if X does not start.  Think before doing this step.

See : man update-rc.d (to put things back if you need to).

---

### Post by Zwack on 2005-04-05
I'm afraid I'm with Alastair on this one...  I don't have enough info to go on... 

ifconfig -a, netstat -ian and netstat -r would help.  The other things I would be interested in knowing are what else is happening on your box at the same time.

Use the init scriptss to stop GDM (from a text console).  Does the ethernet port come back?  If so then do a tail -f on /var/log/syslog press return a few times and switch to a second console...  login and run startx.  X should start up.  Does the network card stop again?  If so logout of X and check the syslog output.   Anything at all in there?

I'm wondering if it is a problem with the network card and graphics card trying to use the same piece of memory... But I'm just guessing at the moment.

Z.

---

### Post by sharky on 2005-04-06
thanks for getting back to me. I dont want to waste your time. Here are the logs you requested (attached).

from the syslog i can see that IRQ #19 is being disabled when gdm or (xdm or whatever) boots. IRQ #19 is the interrupt for the ethernet card.

I'm now guessing that this is an ACPI problem (or similar). What do you think? If this is the case, is there a way forward?

---

### Post by sharky on 2005-04-06
ok, here's weird update.

because gdm breaks eth0, i stopped gdm autoloading at startup.

That means i can use apt. I've allready done a dist-upgrade.

So, i've installed, kernel 2.6-10 686, fglrx (plus dev), gstreamer, development tools and xine.

I reboot after configuring fglrx

start gdm

and eth0 is working. IPv6 is enabled.

---

### Post by alastair on 2005-04-06
Well done for sorting it out.

The :

irq 19: nobody cared (try booting with the "irqpoll" option.
...

messages are very suspicious. A kernel update and/or ACPI would be the things to look at. To test the ACPI theory, you could :

 - boot the old kernel as is, see if the problem returns
 - boot the old kernel but add "acpi=off" to the kernel args - see if the problem goes away

Anyway, good to hear things are working now.

---

