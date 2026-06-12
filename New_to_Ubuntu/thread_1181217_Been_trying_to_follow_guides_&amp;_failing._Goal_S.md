---
title: "Been trying to follow guides &amp; failing. Goal: Set up WordPress on 9.04 or 8.04 server"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by tehmoos on 2009-06-07
I just got an Ubuntu 8.04 server from my computer teacher for me to screw around with. I really want to set up a WordPress blog for a project I've already started on a blah.wordpress.com account. Preferably, I'd like to take away the ".wordpress.com" part, so I'm setting up this server.

_**My project will (hopefully) involve**_

[LIST]
[*]Displaying information (through text, pictures, and videos)
[*]Hosting a forum *
[*]Allowing people to download files from my server *
[*]Side-blog for personal use *
[/LIST]
* = Optional

Great security would be wonderful, as well. My project will involve a controversial subject. Others who have made sites relating to this subject have been attacked like crazy after they became popular.

I wanted a clean slate, so I cleared everything and installed Jaunty Jackalope (server version). I followed _[these instructions]("http://www.corey-m.com/blog/?p=291")_ and skimmed a bit over _[this guide]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2")_ (the former probably being a dumb idea since it was 9.04 instead of 8.04, but the installations seemed pretty much identical to each other. **I am willing to reinstall the OS or switch to 8.04 if it'll make things easier, since I really don't have anything on there now.** In fact, I'm thinking of redoing everything under the HowToForge guide, since it's actually 9.04.


_**Current problem(s)**_

[LIST]
[*]Server doesn't seem to connect to the internet. (Ex: When trying to use 'wget [http://wordpress.org/latest.tar.gz](http://wordpress.org/latest.tar.gz)' it responds by saying it could not retrieve the URL.)
[/LIST]
As of now, that's the biggest problem, but I'll update this when necessary. [SIZE=1][COLOR=White]I'm big into formatting posts and keeping them organized. heh.[/COLOR][/SIZE]

I really don't know anything about Linux. I tried using PCLinuxOS for a bit, but got really aggravated with it since it was my primary home computer. At the most, I know root = administrator, sudo has something to do with root powers, shell scripts seem to be similar to exe's, tar seems to be a compressed file, and nano & vi are text editors.

**Questions:**
**1.** Do I need to pay for anything in order to get this thing running? (Corey's blog makes it seem like I have to, but I've heard otherwise that I don't.)

**2.** Does [_this_]("http://images.howtoforge.com/images/perfect_server_ubuntu_9.04_ispconfig2/big/11.png") part of the installation affect my URL? Example: If I chose to put ubuntuserver, when I finally get the server up and running, would it display as
"http://ubuntuserver.domain.com"
"http://www.ubuntuserver.com"
OR would it not affect the URL?

**3.** On step 7 of [_this page of HowToForge's guide_]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2-p3"), it says he uses an example IP address and whatnot (which I'm guessing affects the network, broadcast, and gateway values). How can I find out what I should use for those values?

**4.** Also under step 7, it says it should look like (changed for Q2's example value)
localhost.localdomain        localhost
ubuntuserver.example.com       ubuntuserver

But for me, it looks like
localhost
ubuntuserver.WorkGroup



Soooo... I'm pretty sure I need to get these problems fixed up before I even try the rest of the guides. #-o

Edit: **Extra info**
**ISP:** Comcast (residential)
**Network:** Ethernet (through router)
**IP type:** Dynamic

---

### Post by cariboo on 2009-06-07
The first thing to do is to get your network connection working properly. Installing wordpress is in the repositories, so unless you really need the latest version, that is the easiest way to install and set it up.

During setup, how did you set up your network connection?

If you plan on going live with this setup, how do you connect to the internet, directly or through a router? Does your ISP allow you to run a web server? Do you have a static ip address?

---

### Post by sandyd on 2009-06-07
> **tehmoos said:**
> I just got an Ubuntu 8.04 server from my computer teacher for me to screw around with. I really want to set up a WordPress blog for a project I've already started on a blah.wordpress.com account. Preferably, I'd like to take away the ".wordpress.com" part, so I'm setting up this server.

_**My project will (hopefully) involve**_

[LIST]
[*]Displaying information (through text, pictures, and videos)
[*]Hosting a forum *
[*]Allowing people to download files from my server *
[*]Side-blog for personal use *
[/LIST]
* = Optional

Great security would be wonderful, as well. My project will involve a controversial subject. Others who have made sites relating to this subject have been attacked like crazy after they became popular.

I wanted a clean slate, so I cleared everything and installed Jaunty Jackalope (server version). I followed _[these instructions]("http://www.corey-m.com/blog/?p=291")_ and skimmed a bit over _[this guide]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2")_ (the former probably being a dumb idea since it was 9.04 instead of 8.04, but the installations seemed pretty much identical to each other. **I am willing to reinstall the OS or switch to 8.04 if it'll make things easier, since I really don't have anything on there now.** In fact, I'm thinking of redoing everything under the HowToForge guide, since it's actually 9.04.


_**Current problem(s)**_

[LIST]
[*]Server doesn't seem to connect to the internet. (Ex: When trying to use 'wget [http://wordpress.org/latest.tar.gz](http://wordpress.org/latest.tar.gz)' it responds by saying it could not retrieve the URL.)
[/LIST]
As of now, that's the biggest problem, but I'll update this when necessary. [SIZE=1][COLOR=White]I'm big into formatting posts and keeping them organized. heh.[/COLOR][/SIZE]

I really don't know anything about Linux. I tried using PCLinuxOS for a bit, but got really aggravated with it since it was my primary home computer. At the most, I know root = administrator, sudo has something to do with root powers, shell scripts seem to be similar to exe's, tar seems to be a compressed file, and nano & vi are text editors.

**Questions:**
**1.** Do I need to pay for anything in order to get this thing running? (Corey's blog makes it seem like I have to, but I've heard otherwise that I don't.)

**2.** Does [_this_]("http://images.howtoforge.com/images/perfect_server_ubuntu_9.04_ispconfig2/big/11.png") part of the installation affect my URL? Example: If I chose to put ubuntuserver, when I finally get the server up and running, would it display as
"http://ubuntuserver.domain.com"
"http://www.ubuntuserver.com"
OR would it not affect the URL?

**3.** On step 7 of [_this page of HowToForge's guide_]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2-p3"), it says he uses an example IP address and whatnot (which I'm guessing affects the network, broadcast, and gateway values). How can I find out what I should use for those values?

**4.** Also under step 7, it says it should look like (changed for Q2's example value)
localhost.localdomain        localhost
ubuntuserver.example.com       ubuntuserver

But for me, it looks like
localhost
ubuntuserver.WorkGroup



Soooo... I'm pretty sure I need to get these problems fixed up before I even try the rest of the guides. #-o

Some questions.
Whats your ISP?
what network are you using to connect to the internet? (ethernet, wireless...)
Did you do the DHCP configuration during the OS installation?


----
post the output of ifconfig
oh and fix your internet before you do the stuff below
-----------------
Setting up Webserver
```

sudo apt-get install apache2 php5 php5-cgi php5-cli php5-common php5-curl php5-ffmpeg php5-gd php5-imagick php5-imap php5-mcrypt php5-mhash php5-mysql php5-sqlite php5-suhosin

```
FYI. I also added the suhosin patch into the above commands because it improves security
Then 
```

wget http://prdownloads.sourceforge.net/webadmin/webmin_1.470_all.deb
sudo apt-get -f install

```
Setup control panel (optional)
```

sudo mkdir /etc/init.d-restricted
sudo mv /etc/init.d/webmin /etc/init.d-restricted
sudo /etc/init.d-restricted/webmin start

```
Then go to another computer and browse to http://<server ip address here >:10000

Login using root, and click on Servers -> Apache

For security purposes, each time you want to open the control panel, you mist do 
```

sudo /etc/init.d-restricted/webmin start

```
and 
```

sudo /etc/init.d-restricted/webmin stop

```
to stop it. 
It will not automatically start up at the computer boot time

you might also want to configure the firewall with iptables, but i unfortunately can't think of the steps oof the top of my head

---

### Post by sandyd on 2009-06-07
oops, i forgot this.. stupid me to leave you with no database server....

```

sudo apt-get isntall mysql-server

```

---

### Post by tehmoos on 2009-06-07
> **cariboo907 said:**
> The first thing to do is to get your network connection working properly. Installing wordpress is in the repositories, so unless you really need the latest version, that is the easiest way to install and set it up.
Wow, that's really useful. Thank you! I like using the latest version for everything, but it's good to know that it's there just in case. :)

> **cariboo907 said:**
>  During setup, how did you set up your network connection?
I don't know. There was something about a proxy, but I left that blank.

> **cariboo907 said:**
> If you plan on going live with this setup, how do you connect to the internet, directly or through a router? Does your ISP allow you to run a web server? Do you have a static ip address?

I connect through a router and my ISP is Comcast. I just talked with them online and they said that through residential accounts, it's not allowed because it's a dynamic IP address. FAIL. :(

Seeing as they're trying to get me to buy a business account and wouldn't let me in on this information if it's there... is there any way to get around this?



~~~~~~~~~~~
> **carlee said:**
> Some questions.
Whats your ISP?
what network are you using to connect to the internet? (ethernet, wireless...)
Did you do the DHCP configuration during the OS installation?


----
post the output of ifconfig
oh and fix your internet before you do the stuff below

ISP: Comcast
Network: Ethernet
I don't think I did anything relating to DHCP in the OS installation, but I know I changed it to static according to Corey's guide.

I don't know what ifconfig is. :(

---

### Post by sandyd on 2009-06-07
if its dynamic, you can still do hosting, you can use a service such as dyndns.org

you don't necessarily need a static ip to host a server, although its highly recommended
on the other hand, you can find a friend who has a static ip, and vpn their connection to your computer. Tnen comcast CANNOT complain..becuase they aren't gonna spend days decrypting your vpn connection just to check on your activities. 

at this point, however, i would just go out and pay a webhost. they deal with security issues every day and are more experienced with dealing with the number of tricks that are pulled on webservers every day. They also probably has DoS protected networks as DoS is a very popular way of attacking a server.

---

### Post by sandyd on 2009-06-07
> **tehmoos said:**
> Wow, that's really useful. Thank you! I like using the latest version for everything, but it's good to know that it's there just in case. :)


I don't know. There was something about a proxy, but I left that blank.



I connect through a router and my ISP is Comcast. I just talked with them online and they said that through residential accounts, it's not allowed because it's a dynamic IP address. FAIL. :(

Seeing as they're trying to get me to buy a business account and wouldn't let me in on this information if it's there... is there any way to get around this?



~~~~~~~~~~~


ISP: Comcast
Network: Ethernet
I don't think I did anything relating to DHCP in the OS installation, but I know I changed it to static according to Corey's guide.

I don't know what ifconfig is. :(

i meant run
```

ifconfig

```
in terminal

---

### Post by sandyd on 2009-06-07
> **tehmoos said:**
> Wow, that's really useful. Thank you! I like using the latest version for everything, but it's good to know that it's there just in case. :)


I don't know. There was something about a proxy, but I left that blank.



I connect through a router and my ISP is Comcast. I just talked with them online and they said that through residential accounts, it's not allowed because it's a dynamic IP address. FAIL. :(

Seeing as they're trying to get me to buy a business account and wouldn't let me in on this information if it's there... is there any way to get around this?



~~~~~~~~~~~


ISP: Comcast
Network: Ethernet
I don't think I did anything relating to DHCP in the OS installation, but I know I changed it to static according to Corey's guide.

I don't know what ifconfig is. :(

without looking, ill try to guess.

you set your static ip through the computer right?
if you set it through the computer, chances are some routers will refuse that configuration and not let you have internet.

Instead, you have to set your static ip through the **router**.

---

### Post by SathyaBhat on 2009-06-07
why not get a hosting package? Decent hosting is cheap, you don't have to worry about hassles of IP routing and what not - and in all probability - the homegrown server will not be capable of handling the holds - if I were you I'd get a decent (shared) hosting package, and once traffic drives up, move on to a VPS

---

### Post by tehmoos on 2009-06-07
> **carlee said:**
> if its dynamic, you can still do hosting, you can use a service such as dyndns.org

you don't necessarily need a static ip to host a server, although its highly recommended
on the other hand, you can find a friend who has a static ip, and vpn their connection to your computer. Tnen comcast CANNOT complain..becuase they aren't gonna spend days decrypting your vpn connection just to check on your activities. 

at this point, however, i would just go out and pay a webhost. they deal with security issues every day and are more experienced with dealing with the number of tricks that are pulled on webservers every day. They also probably has DoS protected networks as DoS is a very popular way of attacking a server.

I'm thinking now that paying a webhost might be for the best. Corey-m recommended Namecheap and the plans seem to fit my budget perfectly. Just searched for some reviews of NC and it seems it's a pretty good service, too.

I still want to get some experience with an Ubuntu server... Would I still be able to even while using something like Namecheap? I'd like to start off with something that'll give me some experience with Ubuntu servers and advance to working on my own when I feel comfortable enough.

---

### Post by sandyd on 2009-06-07
> **tehmoos said:**
> I'm thinking now that paying a webhost might be for the best. Corey-m recommended Namecheap and the plans seem to fit my budget perfectly. Just searched for some reviews of NC and it seems it's a pretty good service, too.

I still want to get some experience with an Ubuntu server... Would I still be able to even while using something like Namecheap? I'd like to start off with something that'll give me some experience with Ubuntu servers and advance to working on my own when I feel comfortable enough.

hmm... not sure if this would still be in your budget, but you can try uisng a VPS.

A vps is typically a virtual machine. 
 

please wait while i do some reasearch.

oh and btw, hosting? REad here : :D [http://www.netfirms.com/max](http://www.netfirms.com/max)

---

### Post by sandyd on 2009-06-07
heres a list of the cheapest ...

cheapvps.co.uk
vpslink.com
cleanvps.com 

however, i haven't tried ANY of them... becuase i use two servers that are in colo

---

### Post by tehmoos on 2009-06-07
Can you explain to me what VPS is? What are the pros and cons of using that instead of a regular webhost?

Edit: I've seen someone use VMWare before. Is VPS something like that?

---

### Post by sandyd on 2009-06-07
> **tehmoos said:**
> Can you explain to me what VPS is? What are the pros and cons of using that instead of a regular webhost?

A VPS is a virtual machine thats run on a server

Pros: exactly the same as running a home server.
      meaning, you can do everything to it just like your own     computer.

Cons: security might be a little crooked, might take some time to pull it back up when it goes down for some reason or another (because shared hosting sysadmins have more experience in this kind of stuff)

Costs a little more than shared hosting.

If you get a bad host, they might overload the servers (some hosts do this believe me) and that will cause your website (and server OS) to run slower. 
Because of that problem, there are now two types of VPS
OpenVZ VPS can be overloaded
Xen VPS cannot be overloaded because the resources are dedicated to each VPS

---

### Post by sandyd on 2009-06-07
> **tehmoos said:**
> 

Edit: I've seen someone use VMWare before. Is VPS something like that?
you got it!

its exactly like that, except that its not really a virtual machine, but a special kernel. but doesn't really matter, its the same concept

---

### Post by tehmoos on 2009-06-07
What if I were to use a regular webhost and PuTTY? What's the difference?

Sorry if I'm annoying you. ^^;; With my budget, I just really need to be 100% sure that what I do is what I want and that there's nothing better as of now.

---

### Post by sandyd on 2009-06-07
A regular webhost that allows putty (ssh connections i presume they mean) doesn't give you much control over anything. In fact, sometimes i wonder why that function is offered at all. The only difference is between  things you could do (im just using my brans here, forgive me if im wrong) would probably be able to chmod directories, create directories, backup, run some programs; 

i doubt they would let you touch the webserver config or install anything for fear of abuse.

---

