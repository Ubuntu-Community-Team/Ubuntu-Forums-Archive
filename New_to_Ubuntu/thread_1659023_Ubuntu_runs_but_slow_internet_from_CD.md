---
title: "Ubuntu runs but slow internet from CD"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by rodrickhales on 2011-01-03
New to Ubuntu Linux.  Made 10.10 CD.  I am running a wired connection on a desktop from a linksys router.  The ethernet card is SIS 190 10/100.  So when I boot Ubuntu from the CD, I can go to google.com, youtube.com, w3schools.com but other websites are very slow.  Most websites won't load even after a day of waiting.  My info from connections info is concurrent with what Windows has and Windows (of all things) works great with the internet.  I want to use the default DHCP settings and try a static IP address later when we get these issues sorted.  I have tried from router and I have bypassed the router.   I have tried a 10.04 CD; same thing.  Everything seems to work fine except this very critical part.  What have I done wrong?  Any suggestions would be greatly appreciated.  Thanks.

---

### Post by perspectoff on 2011-01-03
Duh. It has to run programs from the CD.

If you want better performance, install to the hard drive.

PS You waited a day for a website to load?

---

### Post by rodrickhales on 2011-01-03
I tried this several different times from different websites. Its was a test to see if the websites were slow loading or if I was having hardware issues.  Duh.  I didn't sit there all day. Duh.  What does this have to do with basic functionality like visiting a website like Ubuntu doesn't offer, hmmmm? Why would I install something on my hard drive that can't visit or download on all the normal websites?

---

### Post by mick222 on 2011-01-03
Ubuntu runs as fast or faster than windows .Bit you are limited by the speed of your cd drive when running live. Everything is running on systam memory. Try installing to your hard drive or install Wubi inside windows.
 You dont need to get rid of windows as install gives you the option to dual boot.

---

### Post by rodrickhales on 2011-01-03
Still, what you are saying is that just because I boot from the ubuntu CD I can't go to any website.  Is that it?

---

### Post by rodrickhales on 2011-01-03
Also, Network Connections says 'Auto Eth0' was last used never.  I went to google.com and youtube.com (even though I was unable to download the flash plug-in and view any videos).

---

### Post by audiomick on 2011-01-03
> **rodrickhales said:**
> Still, what you are saying is that just because I boot from the ubuntu CD I can't go to any website.  Is that it?
It may be that the Ubuntu on the CD doesn't have Flash on it. I think you only get that after you have installed ubuntu-restricted-extras. 

That would explain some websites not working, I think. The reason Flash, along with some other stuff, is not included has to do with licensing.

Here, some reading:
[https://help.ubuntu.com/8.04/internet/C/web-browsing.html](https://help.ubuntu.com/8.04/internet/C/web-browsing.html)

---

### Post by mick222 on 2011-01-03
A live cd is only for trying out ubuntu to make sure your hardware is compatible.you have no hard drive to install anything to therefore you cant install anything . Thats why you cant visit flash sites .As i said before try wubi from windows if you don't want to install to your harddrive.[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by Verbeck on 2011-01-03
> **rodrickhales said:**
> Also, Network Connections says 'Auto Eth0' was last used never.  I went to google.com and youtube.com (even though I was unable to download the flash plug-in and view any videos).
only the 'Auto "interface name"' does that,
so just create a new one

---

### Post by rodrickhales on 2011-01-03
Well folks, I used the Wubi approach and it installed again.  This time it was 10.04.  There were certain parts I wanted to give a chance to install but I just skipped because it was taking way too long.  The results are websites visited and results:

google.com : yes, lightning speed
gmail.com : yes, lightning speed
yahoo.com : no
msn.com : no
w3schools.com : yes, lightning speed

Conclusion: Ubuntu is very selective about the websites it wants Firefox to go to.  Any other suggestions?

---

### Post by kroq-gar78 on 2011-01-03
did you install ubuntu-restricted-extras AFTER you installed ubuntu?

---

### Post by jtarin on 2011-01-03
Post your /etc/resolv.conf file. Running a CD you more than likely are having DNS problems.These settings will not persist through the next boot when running off the CD, but lets see that file while its running.

---

### Post by kane.sattyajit on 2011-01-03
ok make a booteble pen drive.
 their is a tool in ubuntu to make a booteble pen drive
and u boot ubuntu 10.10 from the pen drive its having good speed to performing any application and internet also. and 
After that its not working then chackout ur network speed on speedtest.com

---

### Post by rodrickhales on 2011-01-04
SOLVED! Went to edit connections and renamed connection from 'auto eth0'  to 'eth0'.  What a dirty trick to play on someone!  Thanks a lot  everyone that responded.

---

### Post by rodrickhales on 2011-01-04
Was solved when I renamed 'Auto eth0' to 'eth0' ... spoke to soon.  I rebooted and back to square one. Partially loading pages (if any loading).  Open to more suggestions.  Thanks.

---

### Post by jtarin on 2011-01-04
Did you try my suggestion above in my last post?

---

### Post by rodrickhales on 2011-01-05
I have since installed the ubuntu OS. Should I still cat /etc/resolv.conf ?

---

### Post by rodrickhales on 2011-01-05
> **kroq-gar78 said:**
> did you install ubuntu-restricted-extras AFTER you installed ubuntu?

How to install this if no internet?

---

### Post by jtarin on 2011-01-05
> **rodrickhales said:**
> I have since installed the ubuntu OS. Should I still cat /etc/resolv.conf ?Only if your still needing help with the same issue. Otherwise its pointless.

---

### Post by rodrickhales on 2011-01-05
cat /etc/resolv.conf

# Generated by NetworkManager
domain hsd1.ms.comcast.net.
search hsd1.ms.comcast.net.
nameserver 68.87.68.166
nameserver 68.87.74.166
nameserver 192.168.1.1

---

### Post by TechWiz2100 on 2011-01-05
Your DNS is fine, I would say the problem is either your router acting up to a new device on the network or your network settings are a bit screwed

run the following commands and post results please:

```
ifconfig
lspci | grep controller

```

---

### Post by jtarin on 2011-01-05
> **rodrickhales said:**
> cat /etc/resolv.conf

# Generated by NetworkManager
domain hsd1.ms.comcast.net.
search hsd1.ms.comcast.net.
nameserver 68.87.68.166
nameserver 68.87.74.166
nameserver 192.168.1.1
Is this persisting through reboots and you don't have to configure it? Now let's see your /etc/dhcp3/dhclient.conf.

---

### Post by rodrickhales on 2011-01-06
I checked today.  It does persist through reboots.  

ifconfig
______

eth0      Link encap:Ethernet  HWaddr 00:17:31:84:e6:b5  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe84:e6b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:875 errors:203 dropped:0 overruns:0 frame:203
          TX packets:752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:680208 (680.2 KB)  TX bytes:79317 (79.3 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9991 (9.9 KB)  TX bytes:9991 (9.9 KB)


lspci | grep controller
_____

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Ethernet Adapter
00:08.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
03:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)

cat dhclient.conf
_____

# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

Thanks for responding.

---

### Post by TechWiz2100 on 2011-01-06
I see almost a 25% package failure rate on the receiving end there

Your controller the SiS 190 might require you to download and/or compile drivers for it and that could potentially be the issue.
[http://www.sis.com/download/download_step2.php?id=155884&country=&Image791.x=78&Image791.y=3]("http://www.sis.com/download/download_step2.php?id=155884&country=&Image791.x=78&Image791.y=3")

I don't know about the DNS report but everything looks fine for DNS based off of your other reports

---

### Post by jtarin on 2011-01-06
Clarify things a bit for me concerning your connection. I'm going to assume you have a cable connection as your resolve.conf refers to Comcast. If this is correct did Comcast give you a modem to use? I don't see it in your "ifconfig". Are you assigned a static IP?

---

### Post by rodrickhales on 2011-01-06
I guess I will try to install the driver from the website.  How do I find out what drivers I already have?  Which one of the commands will do this?

---

### Post by rodrickhales on 2011-01-06
> **jtarin said:**
> Clarify things a bit for me concerning your connection. I'm going to assume you have a cable connection as your resolve.conf refers to Comcast. If this is correct did Comcast give you a modem to use? I don't see it in your "ifconfig". Are you assigned a static IP? Yes I have the comcast cable connection. They did give me a modem to use. I am on DHCP.  I want to be on that until I get this problem solved.  Then "hopefully" the settings will let me change to static IP.

---

### Post by TechWiz2100 on 2011-01-06
> **jtarin said:**
> Clarify things a bit for me concerning your connection. I'm going to assume you have a cable connection as your resolve.conf refers to Comcast. If this is correct did Comcast give you a modem to use? I don't see it in your "ifconfig". Are you assigned a static IP?

Cable modems don't require static IPs, only DSL or really REALLY crappy modems which Comcast does not use AFAIK.

Also based on his resolv.conf, he is hooked up directly to his modem because DHCP set his IP to 192.168.1.101 which would be the start of the generic modem DHCP pool rather than a router's 192.168.1.2... unless there are 99 other computers on his network or his DHCP is acting up lol. And his modem is potentially a wireless model because it lists 192.168.1.1 as a name server.

---

### Post by rodrickhales on 2011-01-06
> **TechWiz2100 said:**
> Cable modems don't require static IPs, only DSL or really REALLY crappy modems which Comcast does not use AFAIK.

Also based on his resolv.conf, he is hooked up directly to his modem because DHCP set his IP to 192.168.1.101 which would be the start of the generic modem DHCP pool rather than a router's 192.168.1.2... unless there are 99 other computers on his network or his DHCP is acting up lol. And his modem is potentially a wireless model because it lists 192.168.1.1 as a name server.
I am hooked to a router (linksys).

---

### Post by TechWiz2100 on 2011-01-06
> **rodrickhales said:**
> I guess I will try to install the driver from the website.  How do I find out what drivers I already have?  Which one of the commands will do this?

```
lsmod
```

Odds are there isn't a driver in place designed for your hardware and the hardware is working its magic with generic instruction from a generic driver

> **rodrickhales said:**
> I am hooked to a router (linksys).

How odd that your router sets DHCP to start at 101 and list the modem's DNS as name server

---

### Post by jtarin on 2011-01-06
Try this....make a backup of your resolv.conf....then make a new one with only these entries.Then try to browse. 
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```You'll need to do as root/sudo and make sure it has the same permissions.

---

### Post by rodrickhales on 2011-01-07
> **jtarin said:**
> Try this....make a backup of your resolv.conf....then make a new one with only these entries.Then try to browse. 
```
nameserver 8.8.8.8
nameserver 8.8.4.4.
```You'll need to do as root/sudo and make sure it has the same permissions.

What is with the periods on the the ends ( nameserver 8.8.4.4. )   Is this OK?

---

### Post by jtarin on 2011-01-07
> **rodrickhales said:**
> What is with the periods on the the ends ( nameserver 8.8.4.4. )   Is this OK?Of course not....:oops: My error...before I coded it, it was a sentence and like all good sentences it ended with punctuation.

---

### Post by rodrickhales on 2011-01-09
> **jtarin said:**
> Try this....make a backup of your resolv.conf....then make a new one with only these entries.Then try to browse. 
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```You'll need to do as root/sudo and make sure it has the same permissions.

Thanks.  It tried this.  It failed.  I will try to re-install the drivers next.

---

### Post by rodrickhales on 2011-01-09
> **TechWiz2100 said:**
> I see almost a 25% package failure rate on the receiving end there

Your controller the SiS 190 might require you to download and/or compile drivers for it and that could potentially be the issue.
[http://www.sis.com/download/download_step2.php?id=155884&country=&Image791.x=78&Image791.y=3](http://www.sis.com/download/download_step2.php?id=155884&country=&Image791.x=78&Image791.y=3)

I don't know about the DNS report but everything looks fine for DNS based off of your other reports

I have downloaded the latest linux driver for it.  What are simplest instructios on reinstalling drivers?

---

### Post by jtarin on 2011-01-09
[Actually the updating the driver does not seem to be the total solution.Your almost better off getting a more compatible card]("http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6")

---

### Post by rodrickhales on 2011-01-10
> **jtarin said:**
> [Actually the updating the driver does not seem to be the total solution.Your almost better off getting a more compatible card]("http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6")

This is what I am talking about.  I thought this would be a walk in the park.

---

### Post by jtarin on 2011-01-10
> **rodrickhales said:**
> This is what I am talking about.  I thought this would be a walk in the park.It is.....Central Park at 2am.:P

---

### Post by rodrickhales on 2011-01-10
> **jtarin said:**
> It is.....Central Park at 2am.:P

Ha Ha.  Where is a list of compatable PCI network cards for Windows AAAAAANNNNNNDDDDDDDD Linux?  Did anybody see where I got it to work at least once? And then it stop working again.

---

### Post by Mindswap1 on 2011-01-10
Hey mate the solution is actually really simple, and takes like 10 secs max to do. What you want to do is open up firefox, and in the adress bar type in > about:config. It may give you a warning about how you probably shouldn't mess with it, but you can go ahead and ignore that. Then where it says filter copy and past the following. 

> network.dns.disableIPv6

Now once you've done that a line should come up that says boolean, and then at the end it says false. Go ahead and double click that making it true. Close firefox, and then open it up again, and it should be a lot faster. Cheers.

---

### Post by TechWiz2100 on 2011-01-10
About 80-90% of hardware will work on the newer versions of windows and about half of those work flawlessly on Linux.

Realtek seems to be a good sport in the open source community, try one of their cards.

The best way to tell if a card is compatible with Linux is to see if they have some linux or OS X drivers available, then check to see if they've been left open source or ported to linux if the latter case applies.

[Oh and heres your post for when you fixed it]("http://ubuntuforums.org/showpost.php?p=10314316&postcount=14")

---

### Post by jtarin on 2011-01-10
> **rodrickhales said:**
> Ha Ha.  Where is a list of compatable PCI network cards for Windows AAAAAANNNNNNDDDDDDDD Linux?  Did anybody see where I got it to work at least once? And then it stop working again.I agree about Realtek.I've never had a problem with any. You can see some takes on it and others [here]("http://linuxhcl.com/browse/search+network-cards?category=30").

---

### Post by jtarin on 2011-01-11
Edited for redundant post.See above

---

### Post by rodrickhales on 2011-01-11
> **Mindswap1 said:**
> Hey mate the solution is actually really simple, and takes like 10 secs max to do. What you want to do is open up firefox, and in the adress bar type in . It may give you a warning about how you probably shouldn't mess with it, but you can go ahead and ignore that. Then where it says filter copy and past the following. 



Now once you've done that a line should come up that says boolean, and then at the end it says false. Go ahead and double click that making it true. Close firefox, and then open it up again, and it should be a lot faster. Cheers.

Nice try.  Already done it.  Same results.

Folks, I bought this computer from a system admin guy who did the same  thing I did with Windows XP and Ubuntu.  He said he never had a problem  with it and now all of a sudden I have problems with network cards?  It  just doesn't make any sense why it would work fine in Windows and not  Ubuntu. Before I'm done its seems like the whole world will know I tried  to do this.

During the installation it was trying to download some files from the internet and such.  Since the internet in Ubuntu was useless, I would guess this would probably be part of the problem.

---

### Post by rodrickhales on 2011-01-12
I looked at my motherboard specs.  It is an A8S-X SE.  It says it already has a Realtek RLC8201 Cl 10/100 Mbps LAN PHY on board.

---

### Post by TechWiz2100 on 2011-01-12
Try ethernet off your mobo's RLC8xxx and report back. 

If the SiS card works fine in Windows then its definitely because SiS is bad at writing *nix drivers lol

The open source drivers prolly suck as much because SiS probably put in a lot of spaghetti code or some proprietary compiled crap. Who knows

---

### Post by rodrickhales on 2011-01-13
> **TechWiz2100 said:**
> Try ethernet off your mobo's RLC8xxx and report back. 

If the SiS card works fine in Windows then its definitely because SiS is bad at writing *nix drivers lol

The open source drivers prolly suck as much because SiS probably put in a lot of spaghetti code or some proprietary compiled crap. Who knows

Seems like we will be closer to a solution soon but let me clarify something.  I don't know why this  is but mobo's onboard network card (RJ-45) is RLC8xxx but the controller  is SiS 190 10/100 .  The onboard network output is the only one available.  This does work in Windows but why do they have SiS 190 10/100 controller for RLC8xxx onboard interface?  Seems as if it would have been RealTek controllers/drivers/etc.  I guess instead if trying to make Sis controllers work, I should be trying to make RealTek controllers work with this onboard interface.  Am I on the right track anyone?

---

### Post by TechWiz2100 on 2011-01-13
Oh, I checked up the specs for that mobo and it seems the reason you have a SiS ethernet controller is because you have a SiS southbridge

Try installing the Realtek drivers anyway see if they can take over even though its a SiS chipset.

This is probably another one of those cases where a Realtek chip is taken by a 3rd party and modifed and renamed to be used as one of their own

---

### Post by rodrickhales on 2011-01-22
Well folks.  I tried the usb straight from the cable modem and what do ya know; works without a problem.  Not even one packet error and I can go to all the websites.  That means the problem is ethernet card or drivers.  I have not found a solution to get it to work.  Guess I will keep searching ( if the are any solutions:) ).

---

