---
title: "Ubuntu machine as a proxy"
date: 2005-06-12
forum: Networking &amp; Wireless
---

### Post by Dave_is_sexy on 2005-06-12
Does anyone know how I can simply allow my flatmate to get on the net through my machine as a proxy. I have heard of IP tables but don't know what they are, and am on linux day 2.. so no assumptions that i know things yet please ^_^

I was using free proxy on windows. Simply to say allow ip 192.168.0.2 net access for http, ftp and socks on ports 8080, 21 and 1080

Can I get a front end for this or easily add it to a text file?
Thanks
Dave

---

### Post by desdinova on 2005-06-12
[QUOTE=Dave_is_sexy]Does anyone know how I can simply allow my flatmate to get on the net through my machine as a proxy. I have heard of IP tables but don't know what they are, and am on linux day 2.. so no assumptions that i know things yet please ^_^

I was using free proxy on windows. Simply to say allow ip 192.168.0.2 net access for http, ftp and socks on ports 8080, 21 and 1080

Can I get a front end for this or easily add it to a text file?
Thanks
Dave[/QUOTE]
 What you want is called IP masquerading - if you install the Shorewall firewall it can set up masquerading too - that way you don't use a proxy, but automagically both machines can see the net

---

### Post by desdinova on 2005-06-12
[http://ubuntuforums.org/showthread.php?t=15703](http://ubuntuforums.org/showthread.php?t=15703)

has more info

---

### Post by Dave_is_sexy on 2005-06-13
I've installed shorewall by apt-get and shorewoll-doc, but.. well they're not graphical which is a pain since i'm in a foreign environment and have to do this pronto (only minutes available at a time cos i can't cut his net connection)

Having looked at the software i'm not convinced things are going to work. The second machine has everything set up to go through a proxy at the server address. That config can't change. So am i right in thinking I need some proxy software which shorewall is not? or can shorewall act as a proxy? 

Port forwarding, though better, is not ok in this case, unless his machine wont know the difference?

If I am using shorewall for this ould someone please give me a hand in setting up this simple task. I can't learn it for myself, because he wont let the net be down on his for that long :(

---

### Post by desdinova on 2005-06-13
[QUOTE=Dave_is_sexy]I've installed shorewall by apt-get and shorewoll-doc, but.. well they're not graphical which is a pain since i'm in a foreign environment and have to do this pronto (only minutes available at a time cos i can't cut his net connection)

Having looked at the software i'm not convinced things are going to work. The second machine has everything set up to go through a proxy at the server address. That config can't change. So am i right in thinking I need some proxy software which shorewall is not? or can shorewall act as a proxy? 

Port forwarding, though better, is not ok in this case, unless his machine wont know the difference?

If I am using shorewall for this ould someone please give me a hand in setting up this simple task. I can't learn it for myself, because he wont let the net be down on his for that long :([/QUOTE]
 You would be a lot better learning it for yourself - it makes it easier to fix a problem - for a proxy look at privoxy.

Why can't the second machine change? That makes things very awkward

---

### Post by Dave_is_sexy on 2005-06-13
The reason I can't learn this myself right now, is cos I'm not allowed to boot linux cos my flatmate is cut off the net if i do. Therefore I have to have us both on the net before I can begin to learn anything. Which means that I have to have a proxy in place. It's not awkward at all because I know the proxy his machine is trying to get to, and on which ports. All I want is a damn proxy with a gui, that i can say  "this.this.this. go"

Something like freeproxy. I know it's not the best way, but it's my only option at the mo. Once it's done I'll be able to set up some propper IP tables

---

### Post by desdinova on 2005-06-13
[QUOTE=Dave_is_sexy]The reason I can't learn this myself right now, is cos I'm not allowed to boot linux cos my flatmate is cut off the net if i do. Therefore I have to have us both on the net before I can begin to learn anything. Which means that I have to have a proxy in place. It's not awkward at all because I know the proxy his machine is trying to get to, and on which ports. All I want is a damn proxy with a gui, that i can say  "this.this.this. go"

Something like freeproxy. I know it's not the best way, but it's my only option at the mo. Once it's done I'll be able to set up some propper IP tables[/QUOTE]
 The best proxy is squid - if you want to gui admin it - I'd advise webmin.

---

### Post by Dave_is_sexy on 2005-06-13
I just found squid, but it doesn't upport Socks proxying! Found Delegate which does but it's a tarball. Searching "how to install a tarball" doesn't have any info, cos if you search anything to do with linux you're just greated with a hundred results of people's problems that were never solved

---

### Post by desdinova on 2005-06-13
[QUOTE=Dave_is_sexy]I just found squid, but it doesn't upport Socks proxying! Found Delegate which does but it's a tarball. Searching "how to install a tarball" doesn't have any info, cos if you search anything to do with linux you're just greated with a hundred results of people's problems that were never solved[/QUOTE]
 unzip the tarball

./configure --prefix=/usr
make
sudo make install

CAution : This isn't a flame, so please don't take it as such.

You're not making it easier for yourself with comments such as "can't learn this myself right now, is cos I'm not allowed to boot linux cos my flatmate is cut off the net if i do" because you're forcing yourself to learn on the fly. Setting up a proxy in linux is very easy, but it takes a little work - server software tends not to come with gui's as its all too easy to come up with insecure install's in my opinion with a pick & mix config system.

To get it done right, it may be worthwhile saying to your flatmate - look, the net's gonna be off for an hour or two whilst I get this done right. With the proper install, they can browse the net without the need for socks proxies and use the full range of facilites.

Its the same as learning a language - things are done differently in Linux, and a little time and patience will reap dividends. Just tell them it will be down for a little while, install shorewall - follow the instructions in /usr/share/doc/shorewall for setting up a ip forwarding firewall (you untar the two interfaces config from [www.shorewall.org](www.shorewall.org) into /etc/shorewall and edit the files (which come with full instructions inside them) as you need).

You then reboot, the firewall will start automatically and if you've said yes to ip_forwarding in the file you'll have full transparent internet access

---

### Post by desdinova on 2005-06-13
[http://www.shorewall.net/two-interface.htm](http://www.shorewall.net/two-interface.htm)

"
**Introduction**

 Setting up a Linux system as a firewall for a small network is a     fairly straight-forward task if you understand the basics and follow the     documentation.

 This guide doesn't attempt to acquaint you with all of the features     of Shorewall. It rather focuses on what is required to configure Shorewall     in its most common configuration:

 
[list]
[*]Linux system used as a firewall/router for a small local         network.

[*]**Single public IP address.** If         you have more than one public IP address, this is not the guide you         want -- see the [Shorewall Setup         Guide]("http://www.shorewall.net/shorewall_setup_guide.htm") instead.

[*]Internet connection through cable modem, DSL, ISDN, Frame Relay,         dial-up ...

[/list]
 Here is a schematic of a typical installation:"

---

### Post by Dave_is_sexy on 2005-06-13
Cheers for the tarbaal advice. Although i'm not too sure about the:

--prefix=/usr

bit (totally new remember, and this is hard)

so, for example

./configure --delegate.tar.gz=/dave? or root?

 No lectures on not logging in as root please. I am logged in as root cos it wont let me do anything as me. So i'm learning and setting up on root. I don't care if it screws up cos once i've got the hang of things, it's getting wiped and put on afresh will all that i've learned.

Why does it care what user i am? doesn't it know that?

I'm still not convinced that Shorewall will be seen by his XP as a proxy. CAn you confirm that it will? I tried webmin, but there was no actual way to start the GUI once it was installed. So it went straight away. Firestarter is far more my level at the moment, but it wasn't recognised as a proxy by his machine cos it was doing internet connection sharing instead. See the problem? Has to be a proxy. Doesn't have to be any good. Just something so i can get on with learning other stuff, because we both have net.

---

### Post by desdinova on 2005-06-13
[QUOTE=Dave_is_sexy]Cheers for the tarbaal advice. Although i'm not too sure about the:

--prefix=/usr

bit (totally new remember, and this is hard)

so, for example

./configure --delegate.tar.gz=/dave? or root?

 No lectures on not logging in as root please. I am logged in as root cos it wont let me do anything as me. So i'm learning and setting up on root. I don't care if it screws up cos once i've got the hang of things, it's getting wiped and put on afresh will all that i've learned.

Why does it care what user i am? doesn't it know that?

I'm still not convinced that Shorewall will be seen by his XP as a proxy. CAn you confirm that it will? I tried webmin, but there was no actual way to start the GUI once it was installed. So it went straight away. Firestarter is far more my level at the moment, but it wasn't recognised as a proxy by his machine cos it was doing internet connection sharing instead. See the problem? Has to be a proxy. Doesn't have to be any good. Just something so i can get on with learning other stuff, because we both have net.[/QUOTE]
 Why does it have to be a proxy - I say why, cause with shorewall set up with ip forwarding and masquerading - you get transparent net access....?

it will be 

./configure  --prefix=/usr

Rather then log in as root, use sudo - its more secure honest. Good practice and all that.

Honestly, ip forwarding is WAY better then socks proxying - its transparent - your flatmate can then strip out all mention of proxy and browse the net as if it was his /herown

---

### Post by Dave_is_sexy on 2005-06-13
Yeah i know it's better, but his machine is set up for proxying. It's really not something I have control over. I'm simply moving to linux, his machine is remaining untouched. Please stop trying to convince me that proxying isn't very good, i'm fully aware of that

Plus you haven't seen our router config. I don't think that connection sharing would be a simple in this case as it would be normally. 

I'd just like some help in installing a GUI proxy with http, ftp and socks. very very very simple. doesn't involve changing his machine. doesn't involve re-wiring the house. is'n t a good method, but it doesn't matter. So far this OS is a complete nightmare, and everyone online and offline is making it harder. 

How hard can it be to put a proxy on with a gui? that supports some half-decent protocols? Socks is needed for DC++ btw

---

### Post by desdinova on 2005-06-13
As you yourself said, its day 2 with Linux - so don't expect instant enlightenment.....

Most server software doesn't come with a gui, though [http://www.secinf.net/firewalls_and_VPN/Firewalling_and_Proxy_Server_HOWTO/Firewalling_and_Proxy_Server_HOWTO__The_SOCKS_Proxy_Server.html](http://www.secinf.net/firewalls_and_VPN/Firewalling_and_Proxy_Server_HOWTO/Firewalling_and_Proxy_Server_HOWTO__The_SOCKS_Proxy_Server.html) seems reasonably clear. GUI configuring a server is a recipe for disaster. When I did sysadmin, I used to hate configuring say Exchange as opposed to something like Courier-Imap. GUI's really do lock you down a lot.

Socks is pretty much not used much anymore, and in all fairness I think you'd probably be best off going back to the old way you were doing it. You've set yourself some pretty stiff restraints...

And re: the router config, Linux probably can handle it. Most of the traffic you use on the net is Linux - Google is all Linux.

I can't find any gui'ed socks server on Google, as its not used much anymore these days except to act as a small proxy....

---

### Post by Dave_is_sexy on 2005-06-13
Well I have squid. Just love the enormous text document config file. Tell me, what's wrong with CSV? It's a text file, that's also a table for easy viewing and modification. 

Er, it does'nt do anything and all the gui's have start and stop buttons. Exclusively. How can they think that i couldn't start and stop it if i've managed to install it? Just wait for Dave-linux. It's gonna take over the world  :smile: 

I'd like to say screw it i'll do a shared connection but i can't. the same settings on the other machine must work whether i'm in win2k or linux and the shared net connection there is impossible cos of the wiring. so it's squid config i need to do. For now. til he tries to use msn or dc++ (i love how no-one in the whole amazing open source world bothered to write a socks4/5 proxy)

thinks... THIS ISN"T GOING TO WORK! Squid does not meet my needs. and i can't figure out that other damn tarball. why did no-one write tarball2deb or rpm.

---

### Post by desdinova on 2005-06-13
[QUOTE=Dave_is_sexy]Well I have squid. Just love the enormous text document config file. Tell me, what's wrong with CSV? It's a text file, that's also a table for easy viewing and modification. 

Er, it does'nt do anything and all the gui's have start and stop buttons. Exclusively. How can they think that i couldn't start and stop it if i've managed to install it? Just wait for Dave-linux. It's gonna take over the world :smile: 

I'd like to say screw it i'll do a shared connection but i can't. the same settings on the other machine must work whether i'm in win2k or linux and the shared net connection there is impossible cos of the wiring. so it's squid config i need to do. For now. til he tries to use msn or dc++ (i love how no-one in the whole amazing open source world bothered to write a socks4/5 proxy)

thinks... THIS ISN"T GOING TO WORK! Squid does not meet my needs. and i can't figure out that other damn tarball. why did no-one write tarball2deb or rpm.[/QUOTE]

An incredibly well labelled text file a la postfix and other servers. Part of your problem is you've sent yourself way too short a timescale. Learning something new cannot be done on the fly.

there is checkinstall which can create deb's from tarballs IIRC.. As I said, Socks proxies are pretty much not needed these days, they're a hangover...

---

