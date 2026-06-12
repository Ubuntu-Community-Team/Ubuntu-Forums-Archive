---
title: "(Wired) Network very unstable, disconnects randomly"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by melissawm on 2007-06-07
Hi guys,

I'm using Feisty in my University computer, I have a fixed IP and for the last week or so have experienced network problems. I get constantly disconnected, stay disconnected for about 20-30 seconds, and get reconnected automatically. This is really annoying, as I work with several pieces of software that need a network connection to obtain license keys (MATLAB, for instance)... 

I've tried searching the forums but couldn't find anything like this... I don't know for sure, but could it be happening after an upgrade? Or is it just random? Please help me as this is really annoying, and I'm an experienced Linux user but I know nothing about networks... Please help :)

---

### Post by swoll1980 on 2007-06-07
How were you able to set you ips? I cant set mine I get disconnected when I use my own ips

---

### Post by melissawm on 2007-06-07
Yes, I have the right IP, DNS, Gateway etc, checked and double checked, I'm connected normally for about 1 hour and then the connection just drops for about 30 seconds. This happens every hour so...

---

### Post by melissawm on 2007-06-13
Help... It's not the cable; it's not IPV6; the only thing I notice is that in /etc/hosts , along with localhost, there should by my host name. However, even after I put it manually as

127.0.0.1 localhost myhost

and save, if I look for it later all I have is 

127.0.0.1 localhost

Could this be it? Why does it not save my hostname? I've tried manually putting it into /etc/hosts, and I've tried putting this in the network configuration GUI in "static hosts" or something (my kubuntu is in french...) Is this a bug? I have the same version of kubuntu at home in my laptop, with no problem at all...

---

### Post by kah00na on 2007-07-27
I have a laptop that has a physical wire going to my router and I can see that when I get "disconnected", the link light on my laptop goes off.  It looks like it a problem with the actual internal card going on and off... not the router.  Weird.  Perhaps this is what is happening to you?

---

### Post by buntunub on 2007-07-28
I am experiencing the same issue. Anyone have an answer or workaround yet?

---

### Post by damianpeterson on 2007-08-01
I'm having a similar problem.

My network connection disconnects every 10 seconds or so and immediately reconnects. I have no idea whether this is time-based or data-based or something else.

I connect to a router and have another computer that connects to the same router without issue so it's definitely my computer that has the problem.

Strangely, my problems only seem to happen in the mornings and go away after a couple of hours. As I write this it is 9am and the network is disconnecting only every couple of minutes or so.

So far I've only noticed this issue since using 7.04 but this could be coincidence. I didn't have this issue with 6.06 and 6.10.

Here is an example of a couple of syslog entries:
Aug  2 08:55:07 nice-desktop kernel: [ 4244.693840] sky2 eth0: Link is down.
Aug  2 08:55:09 nice-desktop kernel: [ 4246.355655] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both

I'm at the limits of my knowledge now so if anyone can make sense of these symptoms please let me know.

Cheers!

---

### Post by curly_nostrill on 2007-08-06
Me too.

I first noticed this condition while copying files to my FreeNAS file server via ssh through Nautilus.  The network disconnects for a few seconds then reconnects automatically.

When I'm lucky, the transfer finishes eventually.

When I'm unlucky the transfer times out and Nautilus pegs the CPU to 100%!  I then have to kill Nautilus.

This happens on my Feisty upgrade and on a new Ubuntu Studio install using the same /home on a separate partition.

I'm suspecting something in my /home folder is awry?

I reinstalled nautilus (and a few other related items) and the problem seemed to go away for a little while after a reboot but then started acting up again. 

I've seen several bug filings for similar situations but I don't see any fixes.

It's exasperateing.

---

### Post by zer0slash on 2007-08-06
Similar problem here. I just installed Feisty a few days ago. I noticed connection problems even when I had the live cd/desktop interface. This problem seems to occur after bootup. Connected...Disconnected over and over. 

I go into the network settings, uncheck and check eth1, save, exit, open a browser window and after a minute it finally connects and seems to stay connected after that.

I have a Toshiba PCX2500 cable modem. I have tried 2 network cards, plugging the ethernet connection directly(which fails), so I have to use the SMC ethernet to usb adapter(provided by ISP) and connect to the motherboard's embedded network adapter

Once I get connected things are ok. If I have to restart, it starts all over again. The driver provided is a Pegasus.

I am at my wits end with this.

---

### Post by damianpeterson on 2007-08-27
OK, I managed to fix my problem. It turned out to be the router and/or the router's power supply. Replacing both of them fixed my problem. I doubt this will be the same problem as others here are experiencing but thought I'd better post this just in case.

Good luck.

---

### Post by hom2it on 2008-02-23
i have this problem randomly with 7.04
I have a dual boot PC - so after doing the usual rebooting router, changing cable etc. booted with windows and there was no problem (while it strikes randomly when I boot with Ubuntu). So its definitely something to do with the software (network manager?).
Dont see any solutions though ...help....is there anyone out there..

---

### Post by JoshuaJamZ on 2008-03-06
Not sure if this will help anyone else posting in this thread, but perhaps it will help someone browsing as I was when I ended up here :lolflag:

I've been having an issue with very frequent disconnects while trying to transfer data between a Windows machine and Ubuntu Gutsy amd64. The same issue with both WinXP and Server 2003 on an older machine. Was so bad that I had to cross my fingers while transferring a mere 200 MB or so.

I have had the two machines networked on a router and with a crossover cable. Using either Samba shares or Xampp on the Win machine produced the same results with the disconnects.

The current configuration is the crossover cable on a Realtek RTL8139, 2003 Server, shared to the Gutsy 64 AMD machine...

Changing the shared connection with the crossover cable on the Win machine to 100 Half Mode seems to work:

```
Start>Control Panel>Network Connections> Right Click, Properties on shared device> Configure>Advanced Tab
```

Then:

```

Link Speed/Duplex Mode Value to 100 Half Mode.

```

I also set Network Address to 192.168.0.1 and changed the Receive Buffer from 64 to 32.

I had forgotten about reading this somewhere sometime back... cannot recall if it was here or not, though :?: ...Seems to have solved my current issue for now.

The Shared Realtek device is PCI, btw... I know there are configuration settings for the device accessible at boot, but I have not checked them... could something be set wrong here to cause issues with full-duplex?

---

### Post by |Eric| on 2008-04-26
Help!! 
i have same problem i keep getting disconnected since i moved to Xubuntu 7.10 
i noticed that Apps->System->nework keeps erasing settings each time i have this problem i need to reapply teh profile (had to save one because of the repeating about avery 5 min ) 

now i saw a few thing im probalby gona try 
how can i specify my DNS i tought it was in resolv.conf ? (gets changed too !!) 


any hints please post !

---

