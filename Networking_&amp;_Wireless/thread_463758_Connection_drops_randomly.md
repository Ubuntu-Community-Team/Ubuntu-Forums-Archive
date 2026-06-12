---
title: "Connection drops randomly"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by DarkGob on 2007-06-04
I switched to Ubuntu about a week ago, and although it's been a steep learning curve, I've managed to work through all of my problems except one -- the random internet drops.

This started happening, from what I recall, the very first time I used Ubuntu, so unless it's a huge coincidence I doubt it's my ISP.  I was having no problems under Windows XP prior to my switch either.  (I had just spent roughly 3-4 hours downloading updates on my new XP install prior to switching.  Guess why I decided to switch.)  Restarting will fix my connection until the next drop.  It seems to happen about 1-3 times per day.  My network card is a 3Com 3C905C-TX Fast Etherlink.

---

### Post by x64Jimbo on 2007-06-04
You could start by switching to Ndiswrapper for the driver. This might fix your problem.

---

### Post by DarkGob on 2007-06-04
Is that just a wireless driver?  (Based on the description in SPM.)  My connection is strictly wired.

I was hoping that this would be a known problem, otherwise a fix probably won't come easily.  Oh well.

---

### Post by Frankenchrist on 2007-06-04
Since it's your wired NIC doing this, I've created a thread to try and round-up all possible incidences and solutions for this.

[http://ubuntuforums.org/showthread.php?t=463588](http://ubuntuforums.org/showthread.php?t=463588)

---

### Post by Adapted.Cat on 2007-06-04
DarkGob,
  The first thing to figure out is where exactly the connection is dying. It could be the link between your cable/dsl/whatever modem and the outside world (is there a fault light blinking on your modem - does restarting the modem fix it?) or it could be the link between your modem and your machine. This could be:
[LIST=1]
[*]Wiring - is it a good cable?
[*]Connection - if you have some sort of ethernet splitter (especially those simple Y-splitters), switch or hub, take that out and connect directly - does that help?
[*]Software - If you're on Cable, you're probably running a DHCP client to negotiate a session with the modem. If you're on DSL, you may be using pppoe to negotiate a session through the modem with the ISP servers. In either case, has this client died, or is there anything in the logs? Does running '/etc/init.d/networking restart' solve the problem? If so, look at what it's doing when you run this command.
[/LIST]
I used to have no end of problems because my Cable provider occasionally changed my IP address, and my DHCP client just didn't know how to cope. The good news is that there are lots of good clients out there so whatever your ISP is doing you can find away around it. No matter how you connect, note how long the session should be valid for (according to the logs).

Another alternative is to get a cheap hub that has a dedicated port for the cable/dsl modem - then the hub can do the negotiation with the modem, and all you have to do is tell it what kind of modem it's talking to.

Finally, I doubt very much that it's your wired NIC having problems, unless you have reason to believe it's faulty. The 3COM cards have been very well supported on Linux for over a decade.

Good luck!

---

### Post by DarkGob on 2007-06-04
Oh yes, that's one detail I left out.  Unlike when there's an actual internet outage (during a snow storm for instance), my modem lights don't change at all when my connection drops.

I'm connected directly to the modem, so there's no hub or splitter involved.

The wiring, last I checked, is fine.  I haven't really done anything with it since I built this computer 2 years ago.

I haven't really had any problems with my ISP prior to this.  There have been some reports of outages in the past couple of months as Time Warner did some upgrading to the systems they acquired from Adelphia, but I've only hit upon these once or twice in that time, always late at night, and restarting didn't fix the problem as it does here.  And that might not even be an issue anymore, I haven't really been paying attention.

I went into Network Tools and configured it with a static address as opposed to DHCP.  So far all is well but it's only been a few hours so that really means nothing.  I'll keep an eye on it for the next few days and see whether or not I lose my connection again; if not, I'll come back and say so.

On a final note, I've seen people post these logs that you've mentioned, but I don't know where to find them.

---

### Post by x64Jimbo on 2007-06-04
If you are connected directly to the modem, unless the modem has a built-in router, you need to change it back to DHCP IP address. The ISP will not allow you to arbitrarily assign yourself an IP. 
One way to tell if the modem is a router is to turn on DHCP and see what IP you get. If it starts with 192.168, you are behind a router. If anything else, you're on the public net. Even if you are behind a router, you should probably let the router do the assignment of IPs. Most of the time you will get the same IP you had before because of the way that DHCP leases work, but you don't want to force it to do something that it may not want to do. Try changing back to DHCP and see if that fixes it. 
Curious: why did you go static in the first place?

---

### Post by DarkGob on 2007-06-04
I should clarify, I was having this problem with DHCP, which is why I tried switching to static.  Really, it was just a shot in the dark because I only half know what I'm doing.

It didn't work anyway.  I woke up this morning to find Gaim disconnected.  I might try spending a day on my Windows drive to see if the same thing is happening there, although somehow I doubt it.

---

### Post by DarkGob on 2007-06-04
I had a thought -- could this be a problem with my lease renewing?  If so, how would I go about determining that?

---

### Post by DarkGob on 2007-06-05
Well, it seems as though it's not renewing the lease when it should be, assuming the problem is early epiration.  The system log says this every time I lose my connection:

```
Jun  5 01:22:52 chris-desktop kernel: [  507.836194] NETDEV WATCHDOG: eth0: transmit timed out
```

My connection information, oddly enough, does not change, I just lose the ability to use any service that connects to the internet.  I've also tried restarting my connection with 'sudo .etc.init.d/networking restart' (a command I've found from digging around on this forum), and to all outward appearances it works fine, but it doesn't change anything.

Is everybody really just clueless about this?  It's extremely frustrating to be losing my internet connection every few hours.  I don't want to say that it would drive me completely back to Windows, but it certainly might make me use it more often, because this is ridiculous.

Please, somebody at least say "I don't know" so I know I'm not being ignored.

---

### Post by psychoelf on 2007-06-05
I'm finding that is seems to be a widespread issue after searching the forums for a solution.  Haven't found one yet, but having the same issue here with my wired connection.  Everything worked perfect before the last update and everything still works perfect in Windows.  Post if you find a fix.  Good Luck.

---

### Post by DarkGob on 2007-06-05
More info after latest drop:

dmesg | grep eth0 yields:
```
[   32.374763] eth0:  setting full-duplex.
[   51.560374] bridge-eth0: enabling the bridge
[   51.560489] bridge-eth0: up
[   51.560588] bridge-eth0: already up
[   51.560696] bridge-eth0: attached
[   59.852659] eth0: no IPv6 routers present
[12642.950775] NETDEV WATCHDOG: eth0: transmit timed out
[12642.950783] eth0: transmit timed out, tx_status 00 status 8681.
[12642.950793] eth0: Interrupt posted but not delivered -- IRQ blocked by another device?
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:01:03:E7:ED:59  
          inet addr:76.50.8.204  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::201:3ff:fee7:ed59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:543408 errors:0 dropped:0 overruns:2033 frame:0
          TX packets:55766 errors:4 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:127306547 (121.4 MiB)  TX bytes:6335452 (6.0 MiB)
          Interrupt:19 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2259 (2.2 KiB)  TX bytes:2259 (2.2 KiB)
```

---

### Post by DarkGob on 2007-06-06
[Well, I guess this is a confirmed bug, at least as far as 3Com cards go.]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109629")

*sigh* Looks like I also picked a bad time to switch to Ubuntu...

---

### Post by DarkGob on 2007-06-06
Downgrading to previous kernel 2.6.20-15 doesn't fix the problem.  Not that I expect anyone to respond, but is this a bug that was in kernels previous to -16 or am I afflicted with a different problem entirely?  Perhaps a voodoo hex?

Hmm...maybe a healthy dose of fire would do the trick...

---

### Post by x64Jimbo on 2007-06-07
If I can recommend anything, it would be to stick with it when things get hard. Linux has a steep learning curve, but the view from the top is SO worth it. I am sorry I can't help you with your specific problem - I hope you are able to find a resolution.

---

### Post by psychoelf on 2007-06-07
I'm dual booting, so I still have a working machine.  I have no intentions of dropping Ubuntu as its the best distro I've used for a newbie.  I just hope this problem gets some better recognition so it can be fixed.

---

### Post by procco on 2007-06-07
I too hope this problem gets resolved as it is annoying.  I recently upgraded (clean install) from 6.06.1 LTS to 7.04 and Network Manager randomly tells me I've been disconnected from the network.  In my case it does reconnect automatically which is a good thing.  I never had an issue with 6.06.1LTS.  I guess I subscribe to the adage: if it ain't broke, fix it till it is.

---

### Post by thepeted on 2007-06-13
I had a similar problem (connection would drop from my f5d7050 usb dongle and then reboot required) but I fixed it by connecting from the command line, rather than using kubuntu 6.06s wireless assistant (wlanmanger).  

Reading round, it seems that many recommend disabling or removing the network manager app, although this app wasn't installed to start with mine.

Not sure whether this helps, but noticed the network manager thing wasn't mentioned here.

---

### Post by stupor on 2008-03-22
sorry i have the same problem mine only lasts 30 to 40 sec still says conected only starts on a reboot have you had any luck

---

