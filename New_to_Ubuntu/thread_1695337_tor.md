---
title: "tor"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2011-02-25
I'm having trouble installing tor.  Could someone please try to explain it to me?  I know this may sound weird, but yeah.

---

### Post by metalf8801 on 2011-02-25
> **TriBlox6432 said:**
> I'm having trouble installing tor.  Could someone please try to explain it to me?  I know this may sound weird, but yeah.

What have you tried to do and where are you getting stuck?

---

### Post by TriBlox6432 on 2011-02-25
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

I get stuck when adding the repos.  I exit out of Software Sources and it tells me to refresh, which I do, then is gives me errors that say it can't add the keys.

---

### Post by bananas4370 on 2011-02-25
Have a look at the instructions at [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Cheers
Patrick

---

### Post by metalf8801 on 2011-02-25
Have you tried these steps? 

Option one: Tor on Debian lenny, Debian sid, or Debian testing

If you're using Debian stable (lenny), unstable (sid), or testing (squeeze), just run
apt-get install tor tor-geoipdb as root.

Note that this might not always give you the latest stable Tor version, but you will receive important security fixes. To make sure that you're running the latest stable version of Tor, see option two below.

Now Tor is installed and running. Move on to step two of the "Tor on Linux/Unix" instructions.
Option two: Tor on Ubuntu or Debian

Do not use the packages in Ubuntu's universe. They are unmaintained and out of date. That means you'll be missing stability and security fixes.

You'll need to set up our package repository before you can fetch Tor. First, you need to figure out the name of your distribution. A quick command to run is lsb_release -c. Here's a quick mapping:

    * Ubuntu 10.10 is "maverick"
    * Ubuntu 10.04 or Trisquel 4.0 is "lucid"
    * Ubuntu 9.10 or Trisquel 3.5 is "karmic"
    * Ubuntu 9.04 is "jaunty"
    * Ubuntu 8.10 is "intrepid"
    * Ubuntu 8.04 is "hardy"
    * Debian Etch is "etch"
    * Debian Lenny is "lenny"

Then add this line to your /etc/apt/sources.list file:

deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main

where you put the codename of your distribution (i.e. etch, lenny, sid, maverick, lucid, karmic, jaunty, intrepid, hardy or whatever it is) in place of <DISTRIBUTION>.

Then add the gpg key used to sign the packages by running the following commands at your command prompt:

gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

Now refresh your sources and install Tor by running the following commands (as root) at your command prompt:

apt-get update
apt-get install tor tor-geoipdb

Now Tor is installed and running. Move on to step two of the "Tor on Linux/Unix" instructions.

The DNS name deb.torproject.org is actually a set of independent servers in a DNS round robin configuration. If you for some reason cannot access it you might try to use the name of one of its part instead. Try deb-master.torproject.org, mirror.netcologne.de or tor.mirror.youam

found on [https://www.torproject.org/docs/debian.html.en#ubuntu](https://www.torproject.org/docs/debian.html.en#ubuntu)

---

### Post by metalf8801 on 2011-02-25
if you have already add the repository using the Software Center 
All you need to do is to open a terminal and enter 


gpg --keyserver keys.gnupg.net --recv 886DDD89

and 

gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

after that the key should be added and you can install tor using the Synaptic Package Manager

---

### Post by metalf8801 on 2011-02-25
Is this helping at all? Should I explain the next step? Oh and why do you need Tor? Edit I mean how do you want to use tor because if you just want the basics you might want to try the tour browser its easier to set up.

---

### Post by TriBlox6432 on 2011-02-25
I'll try those steps when I get the time.  Sorry for being gone, little busy right now.

Basically I want to mess with my IP address so I can access certain things (with firefox, xchat, and pidgin) without anyone being able to trace me.

---

### Post by overdrank on 2011-02-25
> **TriBlox6432 said:**
> I'll try those steps when I get the time.  Sorry for being gone, little busy right now.

Basically I want to mess with my IP address so I can access certain things (with firefox, xchat, and pidgin) without anyone being able to trace me.

That doesn't sound good. [-(
:)

---

### Post by TriBlox6432 on 2011-02-25
Why's that?

---

### Post by metalf8801 on 2011-02-25
> **TriBlox6432 said:**
> Why's that?

Please don't use Tor to do anything illegal. Tor does a good job of getting around being tracked by advertisers

---

