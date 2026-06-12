---
title: "Slow wireless and wired internet Ubuntu 7.10"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by dnordell on 2007-10-19
Hi! Installed Linux recently and Internet works fine at the office, but with my home WLAN it's quite another story. I have a 11G Wireless ADSL router 54MB, and have tried to connect to internet both with and without "wire". Loading web pages takes about 20 sec. Internet works fine with Windows though. 

I've tried to read all the posts but I'm hoping that it colud be easier to fix than with Ubuntu 7.04. If anyone have any ideas please reply. This is what i get when i type:

iwconfig :
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:64:2D:FA:81   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=92/100  Signal level=-41 dBm  Noise level=-41 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:361   Missed beacon:0 

ifconfig: 
eth0      Link encap:Ethernet  HWaddr 00:16:D4:9E:21:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

eth1      Link encap:Ethernet  HWaddr 00:13:02:34:69:1A  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::213:2ff:fe34:691a/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:13 errors:0 dropped:370 overruns:0 frame:0 
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:33680 (32.8 KB)  TX bytes:20072 (19.6 KB) 
          Interrupt:18 Base address:0x2000 Memory:54000000-54000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:800 (800.0 b)  TX bytes:800 (800.0 b) 

 ping -c 4 google.com :
PING google.com (64.233.187.99) 56(84) bytes of data. 
64 bytes from google.com (64.233.187.99): icmp_seq=1 ttl=241 time=142 ms 
64 bytes from google.com (64.233.187.99): icmp_seq=2 ttl=241 time=138 ms 
64 bytes from google.com (64.233.187.99): icmp_seq=3 ttl=241 time=139 ms 
64 bytes from google.com (64.233.187.99): icmp_seq=4 ttl=241 time=144 ms 

--- google.com ping statistics --- 
4 packets transmitted, 4 received, 0% packet loss, time 3000ms 
rtt min/avg/max/mdev = 138.835/141.240/144.116/2.301 ms


:confused:

---

### Post by jlombs on 2007-10-19
I am having the same issue man - I don't know what is going on.  Connecting to my shared drives totally sucks now

---

### Post by Suchthefool on 2007-10-19
im also having the same problem but the wireless just isnt working. its picked up the card and ndiswrapper appears to be working perfectly but it just wont let me connect wirelessly. and when its wired its just really slow ](*,)

---

### Post by Chriis on 2007-10-19
Since upgrading to Gusty (fresh install) my internet is realy slow too

The speed is up to 15-20 kbps for 5 sec then drop to zero,..re up and redown ect..

before gutsy my speed was about 150kbps !! :confused:

---

### Post by emanububu on 2007-10-19
I Upgraded to Gutsy and there is a delay in http of about 20 seconds then works by bursts

strangely the 'link download' (with DownloadThemAll extension for example) does not have the same problem

Should I reload my 7.04?

:confused:

---

### Post by kkovach on 2007-10-19
Same here.  Upgraded to Gutsy today and my wired network is very slow.  I'm no networking expert, but I ran Wireshark to see if anything jumped out at me.

I'm seeing lots of messages about incorrect checksums in nearly everything I am sending?  Anyone know if that's normal or not?  Doesn't sound normal.  Looking closer it only seems to be happening in HTTP and DNS traffic with my IP as the source.

---

### Post by jlombs on 2007-10-19
> **Suchthefool said:**
> im also having the same problem but the wireless just isnt working. its picked up the card and ndiswrapper appears to be working perfectly but it just wont let me connect wirelessly. and when its wired its just really slow ](*,)

for the wireless, did you put in your wep passphrase as the actual word  - I did all kinds of stuff before I remembered that.

---

### Post by Najmudin on 2007-10-19
I have the same problem also with my wired connection after installing Gutsy 7.10 on it , first i thought something is wrong with the network configuration , but it isn't .
i installed fresh Gutsy on my laptop also and its the same problem , slow internet as hell:x
What should we do in this case filling a bug report or what ?????!!!!!!
I'm thinking of a hidden security program or a firewall in Gutsy that making the connection so slow ...   :-k
I was using feisty fawn with a fast connection but with gutsy ???!!!!!
But I'm sure they are going to solve this issue as so many people are complaining about it.

---

### Post by emanububu on 2007-10-19
I did some more testing:

the problem exists also from the 7.10 RC live CD (shows how much I trusted ubuntu before installing it: i did not test the 7.10 RC fully, obviously)
it does not exist in the 7.04 live cd/ install

the wait before displaying any page 'feels like' a DNS problem caused by some security mechanism new to 7.10

hope this helps

:(

---

### Post by jlombs on 2007-10-19
> **Najmudin said:**
> I have the same problem also with my wired connection after installing Gutsy 7.10 on it , first i thought something is wrong with the network configuration , but it isn't .
i installed fresh Gutsy on my laptop also and its the same problem , slow internet as hell:x
What should we do in this case filling a bug report or what ?????!!!!!!
I'm thinking of a hidden security program or a firewall in Gutsy that making the connection so slow ...   :-k
I was using feisty fawn with a fast connection but with gutsy ???!!!!!
But I'm sure they are going to solve this issue as so many people are complaining about it.

yeah - it is just driving me nuts - I want to know what it is.

---

### Post by jlombs on 2007-10-19
> **emanububu said:**
> I did some more testing:

the problem exists also from the 7.10 RC live CD (shows how much I trusted ubuntu before installing it: i did not test the 7.10 RC fully, obviously)
it does not exist in the 7.04 live cd/ install

the wait before displaying any page 'feels like' a DNS problem caused by some security mechanism new to 7.10

hope this helps

:(

Thanks for posting this - I was going to do a total reinstall - now I will wait

---

### Post by oji-sama on 2007-10-19
I had (or quite possibly still have after reboot) the same problem. 

I also think it's somehow related to DNS. 

I'd suggest testing two things. 

1. test setting the DNS IP-address manually, for example openDNS ones are listed below:
208.67.222.222
208.67.220.220

System -> Administration -> Network -> DNS, delete the one that you have (perhaps write it down first...) and enter the ones above instead. (you could try the DNS of your service provider also if you know it) [https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

2. update the firmware on your ADSL-modem if you're using one. For some strange reason 7.04 worked nicely with my ADSL box, but 7.10 doesn't. I was using the openDNS to surf with a bit less delay, but tried to update the box, and now the problem is gone... (but like I said, I haven't restarted yet, so it's possible that the slowness creeps back. Hope not)

UPDATE: I confirmed that the problem disappeared (on my machine, your situation may be different) after I updated the firmware of the ADSL-box (and using the openDNS worked also, but since I didn't edit any files, the DNS was overwritten each time the network service updated itself. Before the firmware-update I had tried to disable the IPv6, but that didn't help, or I didn't do it correctly.

---

### Post by henriksultan on 2007-10-19
I have the same problem... kinda sucks... In windows and Ubuntu 7.04 i where up to 1meg/s and now...around 77kb/s... wtf... need this fixed.

But buffering videos at youtube seems to work? somthing is very wrong...

---

### Post by vinater on 2007-10-19
I'm glad I found this thread thought i was going nuts.... I thought it had to do with DNS but now I'm thinking IPv6 may be the culprit. I'll let you all know if i find anything.

Mike

---

### Post by henriksultan on 2007-10-19
> **vinater said:**
> I'm glad I found this thread thought i was going nuts.... I thought it had to do with DNS but now I'm thinking IPv6 may be the culprit. I'll let you all know if i find anything.

Mike

Plz do :) I will do the same but dont count on it since I kinda sucks at computers...

---

### Post by henriksultan on 2007-10-19
> **oji-sama said:**
> 

1. test setting the DNS IP-address manually, for example openDNS ones are listed below:
208.67.222.222
208.67.220.220

System -> Administration -> Network -> DNS, delete the one that you have (perhaps write it down first...) and enter the ones above instead. (you could try the DNS of your service provider also if you know it) [https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)


This worked for me, now all seems fine... we will se after a reboot... but great work man :guitar:

---

### Post by jlombs on 2007-10-19
> **henriksultan said:**
> This worked for me, now all seems fine... we will se after a reboot... but great work man :guitar:

gave it a try didn't really help and I think it cranked my Samba connections even more.  

Back to the drawing board - thanks for the research and suggestion

---

### Post by FLCLFan on 2007-10-19
I have the same problem. If this isnt fixed soon im going to have to go back to windows. :(
The network manager also doesnt save any of my setting i put in.

---

### Post by rpasell on 2007-10-19
I'm also having a problem with slow Internet response.  When upgrading to Gutsy, I thought it was just bogged down servers, but all pages are rendering extremely slowly even after the upgrade.

I've tried disabling IPv6 and adding the OpenDNS entries statically.  Neither helped.

---

### Post by FLCLFan on 2007-10-19
Anyone? Theres 1200 members online and no one knows what the problem is?

---

### Post by jlombs on 2007-10-19
I am guessing we just have to wait it out.  We are working at least.  Some people don't even have that going on.  Those with the networking superpowers will eventually dig in here.

---

### Post by kaede on 2007-10-20
funny thing happen. with live cd. gutsy managed to detect my pcmcia wireless card. but after i installed. i can't use my wireless. now im tryin again with normal ndiswrapper.

---

### Post by BC7333 on 2007-10-20
A remote possibility... [http://ubuntuforums.org/showthread.php?t=582606](http://ubuntuforums.org/showthread.php?t=582606)

after upgrade was getting sporadic inet via wireless and slow pages.. then it eventually stopped working altogether as I fiddled around more..

Now inet fast and back to normal.

---

### Post by radinr on 2007-10-20
Same identical problem.  Changed DNS, which was set to my default internal router (in my case a Netopia 3347W) to my upstream Bellsouth/ATT DNS servers, no reboot, then all seems improved.  No reboot.

Very strange.

Again, this was ok in 7.04, and only went bad after the 7.10 upgrade.

My upgrade was in place.

---

### Post by radinr on 2007-10-20
Well, let me semi-retract.  It WAS improved after the DNS change, now it's slow again, wired and wireless.

---

### Post by gli8600 on 2007-10-20
I can't even connect to my wireless(even it shows it's available), pisses me off big time, linux has put me off one more time.

---

### Post by Lord Darth Vader on 2007-10-20
I had this problem in Ubuntu 6.10. It was gone in Ubuntu 7.04 and now it is back again. Kiinda disappointing.

Here is the partial solution: ( [http://osnovice.blogspot.com/2007/10/slow-internet-connection-in-ubuntu.html](http://osnovice.blogspot.com/2007/10/slow-internet-connection-in-ubuntu.html) )

In firefox, type 
**about:config**

look for this:
**network.dns.disableIPv6**

change the value to "true"

That should fix the internet speed, at least in firefox.

---

### Post by jlombs on 2007-10-20
Thanks for the idea and the help - i don't think it worked for me:

it helped for a few minutes and then it went back to crap speeds again (and firefox took forever to load my homepage)

It seems like the network keeps giving out or something - it has bursts.  

I keep using speedtest.net - one minute I am testing a 1.5mb\s and the next it is 30 kb\s

---

### Post by PeterDB on 2007-10-20
Hi,

Disabling the IPv6 in Firefox helped for me (at least working much faster now for the last 10 minutes).

I noticed something, I also have an Netopia 3347 ADSL modem and maybe something else to add, after I upgraded to 7.10 from 7.04 (using the Update Manager) each time I such down, some new thing called the Network Manager throws some error messages.

/Peter

**** UPDATE *****
I noticed in the release notes for 7.10 , that the Network Settings have been changed to be constantly set on "roaming" instead of DHCP. I tried to leaver this setting, but it made no difference at all...

******** UPDATE **** Found Valid Workaround *****
If you get the DNS address used in your router/modem and add them to the DNS list in the Network settings (but first remove the IP for the router/modem), then add the IP for your router/modem after having added your ISPs DNS I got it working. Not sure, what is causing this though.

---

### Post by ture72 on 2007-10-20
I have the same problems with internet, however some sites, like youtube, works fine but other are impossible to reach. I use the onboard network card, Nvidia chip set, and I have a router. It worked fine in 7.04 so I might go back .. :-(

Update: I removed my router, D-link DI-804, and now I have full connection to the internet. I had exactly the same problem with Ubuntu 6 but it worked fine in 7.04.

---

### Post by dberg on 2007-10-20
disabling ipv6 in firefox worked great for me

---

### Post by PeterDB on 2007-10-20
Hello,

So, I did more troubleshooting again and this definitively is an issue in 7.10.

1. The Network Manager throws errors when shutting when set to the default roaming. I tried now on a few PC's. (error being nm_hal_deinit: libhal shutdown failed, and nm_signal_handler caught signal 15). 7.04 works perfect.

2. The IPv6 trick in Firefox, works great for Firefox, but nothing else. I run a SlimServer on my box for my four SqueezeBox 3's, on 7.04 no issues, on 7.10 issues with gaps or overlay in the music which is streamed. I tried to stream video via VLC from a friends PC over the Internet, same issue, where it worked in 7.04, now it is out of sync and there is lag.

3. Found possible workaround, which is using the System > Administration > Network, to a static IP (remember to add all the details) and then delete the DNS for the router/modem, but add the ISP primary and secondary DNS, before adding the router/modem IP to the DNS list again. ** but this is not a good workaround, over the Internet this works good, but on my LAN I still have issues.**

Since I need a stable solution to offer up my music, I am going back to 7.04 for a couple of months...

/Peter

---

### Post by jlombs on 2007-10-20
Ok, I plugged the laptop into my router and it is working just fine.  The speed tests are pumping at 8556 kb\s, I have tried it several times and it is at least 4 MB\s

My windows shares are working as well.

Yesterday this wasn't the case, but the WIRED connection seems ok.

The wireless still seems to suck, so the focus might shift back on the wireless driver that was installed in the upgrade.

---

### Post by jlombs on 2007-10-20
In some other threads people are saying WICD fixes the issue - has anyone tried that?

---

### Post by braindead_in on 2007-10-20
Faced the same issue. But using Open DNS servers worked for me. The DNS lookup is much faster now. Since I use DHCP I had to edit the dhclient.conf file in /etc/dhcp3. Added these two statements

[INDENT]
prepend domain-name-servers 208.67.220.220
prepend domain-name-servers 208.67.222.222
[/INDENT]

before the request statement.

---

### Post by jlombs on 2007-10-20
> **braindead_in said:**
> Faced the same issue. But using Open DNS servers worked for me. The DNS lookup is much faster now. Since I use DHCP I had to edit the dhclient.conf file in /etc/dhcp3. Added these two statements

[INDENT]
prepend domain-name-servers 208.67.220.220
prepend domain-name-servers 208.67.222.222
[/INDENT]

before the request statement.

When I changed my settings they don't stay - I have it still set to random instread of DHCP.  What do I need to do to make the IP addresses stick?

---

### Post by jlombs on 2007-10-20
> **braindead_in said:**
> Faced the same issue. But using Open DNS servers worked for me. The DNS lookup is much faster now. Since I use DHCP I had to edit the dhclient.conf file in /etc/dhcp3. Added these two statements

[INDENT]
prepend domain-name-servers 208.67.220.220
prepend domain-name-servers 208.67.222.222
[/INDENT]

before the request statement.


Also - this will work for the internet, but my internal network connection is still very slow and bad.

---

### Post by rpasell on 2007-10-20
This is ridiculous.  I've tried all the suggestions from 5 different threads and still no success.  Everything worked fine in Feisty (wireless, wired, Firefox, Swiftweasel).  Did the upgrade in place using synaptic.  Now every time I start Firefox, or Swiftweasel pages take forever to load (2 to 3 minutes)  Once a site loads, I can navigate it OK, but switching to a new site requires another 2-3 minute wait.  I've done the OpenDNs suggestions, I've disabled IPv6 in both browsers, and 3 places in the system.  This is all problems with the wired connection.  I haven't even tried to troubleshoot the wireless connection yet.  How did this make it to final release with a problem this big?  I know I'm not the only one, I've seen dozens of other posts with the same issue.  Went from a flawlessly working system, to an Internet brick.

Acer Aspire 5102.  I use WiCD for managing network connections.

---

### Post by jlombs on 2007-10-20
So WICD doesn't work?

---

### Post by jlombs on 2007-10-20
I was looking around in some other threads and a guy was having issues with Firefox and it hanging so he tried this

> Hi,
I had exactly the same problem...I found this in the Help...

3.2.7.&#8195;IPv6 Not Supported

1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
4. Reboot Ubuntu.

This solved my problems.

Cheers

It didn't work for me, but it might help someone out there

---

### Post by FLCLFan on 2007-10-21
The ubuntu team should fix this problem. :(
I want it fixed.

---

### Post by startgame412 on 2007-10-21
My problem is even more strange.  My WIRED connection is NOT detected BUT my WIRELESS connection is detected and working with the same slowdowns and delays while browsing the web. Go figure that one.

---

### Post by frunns on 2007-10-21
yeah, I'm experiencing the same problems, my wireless is dreadfully slow and usually works in bursts when it do work. BUT, if I connect to my neighbours network, everything works like a charm...

---

### Post by j-b-m on 2007-10-21
I can confirm that disabling IPV6 solved the Gusty slow internet browsing problem for me on 2 different computers.

I did as suggested in a previous post:

 3.2.7. IPv6 Not Supported
 
 1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
 2. To disable it, open a Terminal (Applications > Accessories > Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
 3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
 4. Reboot Ubuntu.

---

### Post by PeterDB on 2007-10-21
I did some more digging, again..

Reading other treads and comparing the information about ppl routers/modems (and checking up on my own), this seems to be an issue with IPv6 compatibility of those routers/modems.

I want to try a slave machine removing the IPv6 support from Ubuntu to see if this makes it work, but for sure, reading the other ppls threads, this seems to resolve it for good.

/Peter

NOTE: Does anyone know what updates were made between IPv6 in Feisty to Gutsy?

---

### Post by SomethinSnappy on 2007-10-21
> **j-b-m said:**
> I can confirm that disabling IPV6 solved the Gusty slow internet browsing problem for me on 2 different computers.

I did as suggested in a previous post:

 3.2.7. IPv6 Not Supported
 
 1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
 2. To disable it, open a Terminal (Applications > Accessories > Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
 3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
 4. Reboot Ubuntu.




[[COLOR="DarkGreen"]Here's[/COLOR]]("http://timelady.com/blog/2007/10/05/a-little-learning/") another blog recommending the same thing. I'm at work, will try it when I get home.

---

### Post by Rehdon on 2007-10-21
I got stuck in the same situation after trying to set a fixed IP instead of the roaming thing: everything ground to a halt, I couldn't even visit the forums to see if there is a workaround.

Ok, then, let's browse the forum using good old Feisty: this is where it becomes even weirder, the network was inaccessible **even under Ubuntu 7.04**, whose network configuration has been working flawlessly during the latest months!!!

I'm sad to say (er ... write) that I had to resort to my Windows XP laptop to browse the forums and see what can be done. I'll try the different solutions hinted here, but I have a weird feeling that the main culprit is the network manager program.

Hope to hear something from the Ubuntu developers as well, this is really a nasty turn of events :(

BTW: I'm an Ubuntu user since Hoary times, this is the first time I feel let down by an otherwise excellent distro.

Rehdon

---

### Post by rpasell on 2007-10-21
I bug reported this here:

[https://bugs.launchpad.net/ubuntu/+bug/155393](https://bugs.launchpad.net/ubuntu/+bug/155393)

---

### Post by mtan on 2007-10-21
I experienced slow internet connection, both browsing pages and updating sources.list.
Here is the solution that worked for me:

1. In Firefox:
   type about:config
   change **network.dns.disableIPv6** to "**true**"

2. edit "/etc/hosts" and comment out the lines containing "**ip6**"

3. edit  "/etc/modprobe.d/aliases"
    and change the following alias:
    #alias net-pf-10 ipv6
    **alias net-pf-10 off**

4. (optional) change DNS to OpenDNS
    [http://blog.mypapit.net/2006/12/how-to-setup-opendns-using-ubuntu.html](http://blog.mypapit.net/2006/12/how-to-setup-opendns-using-ubuntu.html)

I hope the solution above can help  somebody.

Please note that _I am not a Linux expert_ and cannot take any responsibility
about any harm done to your system.

---

### Post by Rehdon on 2007-10-21
> **mtan said:**
> I experienced slow internet connection, both browsing pages and updating sources.list.
Here is the solution that worked for me:

1. In Firefox:
   type about:config
   change **network.dns.disableIPv6** to "**true**"

2. edit "/etc/hosts" and comment out the lines containing "**ip6**"

3. edit  "/etc/modprobe.d/aliases"
    and change the following alias:
    #alias net-pf-10 ipv6
    **alias net-pf-10 off**

4. (optional) change DNS to OpenDNS
    [http://blog.mypapit.net/2006/12/how-to-setup-opendns-using-ubuntu.html](http://blog.mypapit.net/2006/12/how-to-setup-opendns-using-ubuntu.html)



I tried all of these suggestions, but nothing worked :( I also upgraded the router (USR 9106) firmware, to no avail ... still have to connect to the net using Windows.

Any official word from the Ubuntu devs?

Rehdon

---

### Post by rpasell on 2007-10-21
Looks like I jumped the gun here.  The following fixed the problem for my wireless connection only.  I will attempt to modify the ISPs router and see if that works for my wired connection as well.

Modifying the ISP router did not help, and my wired connection is still slow on most websites.

OK, I've "solved" my problem on the wireless connection with a work around.  I added the OpenDNS entries on my wireless router.

Instructions here:

[https://www.opendns.com/start](https://www.opendns.com/start)

This has worked for most sites.  Sites like ESPN.com though are still extremely slow, and take upwards of 7 minutes to render.

To Canonical:  This should not have to be done, and I still consider this a bug.  I hope that you see enough people are having this problem that you continue to work the issue.  The goal I assume is to have this work "out-of-the-box" and this does not.  I will add the solution to my bug report.

Anyone else having this problem, please add your comments to the bug report.

[https://bugs.launchpad.net/ubuntu/+bug/155393](https://bugs.launchpad.net/ubuntu/+bug/155393)

---

### Post by Najmudin on 2007-10-21
> **rpasell said:**
> Looks like I jumped the gun here.  The following fixed the problem for my wireless connection only.  I will attempt to modify the ISPs router and see if that works for my wired connection as well.

Modifying the ISP router did not help, and my wired connection is still slow on most websites.

OK, I've "solved" my problem on the wireless connection with a work around.  I added the OpenDNS entries on my wireless router.

Instructions here:

[https://www.opendns.com/start](https://www.opendns.com/start)

This has worked for most sites.  Sites like ESPN.com though are still extremely slow, and take upwards of 7 minutes to render.

To Canonical:  This should not have to be done, and I still consider this a bug.  I hope that you see enough people are having this problem that you continue to work the issue.  The goal I assume is to have this work "out-of-the-box" and this does not.  I will add the solution to my bug report.

Anyone else having this problem, please add your comments to the bug report.

[https://bugs.launchpad.net/ubuntu/+bug/155393](https://bugs.launchpad.net/ubuntu/+bug/155393)

I agree with all you said , since i have the same problem from two days and nothing has solved it yet.
We have to thank you for reporting the bug and i hope the Canonical people will look into solving the problem.

---

### Post by FLCLFan on 2007-10-21
I have a Actiontec router/modem. Does anyone else with this problem have the same router?

---

### Post by dnordell on 2007-10-21
I'm the one who started this thread, and I'm happy to say that I've found the solution .

<<MY SOLUTION>>

I just upgraded my routers firmware and now both wireless and wired connections is working as it should be :). I also have the IPV6 system-thing disabled.

I hope upgrading the WLAN firmware helps for some of you!

---

### Post by FLCLFan on 2007-10-21
> **dnordell said:**
> I'm the one who started this thread, and I'm happy to say that I've found the solution .

<<MY SOLUTION>>

I just upgraded my routers firmware and now both wireless and wired connections is working as it should be :). I also have the IPV6 system-thing disabled.

I hope upgrading the WLAN firmware helps for some of you!
Thats just for your wireless. Wired still has problems.

---

### Post by repustech on 2007-10-21
I too am having problems with slow network. In my case, it is only the wireless. It is slow for internet and local network transfers. I have tried updating the router firmware but that did not help. For now I'll just wait it out. My connection is usable thankfully, just slow. Lets hope they get this fixed soon. :)

---

### Post by jlombs on 2007-10-21
Updating my router also did not do the trick

Also would the DNS changes fix any of the internal network performance?

---

### Post by lik3n on 2007-10-21
Wired for me is no problem.

However wireless is my biggest issue. It was working perfectly right after I upgraded. I was so happy to see how easy it was while it was wired. Just click the download button and it works. That's never happened for my laptop before.

When I woke up today and tried using my laptop it was taking around 4-5 minutes for each page to load. This is no good for me and while I haven't tried everything yet, it shouldn't be this hard to fix.

---

### Post by startgame412 on 2007-10-21
My wired connection does not even show up. This is such a mess. How do I get my wired connection to show up.

---

### Post by jf1991999 on 2007-10-21
I was not able to connect to any https web addresses and Pidgin could not connect to any servers.  This issue was solved by adding the openDNS servers into my wireless network as suggested.  thanks!

---

### Post by groovomata on 2007-10-21
The same situation for me. I am able to download using Deluge torrent client at 300kbps, but I can barely load a web page. It's like there's a latency occuring, so that the server times out. I have to reload numerous times before I can load the page. Strangely enough the only site that loads immediately is [www.cbc.ca](www.cbc.ca). All other sites including google, youtube, facebook, ubuntu, ubuntuforums... etc take at least 10 reloads before I can get the page. Once I'm on the site though, it seems to work normally. The frustrating thing is that Vista works fine (very frustrating). I tried Opera thinking it was a Firefox problem but I experienced that same issues.

---

### Post by jlombs on 2007-10-21
There is word that there is a firewall program that was added into the mix in 7.10 - anybody know how to shut it off?

---

### Post by jlombs on 2007-10-22
> **rocket777 said:**
> The firewall is a set of rules that let you restrict access to your servers in a variety of ways. If it is not set correctly, it can make many of your services fail.

Look under applications/internet. See if you have firestarter installed. If not, add it via add/remove apps. 

Then, look at this page:

[http://www.fs-security.com/docs/status-page.php](http://www.fs-security.com/docs/status-page.php)

Once it is running, click on the stop firewall button. If this fixes your problems, then you know that the firewall is what is causing your problem.

You can look at the status tab and if there is an events count under serious, you probably have some kind of blocking going on. In my case, I found events for my 2 servers.

I don't know, yet, how to make it stay off, as when I come back from hibernation it's back on.  I'm still studying the online manual (mine doesn't seem to have a working help command).

I'm looking for how to make a rule that allows all connections from my local (192.168.*.*) lan, as that's where I connect to my ubuntu system from my laptop running XP. If you find that the firewall is your problem, I'm sure you can find some help by others more knowledgable than me on how to set it up so it both protects yet doesn't shut down your servers that you want active.

Rocket has some info on disabling the firewall program - I will test this when I get home

---

### Post by staticsage on 2007-10-22
> **kkovach said:**
> Same here.  Upgraded to Gutsy today and my wired network is very slow.  I'm no networking expert, but I ran Wireshark to see if anything jumped out at me.

I'm seeing lots of messages about incorrect checksums in nearly everything I am sending?  Anyone know if that's normal or not?  Doesn't sound normal.  Looking closer it only seems to be happening in HTTP and DNS traffic with my IP as the source.

It's most likely normal. 

[http://www.wireshark.org/faq.html#q11.1](http://www.wireshark.org/faq.html#q11.1)

---

### Post by JillyJK on 2007-10-22
I had the same problem, doing the following 2 things solved it:

> 
Add the following to /etc/sysctl.conf (524288 could be too large, try 262144 or 131072 in place of 524288 if you don't notice an improvement. 524288 worked best for me though):

# Tweaks for faster broadband...
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

Then to have the settings take effect immediately, run:

sudo sysctl -p

Source:
[http://ubuntuforums.org/showthread.php?t=251509](http://ubuntuforums.org/showthread.php?t=251509)


and

> 
3.2.7.&#8195;IPv6 Not Supported

1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
4. Reboot Ubuntu.


---

### Post by jlombs on 2007-10-22
I think this might have helped
I rebooted and got about 600kb\s downlaod on speedtest.org

But then I messed around with some settings again and it wouldn't even work, reset and rebooted....

---

### Post by jlombs on 2007-10-22
Scratch that - I am down to 111 kb\s

GRRRR.... This is very frustrating!

---

### Post by jlombs on 2007-10-23
Do you guys think there will be a viable solution or will it just be a "live with it" situation (in which case I will drop back to 7.04)

---

### Post by repustech on 2007-10-23
Well the first thing is that the Ubuntu team needs to recognize its a bug. The status on the bug ticket will hopefully be updated to confirmed soon.

---

### Post by groovomata on 2007-10-23
My problem was solved by setting the DNS manually and using a DNS service. So certainly for me the problem was a DNS problem. Now I fast internet again and I love my ubuntu box again! 
Thanks!

---

### Post by jlombs on 2007-10-23
There was a guy on the bug report page that said he fixed it by removing IP6 references everywhere. 

Where are all the references
I did it in firefox and I also did it in the config file mentioned a few posts back, but I am better there are probably more places (considering I am still slow).

It is very odd.  Some times I can get 700 kb\s, sometimes I get 70kbs one time I got over 1 MB.  Most of the time it is hovering around 100.  My other PCs are working just fine.  And hardwired it is working well too.

---

### Post by BlenderBoy on 2007-10-23
Using OpenDNS seems to be working for me. I tried removing the ipv6 referenced in the '/etc/modprobe.d' file (like suggested earlier), but after a restart my WiFi or NIC card won't even obtain an IP address from my Apple Extreme router. BTW, I have a Dell Vostro 1400 with a ipw3945 wifi card, running Ubuntu 7.10 64-bit (fresh install).

This slow and FRUSTRATING problem appears to be DNS related. I trust the Ubuntu development team will address this issue ASAP. Thanks for your hard work!

---

### Post by elmerfud on 2007-10-23
My wireless is slow too.  I was thinking there was something wrong all day and then I find this.  This needs to be fixed ASAP !

---

### Post by Scareface on 2007-10-24
After fresh instalation of Gutsy Gibbon I had problems with my internet connection. I had blacklisted ipv6 in the file /etc/modprobe.d/blacklist. I thought, that it will solve the problem. After it I can browse internet pages in firefox, but when I try to get new post by Evolution, or try to login into pidgin, it still write me connection timed out. And worst is, that it do also during refreshing software sources, so I can not install anything. If anybody have ideas, what I shall do, please let me know. Thanks.


I use Acer TM 4050.

---

### Post by ~cyrus~ on 2007-10-24
**I seem to have similar problems.**

1. Disabed ipv6 in Firefox only, through about:config

2. I can login to irc.freenode.com only after I ping it from System Tools. If I don't ping the exact address I am trying to connect to, I get a time out. That is...ping from system tools, and try to connect immediately.

3. The same with system upgrades. If I ping the archive that I am trying to connect to, I get a connection immediately after the ping, and can subsequently keep my system upto date. If I don't ping the archives, I get a timeout.

4. I just cannot establish a connection with Pidgin to my msn account.

5. gFTP also only connects after I ping ftp.mysite.com. If I don't, I get a timeout

6. I seem to be able to ssh into a server alright.

**I have also tried with no effect whatsoever:**

1. Blacklisting ipv6 system wide (not refering to Firefox)

2. Prepend nameservers with the opendns nameservers

As nothing worked, I reverted back to the distribution standards. The only change I have currently is in Firefox where I've disabled ipv6, or I cannot browse.

Regards,

cyrus

---

### Post by bigbang on 2007-10-24
I to have fallen plague to this on my laptop! I tried some of the fixes like the openDNS and IPv6(?); nothing has made a difference (openDNS stopped the connection). Wireless worked OK for me too in 7.04, except I had to configure it manually because it wouldn't show the list of available networks. Now, in 7.10, it shows the list but its constantly slow. I don't get any fluctuation in speed, mine just stays constant at around 120kb/s. 

This is bad for me because this is the laptop my parents use. Is there a way of downgrading back to 7.04 without having to reinstall completely? 

Also, the computer I'm writing this on is running 7.10, no problems, so I don't think this is a rooter problem, more hardware. I have yet to try connecting the laptop via Ethernet.

EDIT: Confirmed, even wired the laptop has the same speed.

---

### Post by orthorim on 2007-10-24
This is definitely a bug in Gutsy. 

My wireless is now at 5 - 10KB/s according to System Monitor.

I run a Mac OS X machine on the same network, and that gets 50KB or more on the same line. Before, in Feisty, Wireless if anything seemed faster on Ubuntu. Now this.

Please fix!!! I have now applied all the suggestions in this thread, turning off IPV6 and so on, nothing helped/

To all of you guys: There are three different kind of issues reported in this thread - those should be separated into different threads. 

1 - Slow wireless and wired networking in Gutsy Gibbon
2 - DNS issues
3 - No connectivity at all

1 and 2 may be related but I can confirm that OpenDNS doesn't fix the problem and in any case it would be a workaround rather than a fix. Please look at what changed from feisty - feisty was totally fine with my WiFi.

---

### Post by bigbang on 2007-10-24
I'm going to downgrade, but how do I go about this without losing any files? (Links?)

---

### Post by BlenderBoy on 2007-10-24
You're right OpenDNS is only a workaround; as this certainly seems like a bug either in the kernel or the TCP/IP stack. But I think it's dependent on hardware too as not everybody has this problem; I mean, you would think something as critical as Internet connectivity is tested thoroughly between betas and before final release.

BTW, for those trying the OpenDNS workaround: make sure you save your new DNS settings. The first time I tried it I didn't save the new settings and after a restart no Internet.

---

### Post by LaserCobra on 2007-10-24
I had a strange one myself where I could not access anything on my network but could get to the internet. All attempts to access LAN ip addresses were getting timeouts. Even my router @ 192.168.0.1 was in accessible. I've had OpenDNS configured on my D-Link router before using Ubuntu so I guess I lucked up there. After 4 days of troubleshooting my LAN access issue resolved itself. Rather disappointing that I could not determine a solution in case it happened again. At this point my only issue is EXTREMELY SLOW LAN access! I finally mounted my NAS via samba but can't access its contents because it takes too long. Anyone this this could be related to this thread or is it the nature of samba? Perhaps I should point out my various Window machines work like a champ.

---

### Post by elmerfud on 2007-10-24
I am very frustrated with wifi support in Ubuntu.   I am running Gutsy and its dropping my connection and losing the ndiswrapper driver in System Settings.  Really stupid !

---

### Post by elmerfud on 2007-10-24
I just found that the /etc/modules file was missing "ndiswrapper".  I have no idea how it ran prior to this.  I added ndiswrapper and it appeared in System Settings and my connection is much fast.  Maybe its my imagination, but I doubt it. 

For the record,
$ uname -a
Linux zd7280 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686 GNU/Linux

I am running Gutsy. 

I installed ndiswrapper-1.48 by downloading the code, the kernel headers and building it manually.  I thought those days were supposed to be over. 

Wireless networking has been hit and miss ever since I installed Gutsy.  It seems to be much, much better now.

---

### Post by orthorim on 2007-10-24
My issues are resolved now. I think it was due to following JillyJK's recommendations of disabling IPv6 everywhere it can be disabled, and adding the "speed up" parameters in hi post. Thanks JillyJK!! 
And then, RESTARTING. Keep in mind that none of that seems to work without restart.
Caveat: I also followed all the other instructions prior to JillyJKs post to disable IPv6 so I can't really say for sure if all of them are needed or just some. Would be nice if somebody in the know could comment on which settings are sufficient for turning off IPv6.

I can rule out that this has anything to do with DNS. My DNS settings are back to automatic, and the only DNS entry I have is my router (got added automatically). I concede that manual DNS settings might get around some problems that IPv6 is causing, but it's certainly not the root of the problem. 

The root of the problem is IPv6 support, which also makes sense as this was disabled in Feisty where everything was OK, and it's consistent with people reporting success by upgrading their router firmware - my router is over 2 years old and I am 100% sure they did not test it against IPv6 at the time it was released. So it seems very likely that IPv6 is causing conflict and Ubuntu would be well advised to turn it off by default and to make a system-wide on/off control somewhere that sets all the bits and pieces in the various config files.

The speed difference is pretty dramatic - before I was getting 10KB/s on average, now I am getting 200KB/s which is the maximum my line can do. 20x speed difference!

> **orthorim said:**
> This is definitely a bug in Gutsy. 

My wireless is now at 5 - 10KB/s according to System Monitor.

I run a Mac OS X machine on the same network, and that gets 50KB or more on the same line. Before, in Feisty, Wireless if anything seemed faster on Ubuntu. Now this.

Please fix!!! I have now applied all the suggestions in this thread, turning off IPV6 and so on, nothing helped/

To all of you guys: There are three different kind of issues reported in this thread - those should be separated into different threads. 

1 - Slow wireless and wired networking in Gutsy Gibbon
2 - DNS issues
3 - No connectivity at all

1 and 2 may be related but I can confirm that OpenDNS doesn't fix the problem and in any case it would be a workaround rather than a fix. Please look at what changed from feisty - feisty was totally fine with my WiFi.

---

### Post by vinater on 2007-10-24
I found that disabling IPv6 and using dynDNS was the best solution for me both of which are already described earlier in the thread. Well at least I was half right. :) I hope everyone else is getting theirs solved.

---

### Post by jamouneau on 2007-10-25
Glad orothim and some others have made progress following the thread suggestions.  Unfortunately, the suggestions aren't a fix for my system. 

Mozilla.org is blazing fast, almost every other site is an instant connect and then "waiting for www.google.com," etc.  A few sites get to "transferring data from ..." but nothing comes of it.

Based on this, and the fact that all the network tools ping, traceroute, lookup, etc. work fine with domain name entries, I doubt that resolving dns is part of the problem.

Any ideas on why Mozilla works when nothing else will?

---

### Post by jlombs on 2007-10-25
Hey - Can you list or link all of the places to disable IP6?

> My issues are resolved now. I think it was due to following JillyJK's recommendations of disabling IPv6 everywhere it can be disabled, and adding the "speed up" parameters in hi post. Thanks JillyJK!! 
And then, RESTARTING. Keep in mind that none of that seems to work without restart.
Caveat: I also followed all the other instructions prior to JillyJKs post to disable IPv6 so I can't really say for sure if all of them are needed or just some. Would be nice if somebody in the know could comment on which settings are sufficient for turning off IPv6.

I can rule out that this has anything to do with DNS. My DNS settings are back to automatic, and the only DNS entry I have is my router (got added automatically). I concede that manual DNS settings might get around some problems that IPv6 is causing, but it's certainly not the root of the problem. 

The root of the problem is IPv6 support, which also makes sense as this was disabled in Feisty where everything was OK, and it's consistent with people reporting success by upgrading their router firmware - my router is over 2 years old and I am 100% sure they did not test it against IPv6 at the time it was released. So it seems very likely that IPv6 is causing conflict and Ubuntu would be well advised to turn it off by default and to make a system-wide on/off control somewhere that sets all the bits and pieces in the various config files.

The speed difference is pretty dramatic - before I was getting 10KB/s on average, now I am getting 200KB/s which is the maximum my line can do. 20x speed difference!


---

### Post by BlenderBoy on 2007-10-25
Changing my DNS settings to OpenDNS got my Internet working (slow, but working) - avg. d/l speed 10-12kb. However, disabling IPv6 restored web access to what it should be. Check out the following links to disable IPv6 correctly (some previous post instructions were incorrect):

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

[http://www.tuxmachines.org/node/7827](http://www.tuxmachines.org/node/7827)

I followed both! Now d/l at 100kb. Good luck; I hope this helps!

---

### Post by Em-Buntu on 2007-10-25
The problems with Gutsy/Firefox seem to be much larger then just  IPV6.
After disabling IPV6, I still have the same issues with Firefox taking usually long time to start, as well as every other site I visit hanging while awaiting data from other sites. After sitting and waiting minutes for the page to load, I finally end up killing Firefox and having to "force quit" the shutdown.

Even pages the work are usually slow (compared to Feisty) and display very slow scrolling.

I think Gutsy has not had enough testing performed before it's release. This is a basic requirement to be able to surf out-of-the box. I cannot see how this bug could possibly escape the attention of the beta testers.
The only site that seems to work reliably with Gutsy/Firefox is the ubuntu forum. CNN, ESPN, and Slashdot.com all hang where they worked flawlessly with Feisty.

Where do I sign up to be a beta tester for the next Ubuntu release (Hardy) so this doesn't happen again?

---

### Post by rpasell on 2007-10-25
This Bug has now been moved from opened to confirmed in my initial bug report.

Please add any helpful information here:

[https://bugs.launchpad.net/bugs/155393](https://bugs.launchpad.net/bugs/155393)

---

### Post by tolremeno on 2007-10-25
> **Em-Buntu said:**
> I think Gutsy has not had enough testing performed before it's release. This is a basic requirement to be able to surf out-of-the box. I cannot see how this bug could possibly escape the attention of the beta testers.
The only site that seems to work reliably with Gutsy/Firefox is the ubuntu forum. CNN, ESPN, and Slashdot.com all hang where they worked flawlessly with Feisty.

Where do I sign up to be a beta tester for the next Ubuntu release (Hardy) so this doesn't happen again?
Anybody can download any build. Personally, I started with beta (bad plan - should've waited a few days) and didn't have this problem until about a week before release. Then it hit hard. Now I get about 90% success on my office network and 10% success at home. They're both linksys routers. And I was using wicd and opendns even before the problems showed up.

---

### Post by Em-Buntu on 2007-10-25
> **tolremeno said:**
> Anybody can download any build. Personally, I started with beta (bad plan - should've waited a few days) and didn't have this problem until about a week before release. Then it hit hard. Now I get about 90% success on my office network and 10% success at home. They're both linksys routers. And I was using wicd and opendns even before the problems showed up.

So, something changed weeks before the release?

I am using a Linksys gigabit router also. One that supports QoS on 1st 4 ports. I am connected to a high speed cable (roadrunner) link that under Feisty supported download speeds up to 2mbps. Under Gutsy I'm lucky to see 200kbps.
Open Office seems also to be effected. It goes into limbo while creating or editing a doc., and also hangs when I go to print. It just sits there and is unresponsive to any keyboard or mouse input.

My system is a quad opteron with 4GB Ram. Even some of the text in this thread is garbled on my screen. This is either related to Gnome or Compiz.
I haven't the time to figure it out, so I've been forced to do what I least wanted, and that's move back to using Windows XP 64 for accomplishing most of my daily workload. For me, at this point, Gutsy is unusable. Over the weekend, I'll likely wipe Gutsy and migrate back to 7.04.

---

### Post by nox.freak on 2007-10-25
I tried all the fixes I could find in the posts here and none of them worked so what I did was used ndiswrapper and that worked.

See this post for ndiswrapper help:
[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

---

### Post by tolremeno on 2007-10-25
But ndiswrapper doesn't work with WPA, does it?

---

### Post by edwardTheGreat on 2007-10-26
> **BlenderBoy said:**
> Changing my DNS settings to OpenDNS got my Internet working (slow, but working) - avg. d/l speed 10-12kb. However, disabling IPv6 restored web access to what it should be. Check out the following links to disable IPv6 correctly (some previous post instructions were incorrect):

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

[http://www.tuxmachines.org/node/7827](http://www.tuxmachines.org/node/7827)

I followed both! Now d/l at 100kb. Good luck; I hope this helps!

This solved any issues that I had perfectly, Thanks BlenderBoy. 
:guitar:
I also disabled IPv6 in Firefox in about:config as well, but I wasn't really experiencing any obvious problems in Firefox.

---

### Post by BaarLaar on 2007-10-26
I am also experiencing this. I am a newbie to linux Ubuntu. I just made the cross over from XP. I hope this will be fixed soon otherwise i will try some other OS or Distro.

The trick for firefox works, which was mentioned earlier works.

---

### Post by tolremeno on 2007-10-26
I have found that updating router firmware really seems to help, although that's obviously more of a workaround than a fix.

---

### Post by fearevilleet on 2007-10-26
Hi,

I have tried all the suggestions, disabling ipv6, and using open dns but I still have a really slow internet connection.  I am using a rt2500 chip set, would my connection would improve by installing the serial moneky drivers or an I likely to screw something up?

---

### Post by napsilan on 2007-10-26
[quote=PeterDB]
******** UPDATE **** Found Valid Workaround *****
If you get the DNS address used in your router/modem and add them to the DNS list in the Network settings (but first remove the IP for the router/modem), then add the IP for your router/modem after having added your ISPs DNS I got it working. Not sure, what is causing this though.
[/quote]

this worked for me

---

### Post by fearevilleet on 2007-10-26
Hi,

I set up open dns in my router. The open dns servers are seen in ubuntu, because that is how they are set on the router, so it filters down. Should I delete them from the network configuration and manually add the opendns servers?

---

### Post by jlombs on 2007-10-27
Ok - so it has been 1 full week and no solution.  

What do you think guys... should I switch back to 7.04? Or should I wait it out.

I find the bootup of 7.10 to be slower as well and general performance has been lagging.

---

### Post by StGermain on 2007-10-27
I updated yesterday, during the update from 7.04 I got speeds of up to 1500K/sec. After the update was done it took a long time to open any webpage, some never opened. I tried all the fixes like disabling ipv6 both for the system and for firefox, but that only slightly helped. Using my provider's DNS directly didn't do much good either.

*** WORKAROUND ***
I'm running on a dell D410 laptop with a broadcom wireless chipset and that seems to be where the problem lies for me. I've plugged in a 3com wireless card that I had lying around (didn't have to install any drivers) then chose to use that card instead of the build-in one by clicking on the network icon and now I'm back to full speed. 

I hope this gets fixed soon because an issue like this might turn first time users away from linux...

---

### Post by kindofabuzz on 2007-10-27
i had the same problem.  switched my wireless to automatic config (dhcp) and started running fine. haven't switched back to static yet to test it though

---

### Post by jlombs on 2007-10-27
Guys - I found a fix
I was re-reading some of the posts and since I didn't have the problem with wired after the first reboot... I focused on wireless.

My laptop had wireless support right out of the box with 7.04, but I made a stupid mistake and ended up installing wrapper and of course it worked great.

I was going to reinstall this morning, but I figured I would give it a try and just run through the process again

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

This worked for me - I am back to 4.5 MB\s, I can watch video off my shares again.  

Give it a try! (I did the wired connection solution)

---

### Post by tolremeno on 2007-10-27
Ok, this has got to be the most obnoxious thing ever. I never thought I'd consider going back to windows, but I am. I can connect almost all the time at the office, but almost none of the time at home. Actually, that's not true. I can connect 100% of the time at home, but I can only get thorugh about 20-30% of the time, even when it thinks it's connected. And lately, I've gotten to the opendns search page but not past. What the hell does that mean?

---

### Post by jlombs on 2007-10-27
> **tolremeno said:**
> Ok, this has got to be the most obnoxious thing ever. I never thought I'd consider going back to windows, but I am. I can connect almost all the time at the office, but almost none of the time at home. Actually, that's not true. I can connect 100% of the time at home, but I can only get thorugh about 20-30% of the time, even when it thinks it's connected. And lately, I've gotten to the opendns search page but not past. What the hell does that mean?

Did you try the NDSWrapper?
What wireless card do you have (I am using a Linksys PCI Wireless G - the standard one)

---

### Post by tolremeno on 2007-10-27
> **jlombs said:**
> Did you try the NDSWrapper?
What wireless card do you have (I am using a Linksys PCI Wireless G - the standard one)
I've tried ndswrapper in 7.04 and 7.10 and have never gotten it to work (most recently using [this method]("http://ubuntuforums.org/showthread.php?t=405990")).
I have a broadcom BCM94311MCG, according to lspci.

The thing is, the damn thing worked right up to about a week before release, and now it acts like it works but it doesn't. And it does work on all routers I've used it on except mine at home.

---

### Post by ivarka on 2007-10-28
Will there (soon) be an official fix for this or should I start going thru all the possible solutions in this thread?


Ivar

---

### Post by gmc on 2007-10-28
I may as well add my 2 cents to this thread too...

I have three system,  a macbook with the official release and a desktop system with RC5 (fully uptodate, both were fresh installs) and an old Toshiba laptop with WindowsXP on it. Both Ubuntu system are showing problems with access to the internet, of course the Windows machine is fine. They are all connected via wired to my Linksys router wit ddwrt firmware (which I upgraded yesterday with no improvement). Local access between the three machines is fine, it's just access to the internet that's the problem.

I've disabled ipv6 in firefox and blacklisted the ipv6 module, played with the mtu value (was 1500), lowered and raise it to no avail.

I'm seriously considering going back to 7.04 or wait another 14 days and give Fedora 8 a shot (though I really hate RPM based distro's)

Very Very Frustrated
Gord

---

### Post by nick_h on 2007-10-28
> **ivarka said:**
> Will there (soon) be an official fix for this or should I start going thru all the possible solutions in this thread?

There is now a fix for [Bug #81057](https://bugs.launchpad.net/ubuntu/+bug/81057/comments/26) - "DNS Resolves everything to 1.0.0.0 intermittently on some ADSL Routers" which may be the cause of the problem for some people.

The fix is to upgrade libc6 from 2.6.1-1ubuntu9 to 2.6.1-1ubuntu10.

To do this enable gutsy-proposed in the software sources and use the Update Manager to download it.  It also selects libc6-i686.  I only downloaded these 2 updates. You can then remove gutsy-proposed after the update.

This works for me without disabling ipv6.

---

### Post by CHFFriday on 2007-10-28
This update has worked for me! I followed the directions and got 70 updates. I installed them all and so far I have no problems.

As an observer of this post I would like to make a comment.

It seamed to me that some panic set in on the part of some of the posters. It took only about a week for our friends at Ubuntu to fix the problem. I have worked in this business for over 40 years and believe me finding a fix that quick is something to be proud of. Just remember sometimes it takes Microsoft months to fix their code. Remember the Love virus? 

Should Ubuntu have waited a few more weeks for the Gusty release? Most likely. But do they want to be like MS and keep postponing a release? Probably not. Lets face it they get a great deal of feed back very quickly. This allows for fast fixes.

Lets face this OS is free! Bill G. would say “you get what you pay for”. I say Ubuntu keep it up! Go for it!

CHFFRiday:)

---

### Post by tolremeno on 2007-10-29
> **tolremeno said:**
> I've tried ndswrapper in 7.04 and 7.10 and have never gotten it to work (most recently using [this method]("http://ubuntuforums.org/showthread.php?t=405990")).
I have a broadcom BCM94311MCG, according to lspci.

The thing is, the damn thing worked right up to about a week before release, and now it acts like it works but it doesn't. And it does work on all routers I've used it on except mine at home.
Update. I tried ndiswrapper again, using [this method]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). It took all of about five minutes to set up, including restarting, and it worked. 

Now my wireless is working 10x better than it ever has on linux. Not only is it not doing the new problems Gutsy caused, but it's also much much stronger and much much faster. I am so so excited, and I'm very glad that Gutsy broke it. I just wish I'd gotten ndiswrapper to work to begin with. 

Oh, and I can get it to work fine with wpa, as well. It's pretty much awesome.

---

### Post by gmc on 2007-10-29
Well I'm pleased to say that upgrading libc6 from proposed seems to be working here too, now I have to decide if I want to keep Fedora Core 7 on my Macbook, since I took it to work and wiped Gutsy from it.

Gord

---

### Post by gmc on 2007-10-29
> **gmc said:**
> Well I'm pleased to say that upgrading libc6 from proposed seems to be working here too, now I have to decide if I want to keep Fedora Core 7 on my Macbook, since I took it to work and wiped Gutsy from it.

Gord


Looks like I may have spoken to soon. I'm still seeing the same problem with the new (proposed) libc6 update.  This is on a fresh install of 7.10 as of about 20 minutes ago.

Can anyone confirm this?

Gord


P.S. Oh and I'm having troubles with the forums too, they report that I'm logged in but when I go to respond to a message, I'm forced to login again...

---

### Post by CHFFriday on 2007-10-29
Gord,
Give me the Specs of the machine you used for the New Install.

CHFFriday

---

### Post by gmc on 2007-10-29
> **CHFFriday said:**
> Gord,
Give me the Specs of the machine you used for the New Install.

CHFFriday

It an Apple Macbook 13" (white), 2G C2D. I'm not sure if these help but I've attached the system specs just in case.

I should note, I have not disabled ipv6 as of yet but will in a few minutes.

Gord

---

### Post by smellydog on 2007-10-29
> **gmc said:**
> Looks like I may have spoken to soon. I'm still seeing the same problem with the new (proposed) libc6 update.  This is on a fresh install of 7.10 as of about 20 minutes ago.

Can anyone confirm this?

Gord


P.S. Oh and I'm having troubles with the forums too, they report that I'm logged in but when I go to respond to a message, I'm forced to login again...

I can confirm this.  I also upgraded to the proposed lib6 and i still have a slow connection with my wireless.  But, my wired connection is doing fine,

---

### Post by gmc on 2007-10-29
Ok, ipv6 is completely disabled and it's just the same.

I'm downloading some packages now via http from from what is reported to be the best site (ping tested) and the through put drops to 0kps and then shoot up to 1200kps (which is impossible for me as my top speed is 120kps download and 12kps upload).

:-(

Gord

Edited: 

Here's what I see if I try to download a file with wget...

```

  150K .......... .......... .......... .......... ..........  7%  197.47 KB/s
  200K .......... .......... .......... .......... ..........  9%   26.01 KB/s
  250K .......... .......... .......... .......... .......... 11%   33.42 KB/s
  300K .......... .......... .......... .......... .......... 13%    1.71 MB/s
  350K .......... .......... .......... .......... .......... 15%    1.12 MB/s
  400K .......... .......... .......... .......... .......... 17%  205.92 KB/s
  450K .......... .......... .......... .......... .......... 19%  113.39 KB/s
  500K .......... .......... .......... .......... .......... 21%  204.02 KB/s
  550K .......... .......... .......... .......... .......... 23%    1.27 MB/s
  600K .......... .......... .......... .......... .......... 25%    1.22 MB/s
  650K .......... .......... .......... .......... .......... 27%  214.42 KB/s
  700K .......... .......... .......... .......... .......... 29%   75.93 KB/s
  750K .......... .......... .......... .......... .......... 31%  111.29 KB/s
  800K .......... .......... .......... .......... .......... 33%   76.43 KB/s
  850K .......... .......... .......... .......... .......... 35%   75.45 KB/s
  900K .......... .......... .......... .......... .......... 37%  207.69 KB/s
  950K .......... .......... .......... .......... .......... 39%    1.64 MB/s
 1000K .......... .......... .......... .......... .......... 41%  212.55 KB/s
 1050K .......... .......... .......... .......... .......... 43%   57.14 KB/s
 1100K .......... .......... .......... .......... .......... 45%   38.84 KB/s
 1150K .......... .......... .......... .......... .......... 47%    1.30 MB/s
 1200K .......... .......... .......... .......... .......... 49%   75.40 KB/s

```

---

### Post by ross350 on 2007-10-29
its not working for me either dell 1501 +gutsy =no internet

---

### Post by CHFFriday on 2007-10-29
Gord,
Are you going thru a Router?

CHFFriday

---

### Post by rkakkar on 2007-10-29
Not working here too! :-(. I have a dlink wireless ralink based lan card. however i'm getting 1/10th of the speed i'm supposed to be getting. :-(. and yes, i'm going through a router

---

### Post by gmc on 2007-10-29
> **CHFFriday said:**
> Gord,
Are you going thru a Router?

CHFFriday


Yes, a  Linksys WRT54G with DD-WRT [DD-WRT v24 Beta (08/15/07) mini]("javascript:openAboutWindow()")

During my attempts to resolve the problem I upgraded the firmware, I was using a release from May.

Gord

---

### Post by CHFFriday on 2007-10-29
Gord,
Click on the Network Icon to open up the network settings. What is in the DNS setting.

CHFFriday

---

### Post by gmc on 2007-10-29
> **CHFFriday said:**
> Gord,
Click on the Network Icon to open up the network settings. What is in the DNS setting.

CHFFriday

nm-applet has control of the network interface and reports:

IP Addr: 192.168.1.3
Broadcast: 192.168.1.255
Subnet: 255.255.255.0
Route: 192.168.1.1
Primary DNS: 208.67.222.222
Second: 208.67.220.220

 and /etc/resolv.conf shows: 

```

# generated by NetworkManager, do not edit!
search mysecretnetwork.org
nameserver 208.67.222.222
nameserver 208.67.220.220

```You probably recognize those DNS servers... OpenDNS :-)

Gord

---

### Post by charles woodward on 2007-10-29
removing the ipv6 seems to have worked for me.

Funny thing is I've been using Gutsy since August/September, doing daily updates - and have only experienced this problem in the last week - at first I thought if was a local `bandwidth` issue (my nephew reported problems getting into sites - and he uses Windows).

In all the months I've been using the `pre-release` version I have never had any problems with networking - so the problem seems to be recent - 

Lets hope my downloads now go a bit faster - that's what alerted me to the problem - a 150mb download set to download over 6 or 7 hours, when normally I can download that in well under an hour.

Hope a proper fix is available soon.

---

### Post by CHFFriday on 2007-10-29
Gord,
Is this a Home setup using Dynamic IP addres or is it a Business type Lan Setup using a static IP address?

---

### Post by gmc on 2007-10-29
I agree. I have a usb drive that has RC5 (fully updated) to use at work and there's no problem there. Unfortunately the Macbook has no way of booting that USB copy of Ubuntu. It's a limitation of the Macbook :-(

Gord

---

### Post by gmc on 2007-10-29
> **CHFFriday said:**
> Gord,
Is this a Home setup using Dynamic IP addres or is it a Business type Lan Setup using a static IP address?


It's home setup with dynamic IP address assignment. I've tried rebooting the router at every test done so far. My ISP is probably wondering why I'm asking for a new IP address every 5 minutes :-)

Gord

---

### Post by CHFFriday on 2007-10-29
OK! Gord,

I will take a stab at this. 

When I am at home and I use the Network Applet and click on the DNS tab the DNS server is my IP address for my Router. This is what it should be as this is how the DHCP is setup. It is the address to access the Router. At home I use Dynamic addressing from my ISP

At work I use Static addressing from my ISP.  The network applets DNS tab shows my LANs Internal DNS servers. This is what is should be showing. This info come from the Routers DHCP settings.

This is what I would try. Make sure the DHCP is setup in the Router. I'm not familiar with this router so I can't help you there.

All this slowness my be caused by what is going on with the Routing Tables. I won't go into this at this time but I would check into DHCP first.

CHFFriday

---

### Post by CHFFriday on 2007-10-29
Gord,
Just one last thing. When you did the update did you get the 70 other updates?

CHFFriday

---

### Post by gmc on 2007-10-29
> **CHFFriday said:**
> Gord,
Just one last thing. When you did the update did you get the 70 other updates?

CHFFriday

The connection to the router is done via DHCP, actually the router is set to match the mac addr with the ip, so the Macbook always gets the same address. I just noticed something interesting... my routing table has changed.

```
~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```Seems to me that the final line use to have a metric of 100 but now it's 0. 

..and yes (finally), it's taken me all morning to get those updates.. figures it included OpenOffice, considering the problem I'm having.


I do appreciate the help though! Thank you. 


Gord

---

### Post by CHFFriday on 2007-10-29
Gord,

I just check my Tables on this machine. Mine are the same as yours except the interface. This is a wireless connection. Yours is Ethernet.

Don't forget there are Tables in the Router. You may ahve to do a Factory reboot. Or they clear out and just start working. Tables are strange that way.

CHFFRiday

---

### Post by gmc on 2007-10-29
Good point, after all I did reflash the firmware. I'll give it a shot and get back to you. Just to save to refreshing for new messages, I need to get some sleep so I'll give it try this evening.

Again, Thank you for taking an interest in the problem.

The good news is that at least the problem is a little better than it was over the weekend and hopefully a solution will be forth comming.. this really has shaken my faith in Ubuntu. Considering I had FC7 on here this morning and was trying to get the hang of RPM package management again after 8 long years.

Gord

---

### Post by ivarka on 2007-10-29
> **nick_h said:**
> There is now a fix for [Bug #81057](https://bugs.launchpad.net/ubuntu/+bug/81057/comments/26) - "DNS Resolves everything to 1.0.0.0 intermittently on some ADSL Routers" which may be the cause of the problem for some people.

The fix is to upgrade libc6 from 2.6.1-1ubuntu9 to 2.6.1-1ubuntu10.

To do this enable gutsy-proposed in the software sources and use the Update Manager to download it.  It also selects libc6-i686.  I only downloaded these 2 updates. You can then remove gutsy-proposed after the update.

This works for me without disabling ipv6.

This did not work for me.

I got a Giga-byte Technology RT2500 802.11g Cardbus/mini-PCI. When I enable networking I get this in the messages log:

```


Oct 29 22:53:17 ika-desktop kernel: [  303.913853] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 29 22:53:19 ika-desktop kernel: [  306.003039] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 29 22:53:20 ika-desktop kernel: [  306.342538] wlan0: duplicate address detected!
Oct 29 22:53:25 ika-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Oct 29 22:53:25 ika-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Oct 29 22:53:25 ika-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Oct 29 22:53:25 ika-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Oct 29 22:53:31 ika-desktop kernel: [  318.030730] ICMPv6 NA: someone advertises our address on wlan0!


```

(I'm sorry but I don't know much about this... but it doesn't sound too good?)

I found something about in this thread but no solution:  [http://ubuntuforums.org/showthread.php?t=522589](http://ubuntuforums.org/showthread.php?t=522589)

Anyone?

Ivar

---

### Post by markhelsby on 2007-10-29
I had the same problem and installed ndiswrapper using these instructions

[http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html](http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html)

Worked a dream, connection speed up to 5500 kps from 150kps

None of the other solutions documented worked at all for me.

Mark

---

### Post by Meerkatjie on 2007-10-30
Hi,

I have managed to get my adsl broadband to work at more or less normal speed and have posted in case it helps someone else. 

I turned off the ipv6 as mentioned before in this thread but it did not help.  I had also updated the DNS servers with the opendns servers (208.67.222.222 and 208.67.220.220) but with my lack of linux experience I could not get those servers to stick. 

Instead I  returned everything to how it was before I started editing.
I updated the DNS servers with the opendns servers (208.67.222.222 and 208.67.220.220) allowing Synaptic to briefly find the repositories.
I then installed 6tunnel (version 0.11rc2-2) and restarted. I installed it as it mentions that it allows ipv4 only capable applications to make use of ipv6 hosts.

Since then I have been able to use firefox and synaptic without any hassles though thunderbird does take a long time to send and receive email

I am a linux/ubuntu newbie so if you need to know more details, ask me and I'll try find out.

cheers

---

### Post by charles woodward on 2007-10-30
the ipv6 and the libc6 upgrade have partly worked for me - the browser seems to work ok as does thunderbird - however I still get massive degradation on dowloads - seems to work ok for about 5-10 mb, then download speed drop to 100bs ( I think thats bits per second - on 150mb file that will take some time)

Hope this gets fixed soon

---

### Post by Jogrrrt on 2007-10-30
After upgrading to 7.10 my wired network was having problems.  My HP Compaq D530 has an onboard network chip which worked perfectly on 7.04 using the same tg3 driver.  Network Manager shows that the roaming connection correctly obtained by DHCP an ip address, subnet mask, gateway, local DNS and Primary ISP DNS addresses.  Still, firefox connections were slow or came in bursts.  My local network was not available.  I used network manager to lookup the ip address of google and ebay which I could not go to using their name.  First of all, lookup found the ip addresses, and secondly Firefox immediately went to the sites using the ip addresses.  Furthermore, after using the ip address and going to the website, Firefox could now resolve the domain name to access the site.  

Yes, I thought ipv6 was an issue (windows problem) and my router is an Actiontec, which had its firmware updated once, but may need it again but this really seems to be DNS related.  Traceroute shows the lookup leaving my computer and going to the ISP provider who passes it up to its highest level DNS server and then boom, the traffic halts and never returns.  My home page seems to hesitate then load in a burst when it does load.  Ad lookups seem to halt traffic as well.  

I first started trying linux with a recommendation to use Gentoo, which had this exact problem.  That's how I found Fiesty, and I love it.  Gutsy would be great if it weren't for these network problems and I found it easier to just reformat and go back to fiesty.  Sigh!:(

---

### Post by charles woodward on 2007-10-30
Jogrrrt has summed up my symptons exactly - everything seems to work in spurts - when initially connected everything works fine, but as time and access increases everything dies.  And the only solution seems to be rebooting (at the moment).  I've tried most of the recommended ideas on this thread, and so far none seems to have worked.  I thought my email was working ok, but then noticed that if I left the program open eventually if would fail to find the server (which, of course, it is already connected to).

---

### Post by two00lbwaster on 2007-10-30
I just wanted to add to this thread as I have the same problem with intermittent internet access with Ubuntu64 7.10.  I was running around for ages thinking that it was something wrong with the native bcm43xx drivers under 64-bit, but having read this thread there seems to be something more fundamental not occurring.

To set out my problems precisely, please not I haven't tried any of the workarounds yet as I have only got as far as page 8, I have intermittent access to both LAN and WAN.  By intermittent I mean that the connection will show 57%, on wireless of course, and starts with a burst slowing to about 8kbs, yes reported as 8xxx bits per second, for a minute or so before stopping completely.  After a period of 5-10 minutes I get a reconnection and then exactly the same problem again.  Something seems to be resetting and then locking again, is the best way that I can describe it.

I can't see how this could be a DNS problem because the problem is as I said both internal and external.  I'll try the workarounds as described in the earlier posts but there seems to be quite a fundamental problem, and as my router should be very happy with IPv6 (being only a few weeks old), then I fail to see the IPv6 solution working.

---

### Post by hades_6_6_6 on 2007-10-30
> **ross350 said:**
> its not working for me either dell 1501 +gutsy =no internet
same hardware, same issue. :(
I've installed ndiswarpper and I can "connect" to my router, but I get no IP :(

---

### Post by gmc on 2007-10-30
No Joy in Macsville..

I took my Macbook to work last night and tried the internet connection there and it's doing it there too. I have access to a WindowsXP Laptop that I hooked up to the network here and it doesn't have any trouble at all (tested with downloading various kernel source tarballs)

9 years with Linux, and I've never seen anything like this problem.

There has to be something we have in common thats at the root of it.

Gord

---

### Post by charles woodward on 2007-10-30
I've found something interesting - I booted into recovery mode, and using a text based browser (lynx) have been able to transfer files back and forth (all over 100mb) with no problems.  I also used this to update software as I couldn't get synaptic to work that long.  I cannot get the `Desktop` network to stay up long enough to get my mail - and it even loses contact with sites I'm already logged onto.

This suggests that the problem has nothing to do with hardware or drivers, but lies somewhere in the interfaces between the Desktop software and the operating system.

I don't think what I've found is a solution - but at least it allows me to function in the short term - and may be a pointer to the real problem.  The downside is that it was even more difficult to get the networks working again when I went back into Desktop mode.

---

### Post by repustech on 2007-10-30
I tried the fix for Bug #81057, it didn't seem to help my problem. I'll wait it out until there is a real fix. I don't want to put a bandaid on this problem.

---

### Post by CHFFriday on 2007-10-30
Gord,
This is really for everyone who has posted here.

As I have read the posts here  it seams to me that there are two main problems. Please correct if I’m wrong on this.

1.Some wireless Cards/Chips do not activate properly or not activate at all with Gusty.
2.The Cards/Chips that do activate work but with reduced functionality. IE slow speed, burst of speed, disconnects etc. 

I noticed the Card/Chips that don’t activate most are covered in other posts on this Form. For those having this problem, getting them to work needs to be done first. It may not solve the problem listed in 2. But it’s a start. 

Now for Cards/Chips that activate but have functionality problems, I still think it has something on how the Routing is taken place. I have seen this problem before with Windows and have sometimes fixed it by uninstalling then reinstalling the TCP/IP stack. I don’t know how this can be done in Ubuntu. If you know how maybe it is worth a try. 

I sure would like to know what update file  is used for. That info may lead to a work around. 

Also notice the poster that said he started in Safe Mode (for lack of a better term). Some drivers not loaded! Maybe? You may know more about this then I.

CHFFriday

---

### Post by vishi on 2007-10-30
Hi All,

I have the same problem with Ubuntu Gutsy. I am able to open most of the websites at full speed and I am also able to download stuff using synaptics @ full speed. However, the main site I want open all the time : google.com is simply refusing to open. 

Also, trying to open ubuntuforums.org takes "ages" to open. I get a redirect message from Firefox and when i click on the new link, it reads the data, loads images, and starts looking for google-analytics.com and  Bang!!! Nothing happens for 10 mins and after a lot of time the page finally opens. I tried pinging google.com and [www.google.com](www.google.com) => No use. 100% loss.

I have tried the following suggestions provided in the thread here:[LIST]
[*]Make changes to firefox by setting the IPv6 bool value to true
[*]Modified my /etc/resolv.conf and added the DNS server IP of my ISP (BSNL)
[*]Modified the aliases file and commented the IPv6 entry and added one below it and set it to 'off'
[*]Commented all IPv6 lines in /etc/hosts
[*]Did the steps listed in the topic : [http://ubuntuforums.org/showthread.php?t=251509](http://ubuntuforums.org/showthread.php?t=251509)
[*]Installed Wireshark and did some tracing
[/LIST]

I use a static IP and can ping my router on the gateway 192.168.1.1
My ISP DNS servers are 61.1.96.69 & 61.1.96.71
The IP of my PC : 192.168.1.100

Using a wired connection via ETH0; Router : Huawei SmartAX MT800

I have absolutely no problem while working on windows. 


Any suggestions?:confused::(

Thanks,
Vishi

---

### Post by nick_h on 2007-10-30
> **vishi said:**
> 
I have tried the following suggestions provided in the thread here:[LIST]
[*]Make changes to firefox by setting the IPv6 bool value to true
[*]Modified my /etc/resolv.conf and added the DNS server IP of my ISP (BSNL)
[*]Modified the aliases file and commented the IPv6 entry and added one below it and set it to 'off'
[*]Commented all IPv6 lines in /etc/hosts
[*]Did the steps listed in the topic : [http://ubuntuforums.org/showthread.php?t=251509](http://ubuntuforums.org/showthread.php?t=251509)
[*]Installed Wireshark and did some tracing
[/LIST]


You could update your libc6 from gutsy-proposed.  You only need to update 2 files not all 70.

---

### Post by charles woodward on 2007-10-30
To answer a question posed above, when you boot into `recovery mode` it is not quite like windows safe mode, as everything has to be carried out on the command line.

Most of the basic tasks can be carried out using the command line, for example in `recovery mode` the basic networking is set up so that you can download files, do updates, etc.  But as I say you can do almost everything from this command line that you can do from the Desktop, except you do not get the graphics.  I worked for over twenty years with Unix/Aix systems, so the command line is a little bit like second nature to me - generally if you are not comfortable with using the command line it is safer to leave alone.

When you use explorer (or even print) the graphical front end (the Desktop) passes the instructions through to these `command line` tools - so if they work at the command line the theory is that the problem must be hidden somewhere within the Desktop Architecture.

As I have tried both fixed network (eg /etc/network/interfaces) and the network manager, and both have the same sorry results, I think they are not the problem.  

The whole thing does point to some sort of software problem, and as it seems that the browsers/mail readers slowly lose contact with the web that the problem may be something to do with IP stacks or routing tables - but frankly that is outside my sphere so I am only guessing.  And obviously I can only judge based on my own symptons.  

As mentioned previously this is a reported bug, which has been confirmed so I would think they are working on it as best as they can.  But from my experience (I used to test software) this is the sort of bug which can take ages to track down, as it often is the result of two or more problems coming together in particular circumstances.  And that's where the cure becomes difficult.  

I do hope they can track this down quickly - but I've only had this problem since Friday (I've just checked) and can (just about) live with it for a little longer.  Those without command line knowledge may feel the thing is more urgent.

---

### Post by charles woodward on 2007-10-30
By the way I should point out that for internet updates, etc., the command line only seems to work in recovery mode - if you boot in the normal way and then go to terminal it doesn't seem to work - probably because ubuntu desktop and ubuntu minimal are loaded.  It certainly didn't work on my machine.

---

### Post by CHFFriday on 2007-10-30
Gord,
There is something common. The Kernel

Do me a favor check the LIb folder on the MAC for two files LIBNSS_DNS.SO xxxx and give the the version number.

CHFFriday

---

### Post by ivarka on 2007-10-30
> **ivarka said:**
> This did not work for me.

.....

Ivar

Now I'm a happy camper :)  Seems like there are some driverproblem with my card: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660)

Build my own driver and the speed is back at  4 406 kbit/s

Ivar

---

### Post by CHFFriday on 2007-10-30
Ivar,
Could you post how you Built your own driver?

CHFFriday

---

### Post by repustech on 2007-10-30
I couldn't wait any longer so I installed ndiswrapper instead of using the built-in fwcutter (restricted drivers manager). This solved my problem, so I assume it's a software problem with fwcutter. Just wanted to let everyone know. I have always had better luck with ndiswrapper anyways... it activates my wireless light! :)

---

### Post by vishi on 2007-10-31
> **nick_h said:**
> You could update your libc6 from gutsy-proposed.  You only need to update 2 files not all 70.

Done that too! The version I had was libc6-<something>-9 and I upgraded it to libc6-<something>-10 using the "proposed" updates. No use :(

---

### Post by gmc on 2007-10-31
> **CHFFriday said:**
> Gord,
There is something common. The Kernel

Do me a favor check the LIb folder on the MAC for two files LIBNSS_DNS.SO xxxx and give the the version number.

CHFFriday

Sorry I missed this message before I re-installed Gutsy RC5 which was the last working version I had. I left the system downloading the updates (apt-get -dy dist-upgrade), so hopefully I'll have everything ready to go in the morning when I get home from work.

I'll check the version number for LIBNSS before and after the updates are installed. Then I'll enable the proposed repository and get the version number again.

Gord

---

### Post by CHFFriday on 2007-10-31
Gord,
I,m at one of our remote office and just tested the speed. I have never connected to this router before today. Speed is excellent!

I hope the development team is reading this post! They have a BIG problem! I'm not discourage as all my machine are working but this sure is a black mark on Ubuntu.  As you can see this problem is all over the place. There seam to be many factors causing the problem.

I would like to try to get the MAC going so keep me informed.

CHFFriday

---

### Post by gmc on 2007-10-31
> **CHFFriday said:**
> Gord,
I,m at one of our remote office and just tested the speed. I have never connected to this router before today. Speed is excellent!

I hope the development team is reading this post! They have a BIG problem! I'm not discourage as all my machine are working but this sure is a black mark on Ubuntu.  As you can see this problem is all over the place. There seam to be many factors causing the problem.

I would like to try to get the MAC going so keep me informed.

CHFFriday
Hi CHFFriday

> 
Do me a favor check the LIb folder on the MAC for two files LIBNSS_DNS.SO xxxx and give the the version number.A couple of things, as I said earlier, I left the system with RC5 installed and only downloading the update to bring it up to GOLD, unfortunately I must have been tired and missed the "d"ownload only option and when I got home this morning, the upgrade had already started. There for I missed making a backup copy of the libnss_dns files, but I belive they would have been 2.6.1-1ubuntu8 or 2.6.1-1ubuntu9.

Now I'm not sure what a "MAC" for a library file is, so with that in mind, I made a backup copy of all the libnss_dns files I could find:

~# find / | grep libnss_dns
/lib/tls/i686/cmov/libnss_dns.so.2    
/lib/tls/i686/cmov/libnss_dns-2.6.1.so
/lib/libnss_dns.so.2
/lib/libnss_dns-2.6.1.so

...and then when I enabled the "proposed" repository. I only updated the libc6 and made another backup copy. This should allow me to switch back and forth without having to re-install the system. :-)

Now, pre-proposed update, libc6-i686 2.6.1-1ubuntu9 was installed and post-proposed update, installed libc6-i686 2.6.1-1ubuntu10. 

The problem persists with both versions.

Gord

---

### Post by ivarka on 2007-10-31
> **CHFFriday said:**
> Ivar,
Could you post how you Built your own driver?

CHFFriday

I did what was written on that page:

I first downloaded [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)

Then unpacked it and moved to module directory

```

tar -xvzf Desktop/rt2500-cvs-daily.tar.gz
cd rt2500-cvs-2007103017/Module/

```

Then build it:
```

make
sudo make install

```

Checked that I got a new line in /etc/modprobe.conf (I use  "pico" as editor)
```

sudo pico /etc/modprobe.conf

```

And added the following lines to /etc/modprobe.d/blacklist
```

blacklist rt2400pci
blacklist rt2x00pci
blacklist rt2x00lib

```

I played with ndiswrapper before I did this but don't think that made any difference ("ndiswrapper -l" gives nothing)

Ivar

---

### Post by two00lbwaster on 2007-11-01
Right having had a look around the issues with wireless are like this.  As described in my previous post on page 14 with the bwcutter and bcm43xx combination.

With ndiswrapper I have a perfect connection, at 1Mbs.  It's much better than nothing, but it's pretty poor when my internet connection is twice that speed. (I'm off to have a look around for a solution to the slow ndiswrapper problem).

It seems that the problem is possibly either with the bcm43xx/bwcutter implementation, or if the ndiswrapper problem is related then something is quite wrong with Ubuntu 7.10 :(

This is still on Ubuntu64 mind.

---

### Post by jamouneau on 2007-11-01
**A SOLUTION**, at least for me!

This may do nothing for wireless problems but my slow/non-browse able wired connection was fixed by the following steps:

sudo gedit /etc/sysctl.conf

change the following parameters to 0:

net.ipv4.tcp_sack = 0
net.ipv4.tcp_window_scaling = 0

save file, reboot and it works!  First time I've been able to browse from Ubuntu!

This solution was proposed by   Mpokrywka on the "Slow internet - Some page not loading at all" thread [http://ubuntuforums.org/showthread.php?t=598567](http://ubuntuforums.org/showthread.php?t=598567) using the "old" reference "net.ipv4.tcp_default_win_scale = 0"

---

### Post by gmc on 2007-11-02
> **jamouneau said:**
> **A SOLUTION**, at least for me!

This may do nothing for wireless problems but my slow/non-browse able wired connection was fixed by the following steps:

sudo gedit /etc/sysctl.conf

change the following parameters to 0:

net.ipv4.tcp_sack = 0
net.ipv4.tcp_window_scaling = 0

save file, reboot and it works!  First time I've been able to browse from Ubuntu!

This solution was proposed by   Mpokrywka on the "Slow internet - Some page not loading at all" thread [http://ubuntuforums.org/showthread.php?t=598567](http://ubuntuforums.org/showthread.php?t=598567) using the "old" reference "net.ipv4.tcp_default_win_scale = 0"

Tried and failed. This fix hasn't made any difference for me - I also just spent 3 hours downloading a bunch more packages from the proposed reop's, one of which was kernel related - Still no joy though.

Gord

---

### Post by charles woodward on 2007-11-02
I don't think this problem is related to fwcutter and ndiswrapper - I also have a bcm43xx card but use a third party driver - I do not even have ndiswrapper on my machine.

One thing I've noticed is that if you go to the command prompt and do iwlist scan it will give you a list of all the networks in your area (providing they broadcast the SSID) - this suggests to me that there is nothing wrong with the drivers, etc.  If you then try and launch your browser it will not connect to the internet.  

You can connect to the internet if booted into recovery mode, although you will only have text based browsers - and they are a pain.

As a bug has been reported on this, I will check up and see if there is any progress.  Just looking at the numerous threads on the networks forum it seems that there are very few people who are not experiencing problems.

(i've spent almost three days offline and have just put 6.06 on to a spare drive so I can get back online)

---

### Post by charles woodward on 2007-11-02
Now that I've been able to use my other connection to get to the internet, I have found something that seems to solve my problem.  

It is mentioned in one of the threads - basically you have to edit a file :

the file is /etc/dhcp3/dhclient.conf

within this file you will see a commented out line (~prepend  )

add the following line :

prepend domain-name-servers 208.67.222.222, 208.67.220.220;



This certaily seems to have worked for me - I've now been up for nrealy an hour, and am experiencing no problems.    For the last week I have barely been able to stay up for more than a few minutes in Gutsy.

---

### Post by gmc on 2007-11-02
> **charles woodward said:**
> Now that I've been able to use my other connection to get to the internet, I have found something that seems to solve my problem.  

It is mentioned in one of the threads - basically you have to edit a file :

the file is /etc/dhcp3/dhclient.conf

within this file you will see a commented out line (~prepend  )

add the following line :

prepend domain-name-servers 208.67.222.222, 208.67.220.220;



This certaily seems to have worked for me - I've now been up for nrealy an hour, and am experiencing no problems.    For the last week I have barely been able to stay up for more than a few minutes in Gutsy.


While I was verifying that I do indeed have the above prepend line in my /etc/dhcp3/dhclient.conf, I noticed that **send host-name "<hostname>" **was also enabled. I don't recall changing that myself (though it is possible). 

Anyone suffering slowdown problems may want to check that its not enabled.

Disabling send-host, hasn't solved the problem but it certainly didn't hurt either.

Gord

---

### Post by charles woodward on 2007-11-02
I have deliberately left my connection on - and it still seems to be working.

I think that this is the solution to the problem - it certainly fits the bill - as the problem seems to have revolved around domain names - anyway its worked for me, so I suggest everyone else try it as well.  You never know - although it's not unknown for there to be mutliple bugs all showing the same symptons.

---

### Post by clandoug on 2007-11-03
More info in case it helps.  I had the slowness until I did the IPv6 stuff.  Now it's fast once it finds a domain, but it's slow to find new pages.  I've done nearly all of the updates.  Take craigslist for example - takes half a minute to find it.  But then I can click any link and it's instant (it is just text, but you get what I mean).  Yes I did the prepend trick - no help.

-Dave

---

### Post by clandoug on 2007-11-03
Okay, I manually entered the OpenDNS entries in the Network DNS window and voila I'm fixed.  But the entries don't stick - reboot and they're gone.  What file do I need to edit to put these in permanently?  I already have the prepend statement.  Thanks in advance!

-Dave

---

### Post by clandoug on 2007-11-03
Yay.  I am fixed.  I had missed the semicolon on the end of the prepend statement.  Works now.  So too issues for me: 1. IPv6, 2. DNS.  I'm only doing wired web.

-Dave

:)

---

### Post by vallaird on 2007-11-03
Hi, really happy to tumble upon this thread as I did a fresh install of Gutsy and wired network speed was sh*t and I could not access Hotmail, I've done the following  and everything is back to normal now. My hardware is an onboard network chip on an Asus P4S800  motherboard with the Lynksis WRT54GL router running DD-WRT version 23 sp2.

"
the file is /etc/dhcp3/dhclient.conf

within this file you will see a commented out line (~prepend )

add the following line :

prepend domain-name-servers 208.67.222.222, 208.67.220.220;
"

Thanks for the person who found this fix.

---

### Post by ookami on 2007-11-05
Right, my computer is wired in using the onboard ethernet port on my nForce2 motherboard  to a Linksys WRT54GL router running DD-WRT v23 SP2.
What solved my issues with pages not responding, slow speeds and all manner of problems that seemed related to problems with DNS-lookups was _not_ to disable IPv6 in Ubuntu but rather to _enable_ support for it on the router.
I did indeed try the trick of disabling IPv6 but it made no difference, so if there are others out there who suffer similar problems I hope this might work for you too.

(I don't know if it matters much really, but I did enter my ISP's DNS-servers manually into /etc/dhcp3/dhclient.conf as well. It didn't resolve my problem either but I've kept it set up that way even after enabling IPv6 in DD-WRT)

---

### Post by gmc on 2007-11-06
> **ookami said:**
> Right, my computer is wired in using the onboard ethernet port on my nForce2 motherboard  to a Linksys WRT54GL router running DD-WRT v23 SP2.
What solved my issues with pages not responding, slow speeds and all manner of problems that seemed related to problems with DNS-lookups was _not_ to disable IPv6 in Ubuntu but rather to _enable_ support for it on the router.
I did indeed try the trick of disabling IPv6 but it made no difference, so if there are others out there who suffer similar problems I hope this might work for you too.



Now I'm itching to get home from work and try your solution. You're setup almost exactly matches my own, even the firmware on the router. So now I'm hopeful that I can finally put this problem to bed and really get into enjoying Gutsy.

Thanks for the tip!
Gord

---

### Post by drizkill on 2007-11-06
I'm hoping a fix comes out for this soon. I am a recent convert to Linux and I have enjoyed it immensely, however; the wireless situation is becoming annoying. I have tried all of the suggestions from this thread and have tried disabling ipv6, re-enabling it and enabling ipv6 on my linksys router (wrt54gl-ddwrtsp2), and I still have the same issue. For me, my connection is fine on a fresh boot, however; if I start a torrent download my DL speed goes from 5mbps to 940kbps in a very short period of time. I cannot download any torrent over ~100KB. As soon as I reboot I can hit a speedtest of over 12000kbps (cox + speedboost - speedtest.net) once I start a torrent, however; it dumps to ~ 940kbps and then affects my entire networks throughput... Even though I only have one Linux box (at this time) it downs my entire network's speed. I desperately need help from any of you out there as I refuse to move back to windows on this machine.

---

### Post by StefAndrew on 2007-11-06
> **j-b-m said:**
> I can confirm that disabling IPV6 solved the Gusty slow internet browsing problem for me on 2 different computers.

I did as suggested in a previous post:

 3.2.7. IPv6 Not Supported
 
 1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
 2. To disable it, open a Terminal (Applications > Accessories > Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
 3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
 4. Reboot Ubuntu.

Worked like a charm.  No more issues with connecting to my wireless router.

Thank you.

---

### Post by greenpea on 2007-11-06
i tried disable the Ipv6, changed the setting for DHCLient.conf and setting for firefox in about:config, none of these seems to be working.

---

### Post by ndaru on 2007-11-07
This is related with bug [#81507]("https://bugs.launchpad.net/ubuntu/+bug/81057")

Just like j-b-m said, all you need to do is disabled IPv6 inside **/etc/modprobe.d/aliases**.

---

### Post by fooman on 2007-11-11
> **charles woodward said:**
> Now that I've been able to use my other connection to get to the internet, I have found something that seems to solve my problem.  

It is mentioned in one of the threads - basically you have to edit a file :

the file is /etc/dhcp3/dhclient.conf

within this file you will see a commented out line (~prepend  )

add the following line :

prepend domain-name-servers 208.67.222.222, 208.67.220.220;



This certaily seems to have worked for me - I've now been up for nrealy an hour, and am experiencing no problems.    For the last week I have barely been able to stay up for more than a few minutes in Gutsy.

omg i have been at it all day trying to fix the slow wireless problem on my gateway mx6421 laptop with a fresh install of gutsy.

tried the ipv6 thing as well as many others with no luck....FINALLY the above fix worked!  i am back at full speed....thank you.  :)

:guitar:

---

### Post by sundar_m77 on 2007-11-12
thanks to everyone. My wireless started working fast after disabling IPV6 and changing the dhclient.conf.

---

### Post by smellydog on 2007-11-14
> **greenpea said:**
> i tried disable the Ipv6, changed the setting for DHCLient.conf and setting for firefox in about:config, none of these seems to be working.

I am glad that some of you are having great success, but i am in the same sinking boat as greenpea.  I did the same as above with no change.  Everything worked great in Edgy and Feisty!  What the heck is the big difference now!! :confused:

---

### Post by smellydog on 2007-11-14
I am using a Linksys wireless B router with 4 port switch, and an integrated wireless B/G in my laptop.  any ideas?  When i plug it in directly with a wire, everything is fast and great.  I also tried to upgrade the firmware on the router itself with no results, but i also think that it didn't take the upgrade for some reason.  Must look more into that.  Hmmm...

---

### Post by sproutz on 2007-11-15
Step 1
> **j-b-m said:**
> 
 1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
 2. To disable it, open a Terminal (Applications > Accessories > Terminal) and type the command: sudo gedit /etc/modprobe.d/aliases.
 3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
 4. Reboot Ubuntu.
Step 2
> **charles woodward said:**
> 
the file is /etc/dhcp3/dhclient.conf

within this file you will see a commented out line (~prepend  )

add the following line :

prepend domain-name-servers 208.67.222.222, 208.67.220.220;


These two steps worked for me. Step 1 fixed 90% of the problem but Gutsy was still taking time to resolve DNS. Step 2 fixed that...

---

### Post by Wanabean on 2007-11-17
Did a fresh install to Fiesty after difficult wifi experiences in Dapper.

Upgraded to Gutsy from Fiesty and lost wifi, which had worked out-of-the box with Fiesty. 

Tried lots of things to get wifi back (Addon GWU190) including ipv6 settings but eventually gave up and went back to Fiesty.

I would like to upgrade to Gutsy again but only after the bugs have been fixed.   Do the mods suggested in the forums get incorporated via routine software upgrades or are separate fixes necessary?  How does one know when when bugs have been fixed?

I am generally delighted with Ubuntu but surprised that problems solved seem to reoccur in later releases.

---

### Post by vishi on 2007-11-19
Nothing works! 

I have tried ALL the solutions in this thread (almost 18 pages of reading / tweaking / testing /rebooting)... but nothing works. I have Gutsy Gibbon (clean install) on my desktop.

I was able to get the Google Homepage on firefox.. but when i try accessing any other sister sites like youtube / gmail / maps, I see nothing...even searching Google wont show results.  Browser shows a plain white page and status bar reads "connecting to <whatever>.google.com"  and nothing happens. 

I tried pinging google on terminal and the address is resolved to an IP and thats it. nothing happens beyond that. I need to get back to windows to post on this forum as the forums page gets stuck on "connecting to google-analytics.com" after loading only the banner. Same case with Firefox  / Opera / another browser i tried.. cant remember its name :P

Let me know what i need to do.. I am growing tired with Gutsy :(

---

### Post by vishi on 2007-11-19
> **vishi said:**
> Nothing works! 

I have tried ALL the solutions in this thread (almost 18 pages of reading / tweaking / testing /rebooting)... but nothing works. I have Gutsy Gibbon (clean install) on my desktop.

I was able to get the Google Homepage on firefox.. but when i try accessing any other sister sites like youtube / gmail / maps, I see nothing...even searching Google wont show results.  Browser shows a plain white page and status bar reads "connecting to <whatever>.google.com"  and nothing happens. 

I tried pinging google on terminal and the address is resolved to an IP and thats it. nothing happens beyond that. I need to get back to windows to post on this forum as the forums page gets stuck on "connecting to google-analytics.com" after loading only the banner. Same case with Firefox  / Opera / another browser i tried.. cant remember its name :P

Let me know what i need to do.. I am growing tired with Gutsy :(

I am however able to download packages, etc using sudo apt get / synaptics @ full 256kbps (32kBps). I have trouble accessing ONLY google sites / sites that refer to google (ads / analytics / etc).

---

### Post by kevdog on 2007-11-19
Disable IPv6 -- that might help you -- Just read the relevant section of the thread below.

Here is the link:
[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

---

### Post by Wanabean on 2007-11-19
A newbie's slightly off-topic  question to Kevdog.

I have great respect for all the helpful responses that have generated your huge bean count but wonder why you are still with Fiesty.

Could it be that upgrading is best done after a release has had a few months to settle down?

I have bounced back to Fiesty with fingers burned in Gutsy but wonder when it will be safe to give it another try.

Are you so busy helping others to upgrade your own system?

---

### Post by dexter on 2007-11-19
I'm having the same problem with 7.10. I've tried all the hints in this thread to disable ipv6, however, none were successful.

I did some tests from which the results may be interesting:

Hardware:
- Ubuntu 7.10 machine
- MacBook
- Adsl Router / wireless switch
- switch

The Router is connected to the switch. Both the Ubuntu machine as the MacBook are connected to the switch using wires. Additionally, the MacBook can be connected to the router directly using the wireless interface. Both machines are set up to run apache, speeds are measured transferring files from one machine to the other using the http protocol.

**Situation 1**: MacBook connected using wire to switch
[LIST]
[*]Download file from Ubuntu to MacBook: normal speeds
[*]Download file from MacBook to Ubuntu: normal speeds
[/LIST]

**Situation 2**: MacBook connected to router using wireless interface
[LIST]
[*]Download file from Ubuntu to MacBook: normal speeds
[*]Download file from MacBook to Ubuntu: slow as hell
[/LIST]

**Conclusion**
[LIST]
[*]Files transferred from Ubuntu to MacBook always goes fast
[*]Files transferred from MacBook to Ubuntu only goes fast if the MacBook is connected directly to the switch. Connecting the computers like this ensures that the router is not being used in the transfer. Only when the MacBook is connected wirelessly through the wireless interface from the router, transfer is slow.
[/LIST]

-> From this we can conclude that the hardware Ubuntu is running is perfectly capable of achieving high download speeds. Only when the connection has to pass through the router, the transfer is dreadfully slow.

---

### Post by MrSootentai on 2007-11-19
Ok so if ANYONE found a foolproof way to get this working help me out.
I don't know what happened, my internet was fine and I did and update and all of a sudden I can't connect to most internet sites.
Just like one said above I can't connect to google, gmail, or any google analytics.
Any surefire way?
After 18 pages and using all tweaks I want to see something that actually helps me out.

---

### Post by MrSootentai on 2007-11-19
MAJOR PS:
Just **[COLOR="Red"]uninstalled moblock-nfq [/COLOR]**(forgot I had it installed) and my internet is back to normal.
Not sure what it did.
please everyone try it.

---

### Post by vishi on 2007-11-21
> **MrSootentai said:**
> MAJOR PS:
Just **[COLOR="Red"]uninstalled moblock-nfq [/COLOR]**(forgot I had it installed) and my internet is back to normal.
Not sure what it did.
please everyone try it.

Oh dear oh dear! God bless MrSootentai!!! It was indeed moblobk-nfq that was cauing the "block" all this time! Oh bl***y oh! What would I have done I if hadn't seen this post.. perhaps format my ubuntu partition! God bless ye all.. God bless ubuntu! Am back on full speed now! 3 Cheers for this community!

Everyone, make sure that you dont have any protocol blocking software like moblock installed!

---

### Post by Beebock on 2007-11-21
hi All,

I have not read all the posts, but found something that helped me.

Synaptic manager, hunt down LIBc6 and select to re-install it.

Did that 20 minutes ago, nice and solide connection now. was bumming out every 1-2 minutes under strain.

Richard

---

### Post by smellydog on 2007-11-22
> **vishi said:**
> Oh dear oh dear! God bless MrSootentai!!! It was indeed moblobk-nfq that was cauing the "block" all this time! Oh bl***y oh! What would I have done I if hadn't seen this post.. perhaps format my ubuntu partition! God bless ye all.. God bless ubuntu! Am back on full speed now! 3 Cheers for this community!

Everyone, make sure that you dont have any protocol blocking software like moblock installed!

Protocol blocking software?  That comes installed on a fresh install of Ubuntu?

---

### Post by Beebock on 2007-11-24
> **Beebock said:**
> hi All,

I have not read all the posts, but found something that helped me.

Synaptic manager, hunt down LIBc6 and select to re-install it.

Did that 20 minutes ago, nice and solide connection now. was bumming out every 1-2 minutes under strain.

Richard

Well scratch this!! that did not work. I've now gone back to Feisty!:mad:

---

### Post by nick_h on 2007-11-25
> **Beebock said:**
> I have not read all the posts, but found something that helped me.

Synaptic manager, hunt down LIBc6 and select to re-install it.


This may be related to my earlier post - [post #109](http://ubuntuforums.org/showpost.php?p=3654324&postcount=109).

---

### Post by Arik Amir on 2007-11-25
Hi All,

I made the changes as mentioned in this post:
1. I've added ipv6 to the blacklist 
2 disabled the ipv6 in Firefox
and still there are some web sites that do not load. I removed windows from this computer and installed ubuntu because I thought Linux desktop is up to par, I guess I was wrong, this computer is being used to access the internet mostly no special program needed just fast internet access and that doesn't work straight from the box, I'm disappointed.
I've installed my first Linux system back in 1993, it was a slackware distribution and it took three days to install because you had to compile a lot of the functionality by yourself, well Linux came a long long way from that but still lacks basic out of the box functionality to become a desktop.

I can tweek and recompile my system to make it work but that is not the point of out of the box.

the website that gives me the most problems is runescape.com, which my kids like to play at, any ideas to make me stick to linux desktop I would realy like to give it a shot

---

### Post by Beebock on 2007-11-25
> **nick_h said:**
> This may be related to my earlier post - [post #109](http://ubuntuforums.org/showpost.php?p=3654324&postcount=109).

Yeah, that is where I got the idea from :)

Has anyone reported this in 32bit? or Kbuntu?

Are we facing a 64bit only issue here?

---

### Post by acebone on 2007-11-25
I have tried all the hacks I could find

Browsing is still painfully slow - torrent seems to run ok

---

### Post by nick_h on 2007-11-25
> **Beebock said:**
> Has anyone reported this in 32bit? or Kbuntu?
Are we facing a 64bit only issue here?

The libc6 upgrade fixed my problem on a 32 bit system.  The bug relates to only some ADSL routers and is one of a few bugs causing similar symptoms on Gutsy.

---

### Post by smellydog on 2007-11-26
> **Arik Amir said:**
> Hi All,

I made the changes as mentioned in this post:
1. I've added ipv6 to the blacklist 
2 disabled the ipv6 in Firefox
and still there are some web sites that do not load. I removed windows from this computer and installed ubuntu because I thought Linux desktop is up to par, I guess I was wrong, this computer is being used to access the internet mostly no special program needed just fast internet access and that doesn't work straight from the box, I'm disappointed.
I've installed my first Linux system back in 1993, it was a slackware distribution and it took three days to install because you had to compile a lot of the functionality by yourself, well Linux came a long long way from that but still lacks basic out of the box functionality to become a desktop.

I can tweek and recompile my system to make it work but that is not the point of out of the box.

the website that gives me the most problems is runescape.com, which my kids like to play at, any ideas to make me stick to linux desktop I would realy like to give it a shot

Well, i was messing around with some other distros... i found that PCLinux worked really well for me on the live CD.  I get my wireless working like it should just from the disk, so i am more than likely going to change to that or go back to feisty.  I am just frustrated that i can't get my wireless to work like normall.  The only drawback to PCLinux is that i am not too familiar with the KDE desktop.  I am sure i can get Gnome on it though, it is Linux after all!

---

### Post by StGermain on 2007-11-26
I have tried all of the hacks in this thread but still the only thing that works properly is using a 3com pcmcia card instead of the built-in Broadcom BCM4309. 

With the built-in card it often takes seconds to resolve an address then it goes to waiting for the website. With the 3com everything works normally...

The broadcom card works properly in Windows... (not that I want to use that anyway :)) and it works fine in Feisty but not in Gutsy.

---

### Post by tolremeno on 2007-11-26
Did you actually try switching from fwcutter to ndiswrapper? Did you make sure fwcutter was actually turned off? (You can install ndiswrapper but have ubuntu still use the restricted drivers, if you're not careful.)

---

### Post by Beebock on 2007-11-26
hi all,

i have been playing around with live cd and have reproduced this issue in both ubuntu and kunbuntu showing that this is an underlining issue in the distro

currently running feisty again as this is the only one that seems stable 
:(

richard

---

### Post by y0gz on 2007-11-26
I had that problem too, try adding "alias ipv6 off" to bad_list (create the file) in "/etc/modprobe.d/". it seems to fix the problem..
It's probably because IPv6 is making problem trying to make a connection or using it's protocol.

---

### Post by StGermain on 2007-11-28
> Did you actually try switching from fwcutter to ndiswrapper? Did you make sure fwcutter was actually turned off? (You can install ndiswrapper but have ubuntu still use the restricted drivers, if you're not careful.)

tolremeno I think you saved me... I went to system - administration - restricted drivers manager and turn the restricted drivers for broadcom wireless OFF, after a reboot everything seems to work fine... I have been surfing lots of websites for the last hour, streaming video works fine... looking good !:guitar:

---

### Post by stvdel on 2007-11-28
I can vouch for the change also, I was getting anywhere from 100-1000 Kbps steady depending on the time of day it was and now my wired connection starts quick at about 150 Kbps for around 10 seconds
and then drops down to like 15 Kbps and occasionaly drops out to zero and back to maybe 15 Kbps steady
I was starting to think my isp was throttling my connection.

---

### Post by fnx.lv on 2007-11-30
Hello everyone

I just thought I would add a few thoughts, seeing as I have the same problem and have tried all of the mentioned solutions to no avail.

When I first installed Gutsy my speeds were like everyone's, painfully slow compared to before.  But I noticed that when I used Nicotine, somehow my speeds would jump back up to 5000kbps+.  I took a few screenshots thinking they might come useful someday so I include them here.  Ever since then however, on a new Gutsy install I have not been able to get my speeds back to what they were, even after using Nicotine for an extended period of time.  

I have no idea what this means, since I am not skilled or trained in networking, but maybe someone out there could take a look at the Nicotine code and do some tests, possible giving the Ubuntu devs a heads up.  

(maybe Nicotine triggers some sort of packet flow)


Notice the Nicotine icons in the panels.

---

### Post by AJB2K3 on 2007-11-30
Ok I'm gunna add my 2 cents to this.

On 7.04 I used wifiradar as my connection manager but 7.10 uses mn-applet.
I havent tryed using wifi radar yet but can anyone conferm this?
IMHO I think it could be down to nm-applet.

OK heres some thing interesting.
My wireless is set to eth1 and when i changed to dhcp I get good signal but loose the signal icon.
How do i change it to the wireless port instead of eth1?

---

### Post by aubreyisland on 2007-12-03
I went into Synaptic and re-installed libc6 and it seems to have fixed the slow internet problem on my  Acer 5050-3371 (ZR3) w/ Atheros AR5BXB63 using Ndiswrapper on 7.10 Gusty.

**[Noticed it was slow when checking Gmail through Evolution]**

[COLOR="Red"][SIZE="1"]Note: Also enabled proposed-updates, but there was no libc6 update when I did it, then I re-installed libc6 and it worked.[/SIZE][/COLOR]

I can not wait until Ubuntu stops releasing every 6 months, what are  they thinking? Maybe I should run things over at Ubuntu!

](*,)

---

### Post by erothoff on 2007-12-04
An interesting note...
On my Xubuntu, I also am having really slow speeds on one of my two computers, (older ibm 500Mhz 512MB ram is slow with xubuntu i386, while my Core2 Duo screams with xubuntu64) but during the download packages, if I move my mouse constantly over the progress window, it downloads normally. Not a clue why though.

---

### Post by b_1_rd on 2008-01-14
> **charles woodward said:**
> Now that I've been able to use my other connection to get to the internet, I have found something that seems to solve my problem.  

It is mentioned in one of the threads - basically you have to edit a file :

the file is /etc/dhcp3/dhclient.conf

within this file you will see a commented out line (~prepend  )

add the following line :

prepend domain-name-servers 208.67.222.222, 208.67.220.220;



This certainly seems to have worked for me - I've now been up for nearly an hour and am experiencing no problems.    For the last week I have barely been able to stay up for more than a few minutes in Gutsy.

This seems to have worked for me,  Thank you.

I've been getting connection ok, through a wired card to router, but seemed to be suffering the burst problem.  I did go through some of the other fixes in this thread like disabling ipv6 and putting in router and IP DNS, so it maybe a combination of all, but the one above seems to have swung it.

Thanks again.  I'll post up and update if anything changes. :)

---

### Post by bilbobagins on 2008-02-01
Ha I just thought it was me having thried a few times to clean install Gusty and use Mr Compwiz excelent  broadcom 4318 instructions- have gone back to Good old Feisty Fawn.
Just hope thing are better with Hardy !:guitar:

---

### Post by Kurt Arndorfer on 2008-02-05
JillyJK you are the coolest.  For those still struggling with this, I had disabled ipv6 in firefox but it did not help.  I followed JillyJK's advice and disabled it in /etc/modprobe.d/aliases and things sped up immediately after a restart, then I added the settings into /etc/sysctl.conf and things were even faster.  Perfect.  I have been trying to get away from Windows for 2 years, but nagging wireless problems made it impossible.  Finally, broadcom drivers in 7.10 and today's fix make it all worth while.  I'm just enjoying the moment here.  I can't believe it's actually over and no more windows!

---

### Post by baixinhu on 2008-02-05
> **Kurt Arndorfer said:**
> JillyJK you are the coolest.  For those still struggling with this, I had disabled ipv6 in firefox but it did not help.  I followed JillyJK's advice and disabled it in /etc/modprobe.d/aliases and things sped up immediately after a restart, then I added the settings into /etc/sysctl.conf and things were even faster.  Perfect.  I have been trying to get away from Windows for 2 years, but nagging wireless problems made it impossible.  Finally, broadcom drivers in 7.10 and today's fix make it all worth while.  I'm just enjoying the moment here.  I can't believe it's actually over and no more windows!

can you help me do that to see if it works for me !!!
on aliases i comment this line #alias net-pf-10 ipv6 
on sysctl.conf what do i do? 

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.
kernel.maps_protect = 1

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1

---

### Post by pyter on 2008-02-19
Did anyone got a solution for this.

I've just installed Gusty Gibbon and I have the same problem with my wireless connection (didn't tried yet the Ethernet).

On Windows everything is fine. I have a WPA2 PSK AES with no SSID broadcast.

____________________

$ ping -c 4 google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from 64.233.187.99: icmp_seq=1 ttl=243 time=2244 ms
64 bytes from 64.233.187.99: icmp_seq=2 ttl=243 time=1860 ms
64 bytes from 64.233.187.99: icmp_seq=3 ttl=243 time=1750 ms
64 bytes from 64.233.187.99: icmp_seq=4 ttl=243 time=2042 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 47254ms
rtt min/avg/max/mdev = 1750.323/1974.383/2244.082/187.481 ms, pipe 3

---

### Post by seijling on 2008-02-20
OpenDNS - Definitely the way to go.


Much better. I felt kinda dirty not being able to update ;)

---

### Post by pyter on 2008-02-20
thanks ;)

---

### Post by Gannon8 on 2008-03-11
Do all these solutions work for kubuntu too?

Both wired and wireless is slow, and linux REALLLLLLY needs to release a bugfix.](*,)

---

### Post by feeble1 on 2008-03-26
I know absolutely nothing about this stuff and with my excuse on the table, this is what I found. I too was experiencing really slow internet, someone mentioned to install the epiphany browser. Well it seems to have the same lineage as FF but I did it anyway. 

Installed and rebooted, my wireless was much faster...... then I went back to FF and found that it too was faster ??  It could have been a coincidence, but I'm not changing anything.

regards. 1

---

### Post by hellomoto on 2008-03-27
I also had slow internet...blah blah... we all know the score. 

System info:

WG511v2 wifi card (using ndiswrapper)
Gutsy Gibbon user
compaq armada E500 pentium 3 (sub 500 mhz) 192mb ram --- aka old!


Here is what worked for me:


1. Disabled IPv6 in firefox

2. Disabled alias net-pf-10 ipv6 in /etc/modprobe.d/aliases

3. Edited (~prepend) in /etc/dhcp3/dhclient.conf


Now firefox works, email client works, pidgin works, updates work.

I'm not saying this will work for you just that it worked for me.
I'm not going into details into how to do the above 3 steps, read this thread
its all in here.

For other users  tips on problem solving:

1. Don't get stressed! - it won't solve anything!
2. If your tired take a break! - Go back to it in a few hours or a day or so.
3. My view is ubuntu is about problem solving... enjoy the challenge!


I have been using Linux now for 5 days, I put it on an old computer and took the attitude
I would learn and see what happens. My fancy desktop is on windows!

---

### Post by oztrailrider on 2008-04-22
I also had the same problems as most in this thread. Mainly slow DNS lookups when browsing. Actual connection speed was ok. I am using a wired connection with Hardy. I tried disabling ipv6 but that did not fix it, it's all good now that I have changed to the OpenDNS servers from my ISPs. The windows boxes I have here though seem fine...:confused:

---

### Post by thewebpromoter on 2008-04-24
Same problem with me, when I was asks to update Gutsy Gibbon, my connection works weird, what causes this?


Im using LinkSys.

---

### Post by TorqueyPete on 2008-04-27
I've a had painfully slow or failing wired internet browsing for more than a while, and was blaming my ISP, but since they don't know anything about Linux, no help there.

 I just found this thread this morning (amazed that I kept browsing for more than a few mins), and have disabled ipv6 in Firefox. I'll give that 2 days to confirm any change and come back here to report. If I have to make more changes I will build a list on this thread.


[B]LIST=

[/B]Disable ipv6 in Firefox. ( Thanks to Lord Darth Vader on page 3 ^^ for the tip )

 In firefox, type 
[B]about:config

Hit  'Go'
[/B] 
look for this:
**network.dns.disableIPv6**

 Double click that line to change the value to "true" 

That should fix the internet speed, at least in firefox.

---

### Post by TorqueyPete on 2008-04-27
I've a had painfully slow or failing wired internet browsing for more than a while, and was blaming my ISP, but since they don't know anything about Linux, no help there.

 I just found this thread this morning (amazed that I kept browsing for more than a few mins), and have disabled ipv6 in Firefox. I'll give that 2 days to confirm any change and come back here to report. If I have to make more changes I will build a list on this thread.


[B]LIST=

[/B]Disable ipv6 in Firefox. ( Thanks to Lord Darth Vader on page 3 ^^ for the tip )

 In firefox, type 
**about:config**

look for this:
**network.dns.disableIPv6**

 Double click that line to change the value to "true" 

That should fix the internet speed, at least in firefox.

---

