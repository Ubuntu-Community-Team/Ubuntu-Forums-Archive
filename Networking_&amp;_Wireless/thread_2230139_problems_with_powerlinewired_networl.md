---
title: "problems with powerline/wired networl"
date: 2014-06-17
forum: Networking &amp; Wireless
---

### Post by jgw on 2014-06-17
I am having problems with my tp-link powerline connection.  Its strange.  I get the proper lights lit, I can connect to my router from this machine, etc.  I can even connect with my router and bring up its gui (192.168.0.1)  The speed, however, wavers between 50kb/s to 200kb/s which is less than I get with my wireless.  Eventually the connection fails and the speed goes to 0.  

I should mention that I am able to disconnect wireless and goto wired and the other way or leave them both enabled.  this does not seem to make any difference.

Here is some information I have on this:
greg@greg-N61PB-M2S:~$ netstat -ie
Kernel Interface table
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:c2:89:1a  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:606559 errors:10365 dropped:56 overruns:10365 frame:0
          TX packets:427655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:880039898 (880.0 MB)  TX bytes:64501661 (64.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:229257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:229257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72059513 (72.0 MB)  TX bytes:72059513 (72.0 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.114.1.6  P-t-P:10.114.1.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:5647082 (5.6 MB)  TX bytes:240666 (240.6 KB)


Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0

greg@greg-N61PB-M2S:~$ sudo lshw -C network 
[sudo] password for greg: 
  *-network DISABLED      
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2.4
       logical name: wlan1
       serial: 00:23:13:01:e7:38
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated



greg@greg-N61PB-M2S:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRgreg@greg-N61PB-M2S:~$ sudo lshw -C network 
[sudo] password for greg: 
  *-network DISABLED      
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2.4
       logical name: wlan1
       serial: 00:23:13:01:e7:38
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated
IB_DESCRIPTION="Ubuntu 14.04 LTS"
Linux greg-N61PB-M2S 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Thank you..........


Tjaml upi//

---

### Post by TheFu on 2014-06-18
Please edit the first post and use "code" tags - to make it easier to read.

It is a bad idea to have both wifi and wired ethernet enabled concurrently. The routing gets screwed up and I've noticed that the metrics for each connection are less-than-good usually.

BTW, what is the tunnel for? THAT could be interfering.

---

### Post by tgalati4 on 2014-06-18
There is typically a lot of noise in powerlines, so any internet connection is a magic trick.  Anything change recently in your household power?  Using the air conditioner, X10 devices, a neighbor with a large ham radio antenna?  Rewire with a proper ethernet cable and router.

---

### Post by jgw on 2014-06-18
Thank you for the replies.  I have no idea what Code tags are or how to use them.  Here is what I have learned by messing with what I have.  I thought that wireless and wired would mess with each other so I tried them, one at a time and let them run.  I found out that without both of them on, at the same time, my download speeds decrease seriously.  I also contacted tp-link about this and they said that I gotta get rid of the extension cords I am using and plug directly into the outlet.  This means I gotta get some longer 10/100/1000 cables to do that although I suspect that shouldn't make all that difference but this stuff seems delicate so that just may be the case.  

I have also noticed that my connection speeds vary wildly from minute to minute, irregardless of whether both are connected or one is connected.  I am also not sure this is not a problem with sabnzbd (downloader) rather than the system.  It just keeps getting stranger and stranger.  When I run the system monitor, and watch the speed what is graphed has little to do with the numbers on the lower left and the difference is seriously different (MB vs Kb)   Basically it will vary between 0 and up to 1.3MB/s, in some cases in less than a minute.  This will occur no matter how its hooked up.  I use an internet speedteset to engender traffic if nothing else is going on. 

If this was not strange enough when I do a speedtest on the internet (cnet and centurylink), those figures don't agree with anything when one also throws in speedtest-cli it just gets stranger.   then there is sabnzbd itself.  Sometimes it just stops downloading and the speed it reports goes directly to 0.  Then I run an internet speedtest and watch the monitor and there is available bandwidth, not much (200/500 or more) but some.  After a bit it will start up again.  I will goto their forum and ask about that one. 

So, to recap.  When running both (wired and wireless) and disconnect 1 all connections seem to go away and then the one connected may, or may not, start up.  To goto 1 that will work I have to disconnect both and then reconnect 1.  Irregardless of which one I do that with the speed is always less than when both are running. 

My wireless is 2.4gz   My router is a dual band.  I cannot use the 5gz because that would require a different dongle and, from what I have read, that is not exactly easy to deal with on ubuntu.  I also, incidentally, have windows machines running in the same environment, some wired, some not, and working just fine but those that are wireless have access to the both bands.  I have dongles for d-link, realtech, and netgear.  From what I have read they are all a pain in the a**. <G>  The machine I am running with, for my downloads, used to be a windows xp machine.  I switched over because the microsoft xp thing tended to upset.

The tunnel thing is my vpn (pia).  I have, when messing around with this stuff, disconnected it and connected it.  It makes no difference in the connection.  I just had another thought.  I wonder what would happen if I hooked up another router, to a phone line next the the computer that I am having all the problems with.  I don't know what that might do.  My suspicion is that centurylink just might have a fit if I were to do that (my internet comes in through my phone line).

Again - thanks for the input and replies.  I am grateful.  I also suspect I may be overthinking all of this but I am learning stuff along the way.

I find that I was completely and utterly wrong on my assumption that an extension cord would make all that much difference.  I connected two I had so that I could plug directly into the outlet and that made all the difference in the world.  I am now getting my maximum connection speed, without the wireless being connected and the speed seems to be absolutely solid with no wild fluctuations.  I also apologize to anybody who read what I wrote here as I was flat out wrong.  If you thought you were dealing with an idiot you were spot on!! <G>  This stuff is much more delicate than I had presumed.

thanks again to those who offered thoughts...........

---

