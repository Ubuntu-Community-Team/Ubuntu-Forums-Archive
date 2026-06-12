---
title: "Can't make PPPoe connection to work"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by TellianGun on 2007-04-25
Hi.
I just installed Ubuntu 7.04 Feisty Fawn and I have some quite stubborn PPPoE instability.

I have pppd, pppoe, pppoeconf, pppdconf and a few other related packages installed.

I have a PPPoE/ADSL connection.
So, I open a term, become root and pppoeconf . Ok, so I configure it, I select Start at boot-up and Start Now.
Works good, but once I reboot, the connection will under no way start again, not even with pon dsl-provider!
If I run pppoeconf again, it works, but after a reboot, even after a thousand poff, pon and plog commands I can't
make it run.

Here's what I get after a reboot:

Apr 25 17:02:41 revans-domain pppd[6555]: primary DNS address 193.231.189.9

Apr 25 17:02:41 revans-domain pppd[6555]: secondary DNS address 193.231.189.18

Apr 25 17:03:25 revans-domain pppd[6720]: Plugin rp-pppoe.so loaded.

Apr 25 17:03:25 revans-domain pppd[6722]: pppd 2.4.4 started by revan, uid 1000

Apr 25 17:03:25 revans-domain pppd[6722]: PPP session is 302

Apr 25 17:03:25 revans-domain pppd[6722]: Using interface ppp1

Apr 25 17:03:25 revans-domain pppd[6722]: Connect: ppp1 <--> eth0

Apr 25 17:03:28 revans-domain pppd[6722]: Remote message: ^M^JAccess denied (external check failed).^J

Apr 25 17:03:28 revans-domain pppd[6722]: PAP authentication failed

Apr 25 17:03:28 revans-domain pppd[6722]: Connection terminated.



My main file is dsl-provider.
This is how it looks like:

pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1452"
#Also tried pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1412" but with no effect
#I haven't tried pty "/usr/sbin/pppoe -I eth0 -T 80"
noipdefault
usepeerdns
defaultroute
hide-password
lcp-echo-interval 20
lcp-echo-failure 3
connect /bin/true
noauth
persist
mtu 1492
noaccomp
default-asyncmap
plugin rp-pppoe.so eth0
user "usernamecensored"


I checked pap-secret and the password and username correspond with dsl-provider...

Any help guys? Please?

Thanks in advance!

---

### Post by TellianGun on 2007-04-25
Bump?

Btw, I've installed rp-pppoe client , ran the setup, configured everything. On Suse and other distros, rp-pppoe would always work, but now it times out...

What's wrong with my PPPoE ??

---

### Post by emartas on 2007-04-27
My pppoe connection in 7.04 does not work either. In 6.10 everythinkg is OK. I'm a bit dissapointed cause i cann't make connection with the new 7.04 thus using it doesn't make any sense. I will have to stick with 6.10. Does anybody know any solution?

---

### Post by Robban59 on 2007-05-06
Hi,

I also had the same problems as you, now all is working as it worked with Edgy; here is what I did : I uninstalled Network Manager, it was confusing pppoeconf I think; since I had installed also Firestarter, I verified that on boot the ADSL link with the provider was up, but Firestarter for some reason blocked all Internet access, so I made sure it didn´t  start at boot up ( you should install BUM [http://ubuntuforums.org/forumdisplay.php?f=75](http://ubuntuforums.org/forumdisplay.php?f=75) )  and after that, at boot up the ADSL link comes alive without problems right away.

Hope this helps/Robban59

---

### Post by acute on 2007-05-18
> **emartas said:**
> My pppoe connection in 7.04 does not work either. In 6.10 everythinkg is OK. I'm a bit dissapointed cause i cann't make connection with the new 7.04 thus using it doesn't make any sense. I will have to stick with 6.10. Does anybody know any solution?

Hi!

I suffered the same problem (couldn't go online), after having feisty installed a few days ago. That made me think about installing 6.10 at first, because I coulnd't find a suitable solution in other posts. But -- the 'deliverance' was quite more basic and not a linux' problem: I just configured my dsl-modem!

Doing that I figured out, that my (a few weeks ago freshly received) modem somehow worked with wlan on my other windows-machine without being configured before; and my xubuntu one is quite old and without wlan, and the lan-connection was still offline. So, while configuring I had to activate the lan/cable-connection, and now it works fine for me (well, I don't need wlan or a boot-up-connection at home). So fire up your browser and put in the modem's address, in (only?) my case it was 192.168.2.1, probably 'javascript' and/or 'windows' popping up' must be enabled.
No I enjoy working with Xubuntu Feisty  :-)

greetings -- acute

ps: anyway, that wouldn't consider the fact that your connection(s) worked on Dapper...

---

### Post by stereo3D on 2007-05-18
I have the same problem and I don't have a solution, I'm a n00b. 
Here is my story. I installed Ubuntu 7.04 as dual boot with Vista. I got my Earthlink DSL working with Vista then got it going in Ubuntu. It was not difficult so I didn't write down how I did it. I did have a problem with not being able to display any resolution other than 800x600 using the nVidia drivers, but that's another story. 

A few days later I discovered Ubuntu Studio and decided to switch, so I installed Ubuntu Studio over my regular Ubuntu 7.04.  Then I tried setting up the DSL connection and have had nothing but headaches since. Can't connect. During installation it fails to set up DHCP. I have re-installed both regular and studio versions of Ubuntu 7.04 about a dozen times and have tried many many variations on pppoe.conf-- nothing works. I've tried every setting in the network gui. 

I tried downloading Roaring Penguin's PPPoE software but I'm a n00b and don't know what to do when it fails to compile (something rather foreign to Windows users-- that you have to compile programs from source code). 

Thanks for reading about my problems. I'll keep looking for solutions. Thanks in advance for any suggestions. 

:(:confused:

---

### Post by stereo3D on 2007-05-19
:) I solved my connection problem. :)
The solution was to create a /etc/resolv.conf file containing my DSL provider's DSN name server IP addresses. Earthlink DSL requires these to be supplied, it doesn't use DHCP. 

Still a mystery to me why I was able to set up the connection the first time, but each time after the pppoeconf  utility did not allow me to enter nameserver IP addresses. 

I'll post this in a separate thread just in case there is another n00b using Earthlink PPPoE DSL is having the same problem.  

:)

---

