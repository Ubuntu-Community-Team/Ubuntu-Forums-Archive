---
title: "uughh I've been searching and tried everything"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by pete35887 on 2008-04-20
Internet still doesn't work.  I can load google.com, but that's it.  **I can't even load my router config page from ubuntu. ** I've changed dns servers to opendns's server, ive done the alias ipv6 off thing, I disabled ipv6 in firefox.  I blacklisted ipv6.  Hell i even downloaded and installed 8.04, after all else failed,  (started with 7.10) REPEATED everything and then some, with no luck.  I've tried static ip (the same way I have it set up in windows) auto dhcp, and all the other options.  

I've been trying since about 10 or 11am and it's 4:30pm now. This is just ridiculous.  I'm so sick of windows, I really want to get Ubuntu working, but it's not looking to good.  All websites ping fine.  I did a /etc/resolv.conf thingy also, checked out fine with opendns servers.  I am using opendns in windows right now and it works great.  Linksys wrt54g router v5, just updated firmware.  SiS190 ethernet adapter.  Wired connection.

Guys, I don't know what more i can do :\

64-bit ubuntu

---

### Post by pete35887 on 2008-04-20
guess im sh!t outta luck :\

---

### Post by Tomosaur on 2008-04-20
Which browser are you using? Seems very odd that websites ping fine etc. Can you download & install software through synaptic?

---

### Post by pete35887 on 2008-04-20
using firefox 3 b5 with 8.04 and i used firefox 2.0.0.6 or whatever comes with 7.10 .  I tried doing a system update and it stopped at 17/25 files.  It said the rest failed.  I had ipv6 turned off in both browsers etc.  Thanks for the reply.

---

### Post by djronh on 2008-04-20
You will not get on the internet unless you can find your router....for my system 192.168.1.1 
 which is entered in firefox address window. Then you now should see a box which asks for your router username and password. These detail and more are got from isp and router maker. DNS should not be important at this stage, however making sure your network settings are set to automatic DHCP is important.
Hm I had a wireless linksys 54 something from pcworld ....it kept dropping my internet connection and losing my router (like you), maybe overheating. I replaced it with a cheap £20 wired one from a computer fair which solved my problems. I upgraded the firmware like you.

---

### Post by pete35887 on 2008-04-20
> **djronh said:**
> You will not get on the internet unless you can find your router....for my system 192.168.1.1 
 which is entered in firefox address window. Then you now should see a box which asks for your router username and password. These detail and more are got from isp and router maker. DNS should not be important at this stage, however making sure your network settings are set to automatic DHCP is important.
Hm I had a wireless linksys 54 something from pcworld ....it kept dropping my internet connection and losing my router (like you), maybe overheating. I replaced it with a cheap £20 wired one from a computer fair which solved my problems. I upgraded the firmware like you.

after i entered my router login info it wouldnt do anything, it would just keep loading.  So, I could connect, but nothing would happen after i logged in (just like if i were trying to load a website).

Just did a fresh install, disabled ip6 and now i can't even get a ping from google (it wouldn't connect with ipv6 enabled either).  Tried multiple dns's, static ip, dhcp etc.  This is garbage, I've been fighting with this all day.

---

### Post by djronh on 2008-04-20
I suspect the router, you seem to know what your doing. Ubuntu is more than worth a cheap router. My linksys almost drove me insane! It got slung in the bin!

I think it was this [Linksys WAG54G Wireless ADSL Router]("http://www.expansys.com/p.aspx?i=113342")

---

### Post by pete35887 on 2008-04-20
hahah, this one is really gonna get you.   I've already tried hooking it up directly to my modem too.

---

### Post by djronh on 2008-04-20
Mine had a built in adsl modem, is yours just a router?

---

### Post by djronh on 2008-04-20
what kind of modem?

---

### Post by pete35887 on 2008-04-20
motorola sb5100 surfboard cable modem (has worked great the whole time i have had it) and a linksys wrt54g v5 with the latest firmware.

---

### Post by djronh on 2008-04-20
You need more than my opinion.....I say hardware problems (modem/router),

---

### Post by pete35887 on 2008-04-20
works fine in windows though....must be some sort of linux incompatibility/bug maybe? meh, who knows. stupid *** computers.

---

### Post by djronh on 2008-04-20
Yes, maybe. My £20 Hong Kong or whatever cheap adsl modem/router has served me better than my £55 Linksys ever did.

---

### Post by pete35887 on 2008-04-20
maybe i should try the 32-bit version?  Maybe it would make a difference?

---

### Post by djronh on 2008-04-20
I have only just noticed the 64bit...I only have 32bit P4 desktops and a laptop.

---

### Post by pete35887 on 2008-04-21
i ran the netstat -rn command this it what i got 




Kernel IP routing table
Destination         Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.100   0.0.0.0         UG        0 0          0 eth0

i don't know how to space it out :\ too tired to deal with it

fresh install of 32bit version 8.04 btw. ip6 disabled

any suggestions?

my gateway is 192.168.1.100
static ip is 192.168.1.102 
starting ip is 192.168.1.101 in router settings

---

### Post by prshah on 2008-04-21
> **pete35887 said:**
> hahah, this one is really gonna get you.   I've already tried hooking it up directly to my modem too.

I had the same problems, try changing the MTU in your router from the default of 1500 to 1492.. see my (solved) thread [http://ubuntuforums.org/showthread.php?t=718709&highlight=lynx+firefox](http://ubuntuforums.org/showthread.php?t=718709&highlight=lynx+firefox) about this.

---

### Post by pete35887 on 2008-04-21
> **prshah said:**
> I had the same problems, try changing the MTU in your router from the default of 1500 to 1492..


thanks, i'll try that out

---

### Post by pete35887 on 2008-04-21
> **prshah said:**
> I had the same problems, try changing the MTU in your router from the default of 1500 to 1492.. see my (solved) thread [http://ubuntuforums.org/showthread.php?t=718709&highlight=lynx+firefox](http://ubuntuforums.org/showthread.php?t=718709&highlight=lynx+firefox) about this.

well, changed my mtu and what do you know.   posting from linux now.  thanks so much.   One weird thing though.  It never worked without my router :O.  but hey, im not complaining.  Finally can kiss windows goodbye.  Well, besides for gaming unfortunately, but I do most of my gaming on the ps3 so it's all good.

might just have to do a reinstall on the 64-bit now :)

---

### Post by kevdog on 2008-04-21
Your solution is really strange.  My MTU is set at 1500 and I've never had any problem.  I wonder when this particular solution is applicable???  Any insight when this approach needs to be taken?

---

### Post by pete35887 on 2008-04-21
> **kevdog said:**
> Your solution is really strange.  My MTU is set at 1500 and I've never had any problem.  I wonder when this particular solution is applicable???  Any insight when this approach needs to be taken?

I agree, it is very strange.  Now that I've changed my mtu i don't even have to disable ipv6. If you can ping websites fine, but can't bring any up besides google, (while having ipv6 disabled and blacklisted), and tried static and auto dhcp/new dns's etc, give this solution a shot.  But you might even want to try it first because it is so simple.

But I still wonder why it wouldn't work when I hooked it up directly to my modem.

---

