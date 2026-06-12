---
title: "Remote Assistance Support?"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by mapes12 on 2009-08-08
Hi

I've just installed Ubu 8.04 on my Dad's machine but he has a few problems. He lives some miles away from me and we both access the internet via broadband. I'm looking for an _easy_ way for me to take control of his desktop so that I can poke around and help him out. Most of the posts and other sites I've been to have some complicated configuration stuff about vnc, reverse vnc and other stuff that's over my head, and definitely over my Dad's head! 

Googling lead me to Gitso which I installed on my machine but the problem is that I have a BTHomeHub ADSL router that will not let me in (it will not accept any of the username and password configurations - and I've tried loads!) to configure the required port forwarding on 5500 per the Gitso instruction page.

As for the BTHomeHub this is the resource I've used to get in: [http://www.frequencycast.co.uk/homehubfaq.html#login](http://www.frequencycast.co.uk/homehubfaq.html#login)

I can successfully call the hub up in my browser with [http://bthomehub.home](http://bthomehub.home) but then can't get into the advanced functions cos it will not accept any of the username and password suggestions.

Any help really appreciated.

---

### Post by juancarlospaco on 2009-08-08
**FreeNX**
:)

---

### Post by Paddy Landau on 2009-08-08
Have you tried using the built-in Remote Desktop?

On your Dad's machine:

[LIST]
[*]System > Preferences > Remote Desktop
[/LIST]
On your machine:

[LIST]
[*]Applications > Internet > Remote Desktop Viewer
[/LIST]
I confess that I've not tried it before, so I can't answer any questions about it. However, you may need to get your router to pass through the connection.

Good luck.

---

### Post by mapes12 on 2009-08-08
> **juancarlospaco said:**
> **FreeNX**
:)Thank you!

I found the FreeNX website here: [http://freenx.berlios.de/](http://freenx.berlios.de/)

Had a look around but unfortunately it doesn't provide an idots guide to:
a) what it does?, and more importantly 
b) how to set it up and use it, step by step?

Does anyone know of any newbie guides for this application please cos it looks promising.

---

### Post by mapes12 on 2009-08-08
> **Paddy Landau said:**
> Have you tried using the built-in Remote Desktop?

On your Dad's machine:

[LIST]
[*]System > Preferences > Remote Desktop
[/LIST]
On your machine:

[LIST]
[*]Applications > Internet > Remote Desktop Viewer
[/LIST]
I confess that I've not tried it before, so I can't answer any questions about it. However, you may need to get your router to pass through the connection.

Good luck.Thank you!

From what I've read this solution only works _easy_ over a LAN or intranet WAN. Apparently, it requires configuration of this VNC stuff to work over the internet and the VNC guides I've read are too complicated for me and my Dad. He's 75 by the way.

I really appreciate you Guys coming back to me. Thanks.

---

### Post by Paddy Landau on 2009-08-08
> **mapes12 said:**
> I found the FreeNX website...
Try the [Ubuntu FreeNX]("https://help.ubuntu.com/community/FreeNX") documentation.

---

### Post by terry_gardener on 2009-08-08
you might want to check you this link 

[http://ubuntuforums.org/showthread.php?t=926098]("http://ubuntuforums.org/showthread.php?t=926098")

---

### Post by terry_gardener on 2009-08-08
also check out 

[https://launchpad.net/remote-help-assistant]("https://launchpad.net/remote-help-assistant")

not used it myself but seems interesting

---

### Post by scorp123 on 2009-08-08
> **mapes12 said:**
>  I've just installed Ubu 8.04 on my Dad's machine but he has a few problems. He lives some miles away from me and we both access the internet via broadband. I'm looking for an _easy_ way for me to take control of his desktop so that I can poke around and help him out. I use **Gitso** .... It's very easy: All he needs to do is to click on an icon ... And poooof! you get to see his desktop. The steps to get this configured are relatively easy on his side. The complicated stuff (finding your public IP, configuring port forwarding so port 5000 TCP can get through to your LAN, etc.) is all on _your_ side ... which is OK.

I use Gitso to support my wife's parents (they're 70+ years old!) who live some 1200 km away from us. I created a pre-configured icon for them (very easy to do once you are connected to the desktop ...) so they now just need to click on it and I instantly get to see their desktop. Very easy to use. So what Gitso does in principle is a so called "Reverse VNC Connection". Whatever. It just works.

Gitso Homepage:
[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

---

### Post by terry_gardener on 2009-08-08
gitso sounds great. 
thanks for this.

---

### Post by mapes12 on 2009-08-08
> **scorp123 said:**
> I use **Gitso** .... It's very easy: All he needs to do is to click on an icon ... And poooof! you get to see his desktop. The steps to get this configured are relatively easy on his side. The complicated stuff (finding your public IP, configuring port forwarding so port 5000 TCP can get through to your LAN, etc.) is all on _your_ side ... which is OK.

I use Gitso to support my wife's parents (they're 70+ years old!) who live some 1200 km away from us. I created a pre-configured icon for them (very easy to do once you are connected to the desktop ...) so they now just need to click on it and I instantly get to see their desktop. Very easy to use. So what Gitso does in principle is a so called "Reverse VNC Connection". Whatever. It just works.

Gitso Homepage:
[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)Thank you very much for your post. 

You mention port 5000. I've had a look at the link you provided and it says "The person who is going to “give support” must have port 5500 open to their PC". Should I open 5000 or 5500 please?

Also, do you have an easy guide to follow or a screen shot that could help please? Thank you.

---

### Post by terry_gardener on 2009-08-08
you are going to need to forward 5500 if you are behind router/nat device 

i have tested this tonight and you dont need to do anything with ubuntu 

sorry cant give screen shot on port forwarding as each router is different.

---

### Post by terry_gardener on 2009-08-08
it works ok aswell 

screen rendering was abit slow but expected really

---

### Post by scorp123 on 2009-08-08
> **mapes12 said:**
> Should I open 5000 or 5500 please?  ... Checking my router's settings ....

Ooops. You're right. It's 5500 TCP. :D

> **mapes12 said:**
>  Also, do you have an easy guide to follow or a screen shot that could help please? Thank you. I was under the impression that the Gitso homepage had that? Did you check the page?

It's very easy. The one giving help should have configured port-forwarding so that connections on port 5500 TCP end up on the workstation that he will use. So you'd quickly adjust the NAT settings of your router/firewall. The other thing you need is either your Internet-routable public IP or a hostname. Dynamic DNS works too. You'd have to give this info to the one in need of help. Or do as I do: Use dynamic DNS and be reachable under a relatively easy-to-remember host name. That's all. Launch the application and choose "Give Support". The application will then sit idle and wait for the remote connection ...

The one in need for help just clicks on the icon and fills in the hostname of the one who will give help: "my-dear-son.dynamic-dns-provider.some-domain.net" ... That's all.

If all goes well you should all of a sudden have your dad's desktop inside a window on your desktop.

Another solution that was suggest to me is this:
[http://www.remobo.com](http://www.remobo.com)

Apparently this is a easy-to-use VPN software and they now have a Linux version too. Debian/Ubuntu package can be downloaded from here:
[http://s3.amazonaws.com/remobo_setup/remobo_0.20.1_i386.deb](http://s3.amazonaws.com/remobo_setup/remobo_0.20.1_i386.deb)

Tutorial for "Remobo" can be found here:
[http://www.remobo.com/howto.php](http://www.remobo.com/howto.php)

Haven't tried that yet .... but it sure looks easy too. The nice thing here is that other users and their machines seem to be reachable/resolvable via their Remobo username ... so you don't have to bother about IP addresses at all.

Another interesting way I found is Dropbox ... Yes, Dropbox is used to sync files between computers. But if you know how you can also use it as SSH replacement :D
[http://wiki.getdropbox.com/TipsAndTricks/RemoteControl](http://wiki.getdropbox.com/TipsAndTricks/RemoteControl)

And this works pretty well. I am using this to remote control my company laptop which is currently located behind three firewall layers inside a lab I have to configure. Normal VPN or SSH won't work. But Dropbox does, reverse SSH and reverse VNC work tip top too. So now I can go to my customers (who usually have very restrictive network rules ...) and still remotely control the lab I am supposed to setup.

Oh well ... I guess this just proves that Linux can do pretty much anything :D

---

### Post by scorp123 on 2009-08-08
Ooops. I just found another one:
[http://www.yuuguu.com](http://www.yuuguu.com)

"Yuuguu offers cross network instant messaging, instant screen sharing,
real time collaboration, web conferencing and remote support.  Works on Windows, Mac OS and Linux based computers. Now works with Skype! learn more... "

[http://www.yuuguu.com/features/remote-support](http://www.yuuguu.com/features/remote-support)

"... Yuuguu remote support works across all platforms (Windows PC, Mac OS and Linux) and automatically deals with firewalls and proxies. In most cases Yuuguu remote support will simply work out of the box. ..."

Hmmm.... That sounds promising :D

I guess I will have to try that too :D

---

### Post by mapes12 on 2009-08-09
Firstly, thank you very much to everyone that has taken the time to respond to my thread.

I have looked at all of your very helpful suggestions. 

GITSO - My understanding is that port forwarding will make a small hole in my firewall. I use this router to connect to my work corporate WAN via VPN and whilst an open port on 5500 may be safe I don't think that I should risk it. Therefore, I'm going to leave Gitso on the back burner for the time being.

REMOBO - Had a good look round the site and decided to install it. Unfortunately, GDebi Package Installer had a problem with some dependency packages and fell over :( I've reported the details of my problem to the Remobo guys so that they can fix any bugs.

YUUGUU - This appears to work on the same principles as Remobo but a more established service. Therefore, I decided to Install the deb pacakge. All has gone well and I've set up my account and sent an invite for my Dad to do the same. Just waiting for him to respond then we can check it out. I'll post back and let you guys know if Yuuguu cuts the mustard later on.

Very many thanks again.

Mark

---

### Post by scorp123 on 2009-08-09
> **mapes12 said:**
>  GITSO - My understanding is that port forwarding will make a small hole in my firewall.  Correct.

> **mapes12 said:**
>  I use this router to connect to my work corporate WAN via VPN and whilst an open port on 5500 may be safe I don't think that I should risk it.  For as long as you are not running Gitso in the "Give Support" mode (or any other VNC daemon that would do the same and wait for a remote reverse connection ...) then there will be _nothing_ (no program, no process, no daemon) that would be accepting connections on that port. So this hole is irrelevant ... there is nothing that would allow anyone to connect to anything. Even if: What could a wannabe attacker do? Send you their desktop and try and shock you into inconsciousness with the ugly wallpaper they have configured ... ? :)

So the risk if any is really really small, IMHO.


> **mapes12 said:**
>  Therefore, I'm going to leave Gitso on the back burner for the time being.  I am back to Gitso. Yuuguu is nice, but there is a catch: You use Yuuguu's infrastructure as intermediary transit point. They claim that the traffic is safe ... but their program seems to be closed source + commercial, so it's kinda hard to tell as nobody will be able to inspect their program. No peer review. I am a bit paranoid about such things. "Security by obscurity" is proven not to be a good idea.

Gitso uses a well-known protocol such as VNC, it's open source, and it connects the machine of the one in need of support directly with the one giving support, with no intermediary servers in between. I definitely prefer that.

Remobo seems highly useful in a "there are too many firewalls between us" scenario. What if the one in need for help is behind a restrictive firewall and the one willing to give help too (e.g. at work behind your company's firewall)? Then Gitso would fail, because you probably won't be able to configure the port-forwarding. Enter Remobo: with the Private VPN you'd get from Remobo you very likely could avoid any firewall troubles and connect to each other directly again (the advantages of a VPN).

So "Remobo" definitely is on my watchlist because it will be interesting to see how they progress. I used to be a "Hamachi" user but since the company got bought by "LogMeIn" they seem to have abandoned the Linux client ..... So "Remobo" is a welcome replacement. Let's see how they will do.

---

### Post by mapes12 on 2009-08-09
Hello Scorp123 and thanks again for your post.

I think I've misunderstood the Gitso open port 5500 issue. Let me get this straight. If I'm not running the Gitso application then my 5500 port cannot be hacked? Your point about the wallpaper made me laugh =D>

Yeh, Remobo looks very good. Have you managed to install their deb package on your machine? As I posted earlier I had dependency issues. I've attached the screen shot I sent to the Remobo team of the install problem I had.

---

### Post by scorp123 on 2009-08-09
> **mapes12 said:**
>  If I'm not running the Gitso application then my 5500 port cannot be hacked?  Well ... think about it. What *precisely* is "hacking"?? It's someone connecting over the network to a program that is waiting for connections; and it's "hacking" if the guy who is initiating the connection is trying to bend and abuse whatever protocol the program is "speaking" to his own ends, e.g. getting more access than he is supposed to have. 

BUT: What if there is no program? Nobody waiting to accept the connection? It's a dead end. The intruder has nothing he can connect to, even if the firewall allows the connection to go through ... there won't be a response because no program is waiting for a connection. Unless you launch Gitso and tell it to wait for a connection ...

IMHO you don't have to worry too much about that little firewall opening.

---

### Post by scorp123 on 2009-08-09
> **mapes12 said:**
>  I've attached the screen shot I sent to the Remobo team of the install problem I had. **DECnet**? Are you sure this is from Remobo? DECnet is a really old network protocol ... it's like a dinosaur. Thought to be extinct ages ago. It's been ages I have seen anyone mention DECnet ... Let alone install it :D

---

### Post by scorp123 on 2009-08-10
> **scorp123 said:**
> **DECnet**? Are you sure this is from Remobo? DECnet is a really old network protocol ... it's like a dinosaur. Thought to be extinct ages ago. It's been ages I have seen anyone mention DECnet ... Let alone install it :D Indeed. Remobo is using DECnet. I am shocked. ](*,)

DECnet changes an ethernet interface's MAC address (how sick is that??) and I really really fail to see why anyone should want to be using this dinosaur protocol ....

Under these aspects I can't really recommend Remobo. I'd recommend you purge it (sudo apt-get --purge remove remobo) from your system and please make sure all that DECnet junk is gone too (packages: dnet-common, libdnet).

My apologies for recommending this piece of junk without having checked it first. :(

---

### Post by mapes12 on 2009-08-10
> mark@test-ubuntu:~$ sudo apt-get --purge remove remobo
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package remobo
mark@test-ubuntu:~$ sudo apt-get --purge remove dnet-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dnet-common is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@test-ubuntu:~$ sudo apt-get --purge remove libdnet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdnet is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@test-ubuntu:~$ 
I guess I'm rid of it? The GDeb Package Installer had a go at installing then just gave up very quickly, churning out the screen shot I posted.

My system seems OK. This is just my test machine so it doesn't matter if it falls over. I test stuff on here to make sure nothing breaks before I deploy on my main Ubu Desktop and Laptop.

Thanks again scorp123!

---

### Post by scorp123 on 2009-08-10
> **mapes12 said:**
> I guess I'm rid of it? 

Look at this!! :shock:
[http://www.remobo.com/community/viewtopic.php?f=4&t=278](http://www.remobo.com/community/viewtopic.php?f=4&t=278)

... the last posting in that thread.

In other words: Nope, Remobo doesn't even use or need DECnet. This is a totally stupid bug on their behalf ](*,) ... I mean seriously. Having DECnet as a dependency which causes serious troubles with TCP/IP, DHCP and what not (because DECnet will change the MAC addresses!) in a product that actually relies on TCP/IP ... oh well. It's almost funny #-o

Let's give it some more time ... maybe in a few releases it will usable :D

---

### Post by mapes12 on 2009-08-10
> **scorp123 said:**
> Look at this!! :shock:
[http://www.remobo.com/community/viewtopic.php?f=4&t=278](http://www.remobo.com/community/viewtopic.php?f=4&t=278)

... the last posting in that thread.

In other words: Nope, Remobo doesn't even use or need DECnet. This is a totally stupid bug on their behalf ](*,) ... I mean seriously. Having DECnet as a dependency which causes serious troubles with TCP/IP, DHCP and what not (because DECnet will change the MAC addresses!) in a product that actually relies on TCP/IP ... oh well. It's almost funny #-o

Let's give it some more time ... maybe in a few releases it will usable :DOh boy! I don't mind this error knocking out this machine (which it doesn't appear to have affected) but if it interfers with my router than that is serious! I have a partition image before all this. Should I install it?

---

### Post by scorp123 on 2009-08-11
> **mapes12 said:**
>  if it interfers with my router than that is serious! You installed DECnet on your router too?

---

### Post by LarsW_Tierp on 2009-08-11
FreeNX has helped me alot.

---

### Post by theozzlives on 2009-08-11
> **mapes12 said:**
> Thank you!

From what I've read this solution only works _easy_ over a LAN or intranet WAN. Apparently, it requires configuration of this VNC stuff to work over the internet and the VNC guides I've read are too complicated for me and my Dad. He's 75 by the way.

I really appreciate you Guys coming back to me. Thanks.

Just to try it out I setup my cell to work as a CDMA Broadband modem and logged onto my server with Remote Desktop without VNC. Just make sure port forwarding is setup in your router (if more than one computer is involved). Then you just need the IP.

---

### Post by little_penguin on 2009-09-16
Yugma is another easy, free option to try, available for Windows, Mac and Linux. No need to worry about port forwarding on firewalls etc.
 
[www.yugma.com]("http://www.yugma.com")
 
Regards,
LP

---

### Post by msriram on 2009-09-30
I'm trying to use Gitso to access Ubuntu machine from Windows XP. I got it installed, but its not working fine...

From windows machine: i gave some random ip address 101:32:89:92 and chose Give Support, and pressed Start

Then, 
From ubuntu Machine: i gave the same ip address and chose Get Help and pressed Start.
Nothing happens on ubuntu machine

on windows machine, I got a error saying " failed to connect "

Any Help??

---

### Post by Paddy Landau on 2009-09-30
> **msriram said:**
> From windows machine: i gave some random ip address 101:32:89:92 and chose Give Support, and pressed Start
I haven't used Gitso, but reading the instructions, you don't want a random address -- that will try to connect to whatever random computer happens to be at that address!

You need to use the correct IP address. If the computer is behind a router, you will need to forward the correct ports, and if it's behind a firewall, you may need to open those ports. (The instructions should tell you which ports.)

The problem with VNC (which Gitso uses) and most other solutions that I've looked at is that they need port forwarding and knowledge of the IP address. [LogMeIn]("http://logmein.com/") doesn't need this, and works brilliantly, but sadly it doesn't support Linux as a server.

From what I can see, [Yugma]("https://www.yugma.com/") (see [post #28]("http://ubuntuforums.org/showthread.php?p=7959340#post7959340")), which I've not (yet) tried, does get over that problem.

---

### Post by msriram on 2009-10-01
I checked out logmein.com and I am feeling bad that they dont supoport linux.

I use teamviewer to connect to windows.. So I decided to boot windows before I leave work, and connect to that from home.

Gitso, which simply uses tightvnc, just connects to Remote Desktop of Ubuntu (which I feel is slower than TeamViewer) that will help me connect only to a system in the local network. :(

1. I tried to open the port (in windows firewall - added port 5900)
2. connected to my wan id (googled it , and got it) using GITSO (or i'd say tightvnc)

Still nothing happens...

---

### Post by Paddy Landau on 2009-10-02
> **msriram said:**
> I checked out logmein.com and I am feeling bad that they dont supoport linux... I decided to boot windows before I leave work, and connect to that from home.
If you use Windows at work, then [LogMeIn]("http://logmein.com/") will work. It doesn't support Linux as a server, but it does support it as a client. I connect to my father's Windows machine from my Linux machine using LogMeIn, and it works great -- even though he is 6,000 miles from me and has a low speed Internet connection.

---

### Post by lasleym on 2009-10-02
> **scorp123 said:**
> I use **Gitso** .... It's very easy: All he needs to do is to click on an icon ... And poooof! you get to see his desktop. The steps to get this configured are relatively easy on his side. The complicated stuff (finding your public IP, configuring port forwarding so port 5000 TCP can get through to your LAN, etc.) is all on _your_ side ... which is OK.

I use Gitso to support my wife's parents (they're 70+ years old!) who live some 1200 km away from us. I created a pre-configured icon for them (very easy to do once you are connected to the desktop ...) so they now just need to click on it and I instantly get to see their desktop. Very easy to use. So what Gitso does in principle is a so called "Reverse VNC Connection". Whatever. It just works.

Gitso Homepage:
[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

This sounds great.  I know even less than the original poster, and I am looking for a way to convince my mom to use ubuntu, and she lives 2500 miles away.  So, what I don't understand is how you configure Port 5500?  Any suggestions?

---

### Post by Paddy Landau on 2009-10-02
> **lasleym said:**
>  what I don't understand is how you configure Port 5500?
This is done on the router. It's quite technical. If you are supporting someone 2,500 miles away, then you will need something that doesn't require fiddling with routers.

There does seem to be a serious lack of easy-to-set-up-and-use remote help programs for Linux. Windows and Mac have several, including the built-in Remote Assistance on Windows, and [LogMeIn]("http://logmein.com/") for Windows and Mac (accessible from Linux).

I would look at [Yugma]("https://www.yugma.com/"), as it supports Linux; unfortunately, I can't get it to work on my machine, and Yugma's support (for me) has been non-existent, so it's not a recommendation.

I hope that someone else can recommend something even half as good as LogMeIn, but for Linux.

---

### Post by lasleym on 2009-10-02
> **Paddy Landau said:**
> This is done on the router. It's quite technical. If you are supporting someone 2,500 miles away, then you will need something that doesn't require fiddling with routers.

...

I hope that someone else can recommend something even half as good as LogMeIn, but for Linux.

Thanks for the reply.  I was able to find this site:  [http://www.portforward.com](http://www.portforward.com), which reminded me that I **have** a router! :)  It gave instructions, which were dated for my Qwest router, but it set me in the right direction.  There are two places, I saw, for port forwarding - a simple option, and a place to adjust the application rules.

I have a cousin who lives equally as far a way who's willing to test it.  But, now Gitso is not installing properly.  Bummer.

---

### Post by mapes12 on 2009-10-03
I got this to work:

[https://launchpad.net/remote-help-assistant](https://launchpad.net/remote-help-assistant)

and setup the port forwarding via the How To once I registered a free Dynamic DNS address here:

[http://www.dyndns.com/](http://www.dyndns.com/)

---

### Post by starcannon on 2009-10-03
For the default Remote Desktop utility that ships with Ubuntu, you will need for the recipient, to open a port, and to allow another user to control the computer.

He(your Dad) should enable "Remote Desktop":
System>Preferences>Remote Desktop
Tick "Allow other users to view your desktop"; then:
Tick "Allow other users to control your desktop"; then:
Untick "Ask for confirmation"; then:
Tick "Require the user to enter this password"; then:
Create a password of 6 characters in length that He can share with You.

He should then log into his router/firewall and forward port 5900 to his LAN address.
He should then go to [http://www.whatismyip.com/](http://www.whatismyip.com/) and give you his WAN(internet) address.

You will then open up the Remote Desktop Viewer application:
Applications>Internet>Remote Desktop Viewer and click "Connect", put his WAN I.P. in the "Host" text field and then click Connect, enter the Password he set for this purpose.

Your in, enjoy helping him out.

GL and HF

---

### Post by Aq32 on 2009-11-30
> **scorp123 said:**
> Look at this!! :shock:
[http://www.remobo.com/community/viewtopic.php?f=4&t=278](http://www.remobo.com/community/viewtopic.php?f=4&t=278)

... the last posting in that thread.

In other words: Nope, Remobo doesn't even use or need DECnet. This is a totally stupid bug on their behalf ](*,) ... I mean seriously. Having DECnet as a dependency which causes serious troubles with TCP/IP, DHCP and what not (because DECnet will change the MAC addresses!) in a product that actually relies on TCP/IP ... oh well. It's almost funny #-o

Let's give it some more time ... maybe in a few releases it will usable :D

Help! I installed Remobo and it has affected my wireless settings so that I can't connect at all. I am lucky enough though that internet by ethernet cable to my wireless router works. Can someone please help me fix my wireless?

---

