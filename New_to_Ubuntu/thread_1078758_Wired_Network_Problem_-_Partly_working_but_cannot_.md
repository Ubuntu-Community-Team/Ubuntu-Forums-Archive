---
title: "Wired Network Problem - Partly working but cannot connect to Internet"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Mia-Linux on 2009-02-23
Firstly, I would like to start with an apology - I am sure variants of my question have been asked on many occasions - I have searched this forum as much as I can and I can find no answer that will help me (unfortunately). I also searched the web, read the ubuntu help documentation, read the FAQ, experimented with different settings and hints of information from the help I did find (a lot of progress was made this way :D) but I am now quite stuck and I am not sure of what I should do, so I would really appreciate a little assistance.

I am a complete Linux newbie, I downloaded Intrepid Ibex on Friday and since then, I have tried everywhichway I can to make the internet work. The problem is as follows:

When I log in, a yellow speech bubble appears over the network connection indicator to tell me that I am connected to the wired network. I try to open FireFox and go to a website, nothing happens. I click on the network connection indicator and then click on the connection itself (called 'Auth eth0') which proceeds to start an animation and prompts another yellow bubble to tell me that the connection is established. I open FireFox again and go to a website, nothing happens.

The way I wish to connect is via the automatic DCHP settings.
While searching for help, I learnt how to use Terminal a little and managed to get more settings information from within the system.
gedit /etc/network/interfaces gives:
```
auto lo
iface lo inet loopback
```

gedit /etc/resolve.conf gives an empty file. I read that I should put my DNS there, but I am not sure if there is a particular format for this (i.e. do I just type the number in the file and save, or write DNS first?).

If I run ifdown 'Auto eth0' it gives:
```
ifdown: interface Auto eth0 not configured.
```

If I run ifup 'Auto eth0' it gives:
```
Ignoring unknown interface Auto eth0=Auto eth0
```

If I run ifconfig 'Auth eth0' it gives:
```
Auth eth0: error fetching interface information: Device not found.
```

If I run ifconfig eth0 it gives:
```
eth0      Link encap:Ethernet  HWaddr [COLOR="Orange"][I checked this number, it matches the one on the Auth eth0 connection information][/COLOR]
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe39:cc49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1320  Metric:1
          RX packets:988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:68717 (68.7 KB)  TX bytes:24206 (24.2 KB)
          Interrupt:219 
```

If I ping my router, it works. If I ping angelsharks.org, it works (albeit much slower).

I read somewhere that I should set the network.dns.disableIPv6 setting in FireFox from FALSE to TRUE which I have done to no avail.

As far as I can see, this is either a very simple or a very tough problem, but since my knowledge of Linux is so limited, I just don't know what to do next.

Has anyone experienced something similar? Is there something else I should have tried or done? Did I manage to massively screw some vital setting up?

Any and all help appreciated and sorry for the loooong post!

---

### Post by yeats on 2009-02-23
> Firstly, I would like to start with an apology - I am sure this question or variants have been asked on many occasions - I have searched this forum as much as I can and I can find no answer that will help me (unfortunately). I also searched the web, read the ubuntu help documentation, read the FAQ, experimented with different settings and hints of information from the help I did find (a lot of progress was made this way ) but I am now quite stuck and I am not sure of what I should do, so I would really appreciate a little assistance.

It's okay to post about something that's been covered before, though it's great that you put the effort in to find things for yourself.  It's the people who don't try who don't get a lot wholehearted help. :-)

> I am a complete Linux newbie, I downloaded Intrepid Ibex on Friday

Awesome.  Welcome!

```
eth0      Link encap:Ethernet  HWaddr [I checked this number, it matches the one on the connection]
          **inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0**
          inet6 addr: fe80::223:54ff:fe39:cc49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1320  Metric:1
          RX packets:988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:68717 (68.7 KB)  TX bytes:24206 (24.2 KB)
          Interrupt:219
```

You have an IP address, so you are connected to the internet.  Since ping also works we know that the connection is established and that DNS works (since you pinged by domain name).

> If I run ifdown 'Auto eth0' it gives:

```
ifdown: interface Auto eth0 not configured.

```


The interface is named "eth0" - the "auto" in /etc/network/interfaces just tells the system to automatically set up the interface. You would also need to run this command prefaced by "sudo" to run as root.  However - you don't need to.  The interface is up and a connection to the network and Internet are working.

What is literally happening when you open a page in Firefox (meaning, what is the error message you're getting)?

---

### Post by Mia-Linux on 2009-02-23
Wow - that was a super fast reply - thank you so much Chris! I had a weak moment on Sunday when I thought to myself 'I could always try to work that "M" word product again but I remain determined :D.

I was not sure about the connection name 'Auth eth0' or 'eth0' but thank you for clearing that up - I ran the following commands on the Terminal too, if they help.

```
mia@mia-desktop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
mia@mia-desktop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
```

The FireFox window does absolutely nothing. I think I did notice that with the ipv6 setting on FALSE, it was giving me an error page (This page could not be found, please check your connection, etc), but with it set to TRUE I noticed that a loading bar in the bottom right corner of the FireFox window looks like it is loading (it has only gone to 50% and no further though).

Edit: I have been using sudo all along (many of the things I asked for would not open without it) - I was just typing without it to cut down on unnecessary text >_>.

I don't have any kind of Firewall installed so I guess that isn't blocking it either...Just seems like a very odd problem to me :-/.

---

### Post by sandyd on 2009-02-23
look here?

[https://www.opendns.com/start](https://www.opendns.com/start)

just maybe that will help

---

### Post by yeats on 2009-02-23
> Wow - that was a super fast reply - thank you so much Chris! I had a weak moment on Sunday when I thought to myself 'I could always try to work that "M" word product again but I remain determined .

Determination and curiosity are key to learning Linux.  Sounds like you've got both.

> 
I don't have any kind of Firewall installed so I guess that isn't blocking it either...Just seems like a very odd problem to me :-/.

It looks like you're connecting to a router of some kind (seeing the 192.168.1.* IP).  Could the problem be there?  Try typing your router's  IP in your browser window to see if you can connect to the admin interface.

---

### Post by Mia-Linux on 2009-02-23
> **carlee said:**
> look here?

[https://www.opendns.com/start](https://www.opendns.com/start)

just maybe that will help

I had a quick read through their privacy policy and some things in there seem quite intrusive...

```
Information We Collect
DNS Services Customers

OpenDNS runs a Domain Name System (DNS) service. DNS translates the name (e.g., www.example.com) you type into the corresponding numerical address (e.g., 192.0.34.166) and gets you to the place you want to go. OpenDNS's DNS service collects non-personally-identifying information such as the date and time of each DNS request and the domain name requested.

In addition, OpenDNS also collects potentially personally-identifying information like the Internet Protocol (IP) addresses from which DNS requests are made. For its DNS services, OpenDNS temporarily stores logs to monitor and improve our quality of service, and to collect high-level aggregate statistics. For customers without an account, OpenDNS removes the IP address from its logs within 2 business days. For customers with an account, such data may be stored for as long as the account is open (although, customers with an account may also choose to have DNS data purged automatically, at any time, from within their account).

For customers using OpenDNS "Shortcuts" feature, DNS requests for certain domains may be directed through an HTTP proxy. The data from the HTTP proxy is kept for approximately 12 hours for technical reasons. Encrypted connections are never proxied.

OpenDNS may aggregate personally-identifying information about the behavior of visitors to its websites and customers of its DNS services. For example, OpenDNS may monitor which domains are most requested by its customers, or how many phishing attempts were blocked by its services. OpenDNS may displays this information publicly or provide it to others in a non-personally identifiable aggregated form (e.g. statistical form).
```

Do I definitely need to do something like this? It really seems like something I'd like to get away from, if I can...

> **chrissharp123 said:**
> 
It looks like you're connecting to a router of some kind (seeing the 192.168.1.* IP).  Could the problem be there?  Try typing your router's  IP in your browser window to see if you can connect to the admin interface.

How did I forget to mention that! Yes I am connecting to a cable modem through a router. I set this router up and it works on all the computers (excluding this one). I can also see the other computers on the network in Ubuntu.

I have been on the router admin page before, so can fumble my way around almost effectively these days. It seems quite odd that I was able to access the router's admin page yesterday but not today. I will reboot everything in the right order (just in case some powercut got them confused) and will edit this post asap.

Edit: The power plugs for the router and modem were so hot, they hurt my hand. I decided to leave them to cool (in the innocent hope that this was the issue, logically I knew this was not true though). I have now re-plugged everything in and my linux PC is still giving me the same cold shoulder, although my other two PCs have no problems in connecting.

It is 1am where I am, so sleep is imminent - I will try searching for more information on google tomorrow, but I would really appreciate some advice from someone who may know what it is that I have done to mess this up >_<.

Many thanks for the help to date : ).

---

### Post by Mia-Linux on 2009-02-24
Okeydoke, I had a few minutes so I searched the internet some more, and found some possible solutions (none of which have worked).

[https://lists.ubuntu.com/archives/ubuntu-users/2007-May/113467.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-May/113467.html)
No effect.

[http://propellerheadadmin.com/tutorials/ubuntu/6-wired-networking-problem-on-a-fresh-ubuntu-810-install](http://propellerheadadmin.com/tutorials/ubuntu/6-wired-networking-problem-on-a-fresh-ubuntu-810-install)
I tried $sudo /etc/init.d/networking restart but I was just told that the networks were being reconfigured, nothing like the message that this guy posted.

The standing problem I have is that the system can see the network, it can see the computers on the network but just nto connect to the internet. If anyone could help, I would really appreciate it - I am nt quite sure of what I should try now...

---

### Post by yeats on 2009-02-24
> **Mia-Linux said:**
> The standing problem I have is that the system can see the network, it can see the computers on the network but just nto connect to the internet. If anyone could help, I would really appreciate it - I am nt quite sure of what I should try now...

Go ahead and do this a terminal and post the output:

```
ping google.com
```

(Ctrl-C to stop)

If ping works, you know you're on the Internet (and that DNS works) and that the problem has to do with Firefox somehow.

---

### Post by ikisham on 2009-02-24
Now, please anybody don't say rude things if what I say is nonsense...
I was just thinking that as it was a new install it couldn't be the system's fault. Here where I live I have to configure pppoe to authenticate the session but since you have the router configured that must not be your case. Where do you live? Maybe it has something to do with your IP and you could ask someone that uses ubuntu in your area.

---

### Post by Mia-Linux on 2009-02-24
Hey Chris - thank you for writing back :). I think my problem may have been slightly more elementary than what I've been thinking about all along - just ran an MD5 check and the number doesn't match [this one]("https://help.ubuntu.com/community/UbuntuHashes").

I also think I got confused downloading - I kept reading about amd64 and i386 and by about 1am that Friday (I had just finished building the PC so I was tired and impatient) I gave up trying to work out which is the right version and installed i386 - with a 64 bit computer though, I should be installing amd64 version so I am downloading it now *sigh*.

I decided to reinstall again, this time ignoring dirty OS that begins with W and just going to Linux boot - the hard drive is almost zeroed out and I will start afresh.

In the mean time, I can only hope the hash file matches, since I run out of options after that (save for buying a Linux copy somewhere ^^).

Thank you so much for your patience - I will persevere and will get this system working one way or the other :D.

Just saw other post:

> **ikisham said:**
> Now, please anybody don't say rude things if what I say is nonsense...
I was just thinking that as it was a new install it couldn't be the system's fault. Here where I live I have to configure pppoe to authenticate the session but since you have the router configured that must not be your case. Where do you live? Maybe it has something to do with your IP and you could ask someone that uses ubuntu in your area.


It is indeed a new install, but my old PC was working just fine with that connection and router set up and so do my two other PCs... Thank you for the suggestion though, if I only had one PC that would certainly be an avenue worth exploring! :D

---

