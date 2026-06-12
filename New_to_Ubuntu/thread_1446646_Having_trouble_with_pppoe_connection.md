---
title: "Having trouble with pppoe connection"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by aloprot on 2010-04-04
Well I'm struggling with this problem for 2 months and no fix, no nothing. No one knows what to do and how to help me. It's simple, i have a pppoe connection. Sometimes it works, sometimes it don't....it's not the connection, on win xp a separate machine has 4 days uptime. Basicly ubuntu hangs up my connection when it wants. If i check plog in the terminal i get modem disconnected.
The problem is as same as this log found on the internet:
[I]bogdan@ubuntu:~$ plog
bogdan@ubuntu:~$ pon dsl-provider
Plugin rp-pppoe.so loaded.
bogdan@ubuntu:~$ plog
Nov 17 21:10:02 localhost pppd[5539]: Using interface ppp1
Nov 17 21:10:02 localhost pppd[5539]: Connect: ppp1 <--> eth1
Nov 17 21:10:05 localhost pppd[5539]: PAP authentication succeeded
Nov 17 21:10:05 localhost pppd[5539]: peer from calling number 00:10x:F3  authorized
Nov 17 21:10:05 localhost pppd[5539]: not replacing existing default route throu gh ppp0
Nov 17 21:10:05 localhost pppd[5539]: Cannot determine ethernet address for prox y ARP
Nov 17 21:10:05 localhost pppd[5539]: local  IP address **82.xxx.xx.253**
Nov 17 21:10:05 localhost pppd[5539]: remote IP address 10.0.0.1
Nov 17 21:10:05 localhost pppd[5539]: primary   DNS address 193.231.236.30
Nov 17 21:10:05 localhost pppd[5539]: secondary DNS address 193.231.236.25
bogdan@ubuntu:~$ plog
Nov 17 21:10:05 localhost pppd[5539]: secondary DNS address 193.231.236.25
Nov 17 21:11:15 localhost pppd[3645]: No response to 3 echo-requests
Nov 17 21:11:15 localhost pppd[3645]: Serial link appears to be disconnected.
Nov 17 21:11:15 localhost pppd[3645]: Connect time 3.4 minutes.
Nov 17 21:11:15 localhost pppd[3645]: Sent 75 bytes, received 75 bytes.
Nov 17 21:11:21 localhost pppd[3645]: Connection terminated.
Nov 17 21:11:21 localhost pppd[3645]: Modem hangup
bogdan@ubuntu:~$ plog
Nov 17 21:11:15 localhost pppd[3645]: No response to 3 echo-requests
Nov 17 21:11:15 localhost pppd[3645]: Serial link appears to be disconnected.
Nov 17 21:11:15 localhost pppd[3645]: Connect time 3.4 minutes.
Nov 17 21:11:15 localhost pppd[3645]: Sent 75 bytes, received 75 bytes.
Nov 17 21:11:21 localhost pppd[3645]: Connection terminated.
Nov 17 21:11:21 localhost pppd[3645]: Modem hangup
Nov 17 21:11:51 localhost pppd[3645]: PPP session is 1717
Nov 17 21:11:51 localhost pppd[3645]: Using interface ppp0
Nov 17 21:11:51 localhost pppd[3645]: Connect: ppp0 <--> eth1
bogdan@ubuntu:~$ plog
Nov 17 21:11:51 localhost pppd[3645]: Using interface ppp0
Nov 17 21:11:51 localhost pppd[3645]: Connect: ppp0 <--> eth1
Nov 17 21:11:54 localhost pppd[3645]: PAP authentication succeeded
Nov 17 21:11:54 localhost pppd[3645]: peer from calling number 00:10x:F3 authorized
Nov 17 21:11:54 localhost pppd[3645]: Cannot determine ethernet address for proxy ARP
Nov 17 21:11:54 localhost pppd[3645]: local  IP address **82.xxx.xx.30**
Nov 17 21:11:54 localhost pppd[3645]: remote IP address 10.0.0.1
Nov 17 21:11:54 localhost pppd[3645]: primary   DNS address 193.231.236.30
Nov 17 21:11:54 localhost pppd[3645]: secondary DNS address 193.231.236.25
bogdan@ubuntu:~$ plog
Nov 17 21:13:11 localhost pppd[5539]: Connection terminated.
Nov 17 21:13:11 localhost pppd[5539]: Modem hangup
bogdan@ubuntu:~$ plog
Nov 17 21:13:11 localhost pppd[5539]: Connection terminated.
Nov 17 21:13:11 localhost pppd[5539]: Modem hangup
bogdan@ubuntu:~$ plog
Nov 17 21:13:41 localhost pppd[5539]: PPP session is 1133
Nov 17 21:13:41 localhost pppd[5539]: Using interface ppp1
Nov 17 21:13:41 localhost pppd[5539]: Connect: ppp1 <--> eth1
Nov 17 21:13:44 localhost pppd[5539]: PAP authentication succeeded
Nov 17 21:13:44 localhost pppd[5539]: peer from calling number 00:10:F3 authorized
Nov 17 21:13:44 localhost pppd[5539]: Cannot determine ethernet address for proxy ARP
Nov 17 21:13:44 localhost pppd[5539]: local  IP address **82.xxx.xx.58**
Nov 17 21:13:44 localhost pppd[5539]: remote IP address 10.0.0.1
Nov 17 21:13:44 localhost pppd[5539]: primary   DNS address 193.231.236.30
Nov 17 21:13:44 localhost pppd[5539]: secondary DNS address 193.231.236.25
bogdan@ubuntu:~$
bogdan@ubuntu:~$

No one seems to know the problem or how to fix it? Now what do i do? Quit ubuntu?
[/I]

---

### Post by itiswhatitis on 2010-04-04
Don't quit!  Every problem has a solution!

Are you ADSL?

Who is your ISP?

Can you paste your peer file in?  (make sure you remove your password from what you paste!)

---

### Post by aloprot on 2010-04-04
Not adsl, I have a fiber optic cable in my house and from there there is a spliter that splits this fiber optic into 2 separate slots. One for my telephone line and one for a utp cable. I connect to the internet using that cable and a username and password provided by my isp. My isp has no problems, my connection has no problems I can assure you. The same connection on windows has uptime of over 4 days...I had 11 days uptime, no disconnects but I had to shut down the computer because I had to leave on vacation. The problem is clearly not my isp but something in ubuntu. I'm a beginner don't know what would help you more or what info to post. The thing is simple, my pppoe connection is not stable in ubuntu.

---

### Post by anewguy on 2010-04-04
Please understand that nobody is just saying your connection is bad - instead, please do as they have asked and post the information asked for.  We all know from our own experiences starting out that it can be frustrating at times, but please understand everyone is trying to help.  More information is needed as previously mentioned.  What type of PC?  What is the model/type of the "card" your fiber connects to?

Also, you said "....it's not the connection, on win xp a separate machine has 4 days uptime" - don't assume that if one computer is working that another "has" to - somethings might need to be changed or tweeked.

Let's start with some other basic information as well as that requested by others already:

in a terminal:

lspci

and

lsusb

Post the output from both of those back here along with the additional output requested from others previously, and we'll try to go from there.

Dave ;)

---

### Post by kaldor on 2010-04-04
Something very similar to this happened to me back on 7.10.

I upgraded to 8.04 when it came out, and I had no issues since.

Maybe you can try another distro?

Ubuntu is not the only easy Linux OS. Try Mint.

---

### Post by 3rdalbum on 2010-04-05
> **kaldor said:**
> Something very similar to this happened to me back on 7.10.

I upgraded to 8.04 when it came out, and I had no issues since.

Maybe you can try another distro?

Ubuntu is not the only easy Linux OS. Try Mint.

Mint is basically Ubuntu with a couple of extra programs; so if you're having a problem with Ubuntu you will have the same problem in Mint.

To the OP: It seems that Ubuntu is continually sending requests to the modem or router or whatever it is, in order to determine whether the connection is still up. But those requests, or at least some of them, are not getting through.

There may be a setting in your PPP configuration file that allows you to limit the number of requests it makes, or increase the number of requests that can fail to be returned before Ubuntu assumes that the connection is broken.

Also, try a different Ethernet cable, and make sure it isn't next to any devices that are putting out a lot of electromagnetic interference (like a microwave...).

I have never needed to use PPPoE from any Linux distribution so I really can't help with finding options in any PPP configuration files; it would be the blind leading the blind.

If you have a modem or router or something at your house (which I assume would be the case), it may have a web-based interface and the ability to initiate the connection itself. If this is the case, then definitely use it! That's what most ADSL and cable broadband modems do by default.

Definitely doesn't make sense for ISPs to require PPPoE on the computer, because of the number of home networks and net-connected game consoles out there!

---

### Post by aloprot on 2010-04-05
Hello, I tried so many times to configure with the help of ubuntu volunteers on irc the pppoe configuration file and I did increse the number of packets to wait before hanging up but nothig. That little box isn't a modem or a router, I know. It's just a fiber optic spliter like in this picture.
[http://dual-comm.com/EBAY/rj45_splitter_1ft_cables.jpg](http://dual-comm.com/EBAY/rj45_splitter_1ft_cables.jpg)

The first spliter withB and A. Thats what i have in my house. Outside where I leave maybe a router but in my house i have only a fiber optic cable and that spliter. I tried as I told you many many times to configure several network files ....with the help of volunteers on irc but nothing. Changed my network manager to wicd and still have problems with pppoe. I understand that this protocol is so exotic but it's my only option to connect to the internet right now. Anyway, what should I do? What distribution should i go then that has no pppoe issues like this? Don't get me wrong but I'm like driving an old car. Everytime I go on the road I am constantly thinking any second the car could leave me in the desert. That's what happens with my internet connection. And I can't work without it. What distro would you suggest then?

---

### Post by stderr on 2010-04-05
Hi aloprot,

Hehe I like the desert analogy. I wouldn't be too concerned; like many things in Linux, they can occasionally be quite difficult to get configured initially, but when set up they usually work flawlessly from then on. As for changing distro - I personally would recommend sticking and trying to resolve, but which distro you choose to use is a highly subjective thing - that's up to you :)

The fact that you tried NM and WICD is interesting...

But as everyone else has said, we really need to know what hardware you're running - so your network card for starters. As anewguy said, to get these details you could best post the output of "lspci" and the like. Also, it would help my understanding if you could post the output of "ifconfig" both when you have an active pppoe connection and after it's dropped.

Plus any other command line output you think may help us figure out what's happening. We really need command line output to help you further. 

Aside: I'm really no pppoe expert either I'm afraid! As you say, it's quite exotic :) but hopefully we can still help.

---

### Post by suzypeppercorn on 2010-04-05
If I am understanding things correctly, you have a fiber cable coming into your house, then a splitter is splitting that connection and from there you have an ethernet cable plugged into your computer.

Since Ubuntu isn't playing nice with your connection, can you try using a router in between your computer and the splitter? This configuration would allow your router to control the PPPoE settings so your computers would not have to at all. This would be an easier setup and allow any device you connect to your router to almost be plug and play without the need for configuring PPPoE settings.

If you don't have a router to play with, I would agree with the others that you need to decrease the time Ubuntu is checking for the connection and increase the threshold for dropping the connection. I have never even used a PPPoE connection so I'm not familiar with how to accomplish this but don't give up. There is always a way to do something. Good luck!

---

### Post by aloprot on 2010-04-05
Already  increased the threshold for dropping the connection, still the same issue. I don't have the money to buy a router right now, maybe in 4 weeks but what do i do until then? stay with no internet because of this problem? I have 10 minutes internet, then nothing ...then4 hours, then3 minutes....it's frustrating. could you please recommend me another distro that doesn't have problems with pppoe? and a wireless router that works under linux in generally since I have a brand new laptop, wireless would be better for me, I hate seeing white cable sticking in my laptop. Thanks!

---

### Post by suzypeppercorn on 2010-04-05
Sorry I can't be more help in regards to configuring PPPoE. I have never worked with it and don't know much about it. You could try another distro, maybe Fedora or CentOS. I have heard good things about both in general but nothing about its compatibility with PPPoE.

As for what router to choose, generally any wireless router you get is going to work fine. The problem many linux users run into with wireless networking is the lack of drivers for some wireless cards in laptops namely Broadcom. The support for these wireless cards has improved recently and my wireless card has gone from no support in 7.10 to plug and play in 8.10.

---

### Post by Steven_S on 2010-04-05
This is a n00b answer, so you probably should wait for others to have their say on this before you try... A little trip on Google got me these pages: 

[http://www.roaringpenguin.com/products/pppoe](http://www.roaringpenguin.com/products/pppoe) - "PPPoE (Point-to-Point Protocol over Ethernet) is a protocol used by many ADSL Internet Service Providers. Roaring Penguin has a free PPPoE client for Linux and Solaris systems to connect to PPPoE service providers."

Also found this: [http://tldp.org/HOWTO/DSL-HOWTO/configure.html](http://tldp.org/HOWTO/DSL-HOWTO/configure.html)

And when I searched for pppoe in synaptic, I saw that there are some applications that are not installed by default. Maybe somebody more knowledgeable can have a look at that list and suggest something ;-).

---

### Post by sdowney717 on 2010-04-05
> Well I'm struggling with this problem for 2 months and no fix

So did it ever work like it is supposed to work?
If so, then try doing a fresh install.

I would think if one time it worked, and now it does not then what has changed is a configuration file or some binary file.
Can this Internet connection style work on a live CD?

perhaps this is helpful
[http://www.ubuntugeek.com/how-to-setup-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-setup-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10-karmic.html)

---

### Post by albert s on 2010-04-05
I could be wrong here, I often am.
but if this is one cable simply being split to feed two computers, and the windows one is constantly on, couldnt there be a conflict here somewhere?
and the windows PC(being as they are) is demanding full service, thereby closing down the connection to the Ubuntu system.
my other thoughts would be with crosstalk, ie, windows trying to send a signal down the cable that is being pulled back into the ubuntu machine on the wrong wires(no crossover).
just something for the more knowledgable members to ponder.

---

### Post by wirelessmonkey on 2010-04-05
What albert s said.   If the fiber splits into two RJ-45s with no switch/router in the middle, then the two machines are conflicting.  The Ubuntu machine would disconnect, but windows machines would quietly keep trying to control the connection.  Basically the last machine to try to speak to the outside world would be the one to get the connection.

---

### Post by sdowney717 on 2010-04-05
> Since Ubuntu isn't playing nice with your connection, can you try using a router in between your computer and the splitter? This configuration would allow your router to control the PPPoE settings so your computers would not have to at all. This would be an easier setup and allow any device you connect to your router to almost be plug and play without the need for configuring PPPoE settings.


I like this solution. If the router controlled the login and maintained the login, then the only thing that ubuntu does is use the ehternet IP supplied by the router.

Here is a type of DSL router
[http://cgi.ebay.com/ACTIONTEC-GT701-WG-Hi-Speed-DSL-MODEM-Wireless-Router_W0QQitemZ110513568350QQcmdZViewItemQQptZPCC_Modems?hash=item19bb1f3a5e](http://cgi.ebay.com/ACTIONTEC-GT701-WG-Hi-Speed-DSL-MODEM-Wireless-Router_W0QQitemZ110513568350QQcmdZViewItemQQptZPCC_Modems?hash=item19bb1f3a5e)

---

### Post by mikewhatever on 2010-04-05
> **sdowney717 said:**
> I like this solution. If the router controlled the login and maintained the login, then the only thing that ubuntu does is use the ehternet IP supplied by the router.


It's not a solution, but rather a workaround. Hopefully someone with pppoe specific expertise sees this and will be able to provide relevant support.

---

### Post by Steven_S on 2010-04-06
I'm still curious to see the solution (and perhaps also how the information that many have already asked from the original poster may finally help to reach that solution). Maybe that information could be provided after all? It might help, you never know. There are also other suggestions in this thread I would most defenitely try and have a closer look at. 

I had PPPoe before and always had problems with it even in a Windows environment. From that experience, I at some point had a bit of a back-and-forth with the ISP helpdesk, who see from the other side what data came through and what not. In the end, they sold me a new splitter, and things were solved. To this date, I still don't understand why (as the splitter is - as I understand it - actually only needed to filter out the signal so that the phone would work). In that case, it wasn't the pc having trouble, but the wireless router. But in the end of the story: tech support from my ISP actually worked (took some time though).

I have upgraded (or better: updated) the connection and the router lately, and everything is super-smooth now.

If you want to try other distributions, if I were you, I would first go with a live cd - or more comfortable on a laptop: a live-usb, if you can get your BIOS to boot from usb. That way, you can easily and comfortably test a few and if they run, keep that setup until perhaps you are ready to install something permanent. I would try knoppix and puppy for sure - how to make a bootable usb stick from the live cd is explained on [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/).

---

### Post by aloprot on 2010-04-06
I think you got it wrong because of my vague explications. As I told you I have a fiber optic cable, in my house. From there, I have a spliter, not a modem not a router, a spliter just like the one I posted above. From there the spliter splits the fiber optic cable into 2. One slot is for a telephone line and one is for a lan cable to plugin. I connect to the internet using that lan cable, nothing else, just that lan cable and a username and password for the pppoe connection. This thing hasn't worked before, I tried several times fresh installs, and still the problem persisted. You got it wrong and excuse me for my vague details. I don't have 2 separate machines working together on the same cable to cause a conflict. I just tried the linux laptop and then shut it down and worked on windows for a couple of days. So there can't be any conflict since the two machines don't run together on the same time and on the same connection. I will try and see other distributions. MY point in this topic is not to flame with everyone or to acuse the developers or something. I just want to try and fix together this issue so that others will not have such a pain working with pppoe. If I can tell you more, or there are things that you want me to configure in order to see if this works please don't hesitate to tell here or message me. I hope we will fix this!
Thanks so much for all your support! ):P

---

### Post by dineshs on 2010-04-06
can you try this
[http://ubuntuforums.org/showpost.php?p=9082164&postcount=6](http://ubuntuforums.org/showpost.php?p=9082164&postcount=6)
Please backup the existing files for safety

---

### Post by anewguy on 2010-04-06
And the responses for our requests for information are where?

---

### Post by aloprot on 2010-04-06
What more information were needed? Did I forgot  to answer something?

---

### Post by anewguy on 2010-04-06
Go back through the thread and check each reply to you.  People have asked for your pppoe config file, lspci, lsusb, and other things.  So far I don't think I have seen those posted back here unless I missed them.

---

### Post by aloprot on 2010-04-07
I have carefully reviewed every post here to provide all the informations needed. First, excuse me in advance for not providing them, I didn't read with enough atention.
 I could not post because this problem happened again. I could not get into ubuntu forums, but finally seems after several endless restarts I am back with a stable connection.

First, I'm not using adsl, I'm using pppoe. I don't know what a peer file is, sorry I'm a beginner. I have a DELL inspiron 1545 laptop running ubuntu 9.10 amd64 version.
Output of lspci:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Output of lsusb:
Bus 001 Device 003: ID 0c45:63ee Microdia 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Ps:Anewguy, thank you and again, excuse me.

---

### Post by dineshs on 2010-04-07
can you try what I suggested in post #20.
Can you tell us how you are connecting in windows?

---

### Post by walt.smith1960 on 2010-04-07
I'm pretty new also and not an IT professional. I use Verizon DSL which uses a PPPoE connection.  I used Verizon's software in Windows just to make sure the connection worked properly. I then went out and bought one of these:

[http://homestore.cisco.com/Linksys-WRT54GL-Wireless-G-Router-Front-Page_stcVVproductId53934619VVcatId543809VVviewprod.htm](http://homestore.cisco.com/Linksys-WRT54GL-Wireless-G-Router-Front-Page_stcVVproductId53934619VVcatId543809VVviewprod.htm)

It is administered via a web interface. One the router's administration page is a section to set up PPPoE connections.  Mine has been perfect.  And yes, it runs on Linux :) There may be other better/cheaper options out there but this one works for me. It does not support N-speed connections if that matters. It's an additional cost but I'm using 2 laptops, one wired desktop, one wireless desktop and 3 networked printers, 2 BrotherMFD's  and one HP Photosmart.  They all play together nicely.

---

### Post by aloprot on 2010-04-07
[dineshs]("http://ubuntuforums.org/member.php?u=253252"), I forgot to do that. I went through all the steps and we'll see if this works. In windows I connect using network connections>create a new network>2nd option then>username, password and every time I login I click the icon and it authentificates on the network. Nothing special, no isp custom software or anything like that.

---

### Post by aloprot on 2010-04-08
[dineshs]("http://ubuntuforums.org/member.php?u=253252"), I did that, and still the same. I think that there might be a conflict between sudo pppoeconf(this is how i did my connection in the terminal) and network manager. It's strange, network manager won't work anymore, it's grey. Can't scan wireless networks, can't activate the DSL network i putted in, so strange. Is there a way to fix this? Maybe install wicd? But how do i drop sudo pppoeconf thing to not cause the conflict anymore?
Thanks!

Ps; if this helps you [http://serverfault.com/questions/3097/ubuntu-pppoe-connection-timeout](http://serverfault.com/questions/3097/ubuntu-pppoe-connection-timeout)
I get the same output in the terminal.

---

### Post by aloprot on 2010-04-09
The same issue, can't use my internet connection....this is becoming more and more frustrating.

---

### Post by aloprot on 2010-04-09
A router seems to be my only fix, but what about people with the same situation that can't afford a router?

---

### Post by mcavady on 2010-04-09
I would in that case put a switch/hub in the middle of your "splitter" and your machines. Just seems the logical thing to do.

If you have the same problem then it would be the "exotic" nature of your connection.

---

### Post by albert s on 2010-04-09
the other issue I have is that I dont think you have a fibre optic cable.
there is NO way you can have a fibre optic cable enter your house and just turn into a copper inside a splitter.
there MUST be something somewhere to change your fibre optic into an electrical signal for the copper connection (ie, RJ45/telephone).
there is much more to this than you suggest, either that or your supply company has misinformed you as to the cable you have.
fibre optic MUST enter a converter of some type somewhere.

---

### Post by wirelessmonkey on 2010-04-09
I assumed the splitter came out of the fiber termination box...

---

### Post by albert s on 2010-04-09
> **wirelessmonkey said:**
> I assumed the splitter came out of the fiber termination box...
possibly, but OP states that the only thing they have inside the house is this splitter thingie,
this makes me doubt fibre optic at all.
IMHO I have only ever saw FO either enter a router, or direct to a server/(the PC).
Im not a computer geek, but I have in the past installed Fibre Optic in my line of work.
something here just doesnt add up if this install really is fibre optic.

---

### Post by aloprot on 2010-04-09
It's a dark grey thin wire coming from outside.  There, outside there is a box om the wall and inside of it there is some sort of a router with many ports so that each neighbour gets acces to the internet. Inside my house as i said theres a dark grey thin wire, I think it's fiber optic wire, I don't know for shure but my connection is high speed stuff, from there, I have a spliter, not a modem not a router not anything, a simple spliter that splits that dark thin grey wire into one telephone port and one lan port. I connect to the internet using that lan cable and a username and password provided by my isp.
It's really frustrating that I can not get that issue fix...:( I wanted so much to stick with ubuntu.

---

### Post by aloprot on 2010-04-09
I don't know but I think there must be a solution, I don't afford now to buy a router....and since pppoe was implemented in ubuntu, I think it was implemented to be used no? I understand, please don't get me wrong, I don't want to insult no one or do a comparison like "windows pppoe works fine and ubuntu doesn't ...therefore ubuntu doesn't work...."I understand that this is a best-service -effort and I can assure you I get the thing that Ubuntu is not Windows. I just want to raise aware of this problem to the ubuntu developers. I know that by buying a router I will not have to use pppoe under ubuntu anymore because the router will take care of it. But as I said I don't afford one right now and I really need to use pppoe. Also I would advise the developers to look at the network manager. It's really bugged. For example I make a dsl connection>the I make it available for all users>apply and surprise....the dsl connection instead of being available for all users is gone. Maybe with the help of the developers we can fix pppoe under ubuntu and this issue with the network manager. Please bear with me and excuse me as I am a beginner. I tried to give you the best info I could....including my connection and everything. I try my best!

---

### Post by albert s on 2010-04-09
is it possible that we have an ADSL connection here?
Im pretty much sure now that it is deffo not a Fibre Optic we have.
possibly configuring the ADSL would sort this out.
can we assume this is broadband(as you say high speed),
so Im lost now as to why PPOE is needed.

---

### Post by anewguy on 2010-04-09
Believe me, pppoe does work - Ubuntu isn't released with something that basic that just plain doesn't work.  I'm in agreement that it is the "exotic" type of connection you are using.  You say this box on the outside of the house has multiple ports for other of your neighbors to plug into.  Are any of them connecting to the internet, and if so, what are they using after that box to connect?  I'm in agreement that it might be a DSL connection, but we would need the OP to check with whoever he needs to to find out just what type of connection it is and how they recommend connecting a computer to it.  Some homework I know, but it will help us help you.

Dave

---

### Post by anewguy on 2010-04-09
Okay, I just went back through the entire thread again, and followed the link again to an Ebay item the OP says it just like what they use as a splitter.  This thing looks like non-fiber connection, like a single cat5 in giving 2 cat5 ports.

Some information was asked for early in the thread by another replier:

who is your ISP, where are they based, and do they have a page on the net that references setup procedures, etc., that we can look at to try to determine what you have?


Dave

---

### Post by mikewhatever on 2010-04-10
Not sure if it's been mentioned, but why do you use ppoeconfig instead of the Network Manager?
Actually, the DSL settings of the Network Manager have the following: 'Send ppp echo packets'. Is it checked?

---

### Post by aloprot on 2010-04-10
Anewguy, my bad. I missed that too. I checked with different people who have my same connection and there is no fiber optic in my house. It's like you said a cat5 in giving 2 cat5 ports.One for my telephone and one for lan. Acces to the internet is provided through that lan cable and a pppoe connection with a username and password. This is 100% required in order to connect to the internet, and my isp to control it's users from illegal activities and such things(someone explained this to me). My isp is a local one, I'm living in Europe and my isp's page is in my native language which is not English. There is no details about the process of connecting...a neighbour who has the same isp and connection explained this to me. I hope this works. So to sum up I was bad, it's basicly a cat5 in giving 2 cat 5 ports. No fiber optic and such things. My bad, excuse me I was wrong.

---

### Post by aloprot on 2010-04-10
[mikewhatever]("http://ubuntuforums.org/member.php?u=160645"), tried network manager aswell with that option, the same. Network manager is really bugged. For example I have my dsl connection with username and password ok? So let's say I want to make that connection available to all users. I go to network manager, chose my connection and click Edit. I thick the available to all users box, and then apply. And then surprise surprise, my dsl connection is gone. Network manager is really bugged. I have tried for instance the same thing in Fedora, and there if i thick available to all users, and apply the info is saved and my dsl connection doesn't dissapear, so it's trully  a bug. Maybe right now you would say" hey well why don't you move there of fedora"? I don't like it and I don't want because I like Ubuntu.

---

### Post by mikewhatever on 2010-04-10
> **aloprot said:**
> [mikewhatever]("http://ubuntuforums.org/member.php?u=160645"), tried network manager aswell with that option, the same. Network manager is really bugged. For example I have my dsl connection with username and password ok? So let's say I want to make that connection available to all users. I go to network manager, chose my connection and click Edit. I thick the available to all users box, and then apply. And then surprise surprise, my dsl connection is gone. Network manager is really bugged. I have tried for instance the same thing in Fedora, and there if i thick available to all users, and apply the info is saved and my dsl connection doesn't dissapear, so it's trully  a bug. Maybe right now you would say" hey well why don't you move there of fedora"? I don't like it and I don't want because I like Ubuntu.

Are there other users on the computer? What if, for the sake of the argument, you don't make it available for all users just yet? Make sure the option I mentioned earlier is not checked.

---

### Post by aloprot on 2010-04-10
Dear Mike, i just did a fresh install of ubuntu amd 64 / 9.10, and checked the dvd for errors. No errors were find. I couldn't make my pppoe connection using network manager. I did enter the dsl connection info but when connecting to that network the net manager showed that i am disconnected from the network. Checked 10 times to see if i wrote everything correctly and  i did. Then i tried with sudo pppoeconf and it worked but as i told you is not stable. I just don't know what to do anymore. Tried wicd, the same thing. i just don't know what to try anymore. Tried with send ppp echo packets....tried without it....i'm not getting to any fix. I don't know  what else I could do.

---

### Post by mikewhatever on 2010-04-10
I see, this is a tough one. Have you tried searching for your ISP in conjunction with Ubuntu? Someone might have had the same problem and perhaps had it solved.

---

### Post by Brian Vaughan on 2010-04-10
I'm wondering if the router is set to only accept connections to specific MAC addresses, and it's set for the MAC address for the Windows laptop. You'd have to get someone to change the MAC address it accepts -- and it would probably be easier to get a cheap router and use its MAC address.

---

### Post by aloprot on 2010-04-10
My isp doesn't have things  like restricted acces based on mac or such things. Basicly every computer that is plugged into this connection works, so no mac restriction. People here aren't any help. I don't know many, they are usually windows users....those who aren't use other distros...and don't know anybody else who uses ubuntu.

---

### Post by NCLI on 2010-04-10
You would really benefit from getting a cheap router, like the Linksys WRT54G. Fantastic router, 44.95 USD on Amazon.

---

### Post by anewguy on 2010-04-10
For grins, try disconnecting every other device, including your phone, from the connection so it is just your single computer.  Try connecting again and see if it helps or not.

I'm a little confused on the phone - does it have some sort of adapter that plugs into the cat5 splitter and then the phone plugs into that adapter?  I ask because it sounds a little like Vonage and others do, and I assume you have to have an adapter.
Can you give us the name and model number of that adapter?

Thanks
dave ;)

---

### Post by aloprot on 2010-04-10
From that lan cable there is a pasive adaptor, like the one in the picture.....passive adaptor, splitte what ever you want to call it. Basically it creates 2 ports, the telephone port and a lan port. The phone line goes into that telephone port and the lan cable goes into the lan port. I don't know what else to tell you.

---

### Post by powder on 2010-04-10
I'm just jumping in here so sorry if this has already been said.  Most ISP's offer router/modem hybrids these days.  I would suggest calling your ISP and see if they'll trade your modem for one of these.

Personally, I bridged the router/modem from my ISP and connected it to a Linksys WRT54GL with Tomato firmware and it manages the PPPOE connection flawlessly.

---

### Post by aloprot on 2010-04-10
Hey poweder, sadly my isp won't do this. Seems like the only real solution now I have is to buy myself a router and let "him"manage my pppoe. I'm just worried that there might be others with my issue. And like myself can not afford right away a router.

---

### Post by anewguy on 2010-04-10
Believe me when I say there are many of us that can't afford to just go out and buy something, but I do think in your case if you can find a way to get some sort of router things would be better for you.

Also - what was the result of testing with all devices (including your phone) disconnected from the cabling except your computer?

Dave ;)

EDIT:  I'm not sure what the telephone wiring looks like overseas, but I would say that the splitter you posted the link to only creates 2 cat5 ports, so I guess your phone wiring must work different over there, or do you have a special phone?

---

### Post by anewguy on 2010-04-10
Forgive me if you posted this in detail and I missed it.

You mention running Windows on the same machine with no problems.  So, did you install Ubuntu as a dual-boot with Windows, did you install it as wubi, or are you just trying to run off a LiveCD or USB stick?

Dave ;)

---

### Post by aloprot on 2010-04-11
[anewguy]("http://ubuntuforums.org/member.php?u=331304"), I have tested like you said. Still the same problem, and excuse me if I  was wrong. I have a computer 2,8 intel celeron....running windows.That computer is mainly used as a offline computer and sometimes I like to play Age of Mythology on it or watch some dvd-s on it. When this problem happend I thought it was my connection. I said"hey let's try this in windows too...and I got a uptime of 4 days, 13 days with no disconnect and said hey ...trully this must be a problem with ubuntu somewere as my internet connection works fine." 
Hope this helps. Yes, I think that the router could and at the same time couldn't be helpful in resolving my connection. Sadly I don't know anyone that can borow me a router for a couple of days to see.
Ps: I have to computers in house, a laptop and a desktop pc. Laptop is running ubuntu amd 64 9.10 and desktop is running Windows Xp Prof.

---

### Post by mikewhatever on 2010-04-11
> Having trouble with pppoe connection 

Renaming the thread was a good idea, thank you mods.

---

### Post by anewguy on 2010-04-11
> **aloprot said:**
> [anewguy]("http://ubuntuforums.org/member.php?u=331304"), I have tested like you said. Still the same problem, and excuse me if I  was wrong. I have a computer 2,8 intel celeron....running windows.That computer is mainly used as a offline computer and sometimes I like to play Age of Mythology on it or watch some dvd-s on it. When this problem happend I thought it was my connection. I said"hey let's try this in windows too...and I got a uptime of 4 days, 13 days with no disconnect and said hey ...trully this must be a problem with ubuntu somewere as my internet connection works fine." 
Hope this helps. Yes, I think that the router could and at the same time couldn't be helpful in resolving my connection. Sadly I don't know anyone that can borow me a router for a couple of days to see.
Ps: I have to computers in house, a laptop and a desktop pc. Laptop is running ubuntu amd 64 9.10 and desktop is running Windows Xp Prof.

Okay, forgive me, but I'm a little confused.  Is the computer with Windows on it the very same computer with Ubuntu on it, or are they 2 seperate computers?  You indicate 2 seperate computers, and there lies the problem in the logic.  If the Windows desktop computer is the one you've tested that works okay, and the laptop running Ubuntu is the one that doesn't work okay, we have 2 completely different hardware platforms, so we can't compare the 2.

For the laptop, do you plug the cat5 cable directly into the laptop, or do you have an adapter card (perhaps PCMCIA or USB) that you use?

And, this is very important, when you are testing the Ubuntu laptop is the desktop computer still plugged in to the cat5 as well?

Dave ;)

---

### Post by aloprot on 2010-04-11
2 separate computers. No, when the laptop is on the internet i can't connect the windows machine because I only have one cat5 cable(I connect with a cat5 cable, not anything else..there's no usb, or anything like this...just a simple network cable plugged into that network slot.I plug this into my network slot in my laptop or my network slot in my mother board's computer. So, there's only one machine connected at the time, can't be both. Hope this helps.

---

### Post by anewguy on 2010-04-11
Okay, now we know they are truely 2 distinct pieces of hardware, so we can concentrate on the hardware that is running Ubuntu.

The first place to start is the brand, model and any other details you can give us of the laptop.  I have to assume the lspci done earlier really was from the laptop, and it says the network adapter is 09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13).  I've read some things on the net about this controller - mainly a debate between whether or not it has gigabit.  If so, I don't know if it makes any difference with Ubuntu (someone more knowledgable on that would need to tell you).  There are also a few posts that mention problems with the driver.  I also noticed your laptop has wireless - by any chance is the wireless connecting to some network and is connected at the same time you are trying pppoe (it might be doing so automatically without you requesting it)?  You may want to check network manager or wicd to see if a wireless connection is there at the same time you are using pppoe.

Dave ;)

---

### Post by aloprot on 2010-04-12
Yes the lspci is from the laptop. The laptop is a brand new DELL inspiron 1545. I don't use other networks such as wireless networks with pppoe only a single wired network connection. Also, because of using sudo pppoeconf in the terminal network manager doesn't work. It says"device not managed". I could not get it to work, entered the dsl connection info but it kept saying that i'm disconnected from the network. Revised 10 times to see if I typed wrong or something but I didn't. So I used sudo pppoeconf in the terminal, it was my only chance to connect to the internet. I have read here a topic that when using sudo pppoeconf, this command adds something in the network manager to tell him that the command is now managing the internet connection.
Hope this helps.

---

### Post by anewguy on 2010-04-12
Just for grins, please......

Forget about network manager not working with your pppoe connection.  Instead, we want to check in network manager to see *if* your wireless in configured (does it show wireless networks in the immediate area?) and is it connect to one (again, it's possible it did this without you knowing)?  I know you are probably thinking what the heck - I'm talking about pppoe NOT wireless, but there is a reason to the madness.  Please check it and then post back.  If it's not then we still need to look at something else, perhaps, as one of the sites on the net suggested, blacklisting the current driver for the Marvell network adapter and then trying to install the Windows driver with ndiswrapper instead to see if it helps.  Please note I'm not talking about installing a wireless driver, but rather installing the Windows version of your network adapter driver via ndiswrapper. 

All of this seems extreme to me, but I truely do believe there is something with the hardware that is causing your problem, and if the driver for your network adapter (Marvell) is flaky it could cause some problems.

Dave ;)

---

### Post by NCLI on 2010-04-12
> **aloprot said:**
> Hey poweder, sadly my isp won't do this. Seems like the only real solution now I have is to buy myself a router and let "him"manage my pppoe. I'm just worried that there might be others with my issue. And like myself can not afford right away a router.

If you do not get this working, I'd be willing to send you my old Linksys WRT54GL for free(Unless the price of shipping to where you live is crazy).

---

### Post by aloprot on 2010-04-12
[anewguy]("http://ubuntuforums.org/member.php?u=331304"), I can assure you I'm not connected to any wireless networks. I went outside to try a wireless network and I can't because the network manager is grey and it can't show any wireless networks. It says:"device not managed". So again, even if I am a gnu/linux beginner I know a little bit. I can assure you I am only connected to this wired network, no other network else.
[NCLI]("http://ubuntuforums.org/member.php?u=387344"), thank you so much. I hope I will get this issue fixed if not I will let you know. Deeply thanks, just for thinking means a lot for me. Thank you !

---

### Post by anewguy on 2010-04-12
So much for TRYING to help........

---

### Post by sanemanmad on 2010-04-12
Are you sure your line is receiving disconnects due to incorrect filtering? Does your Winfroze machine connect to a splitter, or does the cat5 cable? Who is your ISP? do you have vdsl? I have not gone through the logs you posted yet but these are the initial questions i have.

---

### Post by anewguy on 2010-04-12
> **sanemanmad said:**
> Are you sure your line is receiving disconnects due to incorrect filtering? Does your Winfroze machine connect to a splitter, or does the cat5 cable? Who is your ISP? do you have vdsl? I have not gone through the logs you posted yet but these are the initial questions i have.

With the utmost respect for jumping in here, I wish you the best of luck actually getting the information from the OP - you need to ask very clearly and give a reason why, it seems, before the information is provided.  ISP info has already been blown off earlier in a request because it's local and not in English - no name, etc., given so we could at least TRY to see if we could find any information on how you are to connect to them.  According to an earlier reply, the Windows machine was connected to the same cat5 cable coming from the splitter - they just unplugged the laptop and plugged in the Windows desktop.  OP seems somehow convinced that it purely Ubuntu - and maybe it is - but I'm still leaning towards some sort of issue of the laptop (Ubuntu) versus the desktop (Windows).  Note that the Windows machine and the Ubuntu machine are 2 different pieces of hardware, and the Ubuntu machine (laptop) uses a Marvell chipset network adapter (not wireless) that I have read some comments about on the net, including some suggesting ditching the built-in driver and installing the Windows driver via ndiswrapper.

I have also wondered if there is something between the wireless (Broadcom) driver and the hard wire (Marvell) driver that may somehow be stepping a little on each other's toes.  No idea there, don't know for sure if it's even possible, but since the OP is using pppoe......

I also requested checking to see if a wireless connection was established without the OP knowing it, to see if that was stepping on the hard wire connection, but as you can see from a previous post the OP says no wireless - but be aware it seems difficult to convince them to consider some ideas because to them it just can't be so, so end of story.  Sure, might be a long shot, but you never know unless you check everything.

If it does turn out to be Ubuntu that's fine - I won't complain.  Myself and others have only been trying to help the OP, no matter what the cause of the problem.

I truely wish you the best in helping the OP, as the only things we have been trying to do is help.  We all know that sometimes the answer isn't as simple as some think, and sometimes it takes a lot of digging around.  I really do hope that someone is able to help the OP, but I'm bowing out.

dave ;)

EDIT: I'm no mental giant nor Ubuntu guru - I've only been trying to help the OP.  If some of my suggestions have seemed strange, it's because the OP's problem is strange and you therefore sometimes have to look at things differently.  I'm the first to admit I can be an idiot, so forgive me if I've made suggestions here that seem crazy - it's just that almost everyone else who has replied seems to have run out of ideas also.

---

### Post by aloprot on 2010-04-13
[anewguy]("http://ubuntuforums.org/member.php?u=331304"), thank you for your support and everyone else. Please [anewguy]("http://ubuntuforums.org/member.php?u=331304"), I'm no guru either....and I don't know all the things..please don't be sorry. You tried to help me and I apreciate you and everyone who tried and tries to digg this with me in order to get this issue fixed.
  	sanemanmad, look at all my posts, you will find answers to your questions. I'm nearly always on this forum, again, I will try my best to supply all the information needed for you to help me. Hope I will get this issue fixed and enjoy internet under Ubuntu:)

---

### Post by aloprot on 2010-04-17
*bump!!

I don't know what I should do now?

---

### Post by aloprot on 2010-04-22
**Bump
Still no ideas of how I could fix this?

---

### Post by aloprot on 2010-05-13
I upgraded to amd64 10.04, and I was able to configure my internet connection using the network manager. But I still lose the internet connection under ubuntu even thou in Windows works fine. :|

Doesn't anyone have any clue why this is happening?

---

### Post by aloprot on 2010-05-14
Hey, again this issue has happened. I connect but i fail to resolve websites but my connection still remains active! No one has gone through the same problem?

---

### Post by lkraemer on 2010-05-14
What happens if you try this:

To set up the modem:
   1. Open Applications &#8594; Accessories &#8594; Terminal
   2. In the terminal type:
      sudo pppoeconf
   3. A text-based menu program will guide you through the next steps, which are:

         1. Confirm that your Ethernet card is detected.
         2. Enter your username.
         3. Enter your password.
         4. If you already have a PPPoE Connection configured, you will be asked if it may be modified.
         5. Popular options: you are asked if you want the &#8220;noauth&#8221; and &#8220;defaultroute&#8221; options and to remove &#8220;nodetach&#8221; - choose Yes.
         6. Use peer DNS - choose Yes.
         7. Limited MSS problem - choose Yes.
         8. When you are asked if you want to connect at start up, you will probably want to say yes.
         9. Finally you are asked if you want to establish the connection immediately.

   4. Once you have finished these steps, your connection should be working.

To start your ADSL connection on demand, in a terminal type:
**sudo pon dsl-provider**
 
To stop your ADSL connection, in a terminal type:
**sudo poff dsl-provider**

Is this typical of the commands you are using?

sudo dmesg
Can also give you more information on any errors.

REF:
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

You might want to read the information on Configuring by hand/The Chap Secrets file!

lk

---

### Post by aloprot on 2010-05-14
I used that command and had endless trouble with it as it disables my network manager- network manager didn't work for me on 9.94- it was really buggy.  I am able to setup my pppoe connection using the network manager but it disconnects randomly(the same issues as I had using pppoe)  and I can 100% say it's not the connection. It's very very frustrating as I am not able to buy a router- with which I would have solved the problem. I made great efforts to buy a laptop. But  [NCLI]("http://ubuntuforums.org/member.php?u=387344") has kindly offered me a router as a donation, to which I am very grateful.  So my issue will be fixed by having this router.

---

### Post by tsx2424 on 2011-04-15
I having an problem with my ISP connection as Fiber-optic.I setup my connection via Network manager.DSL setting and connection is work.but lack of speed as basically 4~6MB is now and unstable(some web site can not access)I checked Synaptic manager as trying to install PPPoE(support fiber optic connection)but I can not find it.  In Synaptic manager,I installed "PPP Over Ethernet driver" and "PPP config" but network Manager doesn't allow me access the internet.I check off the "PPP Over Ethernet driver" It works fine now.I'm assume the connection would not work when I restart the Ubuntu...

---

