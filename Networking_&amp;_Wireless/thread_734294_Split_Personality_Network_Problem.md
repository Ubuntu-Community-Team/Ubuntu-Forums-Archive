---
title: "Split Personality Network Problem"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by ytene on 2008-03-24
Hey everybody...
At the risk of being told I'm trying to do something very silly, I've just hit a snag with a fresh 7.10 build and wonder if someone can help me.

First, the context and objective:
I have a single Linux machine that is connected to the internet by a firewall/router and a DSL line. I want to use this machine in **two** discrete configurations

[LIST]
[*]an Internet "Client" with no local services running
[*]a local Development Server, with multiple services
[/LIST]

When in Dev Server mode, I want to be running Apache2, MySQL, and BIND9 [along with non-daemon components such as PHP5. In Client mode I want all these to be shut down, and to have the machine re-configured for internet-only traffic.

I'm sure there are many ways of achieving the above, but, being a Linux Luddite, I approached with the following sledgehammer. I wrote a script [netswap], which looks like this:-

======================================================
if [ "$(id -u)" != "0" ]; then
	echo "This script is only available to the root user."
	exit 1
fi

case "${1:-''}" in
  'local')
	if [ ! -f /etc/network/interfaces_local ]; then
		echo "Cannot find /etc/network/interfaces_local."
		exit 1
	fi
	if [ ! -f /etc/resolv.conf_local ]; then
		echo "Cannot find /etc/resolv.conf_local."
		exit 1
	fi
	cp /etc/network/interfaces_local /etc/network/interfaces
	cp /etc/resolv.conf_local /etc/resolv.conf
	/etc/init.d/networking restart
	/etc/init.d/bind9 restart
	echo "Successfully converted to Local Network Config..."
	;;

  'net')
	if [ ! -f /etc/network/interfaces_internet ]; then
		echo "Cannot find /etc/network/interfaces_internet."
		exit 1
	fi
	if [ ! -f /etc/resolv.conf_internet ]; then
		echo "Cannot find /etc/resolv.conf_internet."
		exit 1
	fi
	cp /etc/network/interfaces_internet /etc/network/interfaces
	cp /etc/resolv.conf_internet /etc/resolv.conf
	/etc/init.d/bind9 stop
	/etc/init.d/networking restart
	echo "Successfully converted to Internet Network Config..."
	;;

  'status')
	ifconfig -a
	
  	;;

  *)
	echo "Usage: $SELF local|net|status"
	exit 1
	;;
esac
======================================================

As you can see, the script depends upon the existence of four simple files - 2 copies each of 

/etc/resolv.conf

and

/etc/network/interfaces

with the respective copies being set for the "_local" and "_internet" configuration options. Basically, the way that this has been working [ since the days of 5.10] has been that I deploy the files, then issue the command

sudo netswap local

or 

sudo netswap net

or 

sudo netswap status [this last to tell me what my present configuration is]

My "local" interfaces file is relatively complex, containing multiple binds to the one network card so that I can host multiple different web addresses with a partitioned Apache.

So this has all stopped working since I built a new version of 7.10 on a new Quad-Core Intel machine. I have it working perfectly on an AMD system based on a Tyan Thunder mobo with a pair of Opterons, but moving to a new machine has broken something. 

Maybe I can't see the wood for the trees. 

I don't get an error message, but what happens is that when the script tries to do a bind9 restart, the script hangs and does not come back. Opening another window and checking the machine suggests that bind is also hanging. For what it's worth, I just did a lift and drop of my bind9 config files and can paste here if required...


I appreciate this might not be the *best* approach here, but for a variety of reasons I want to stick with a multi-homed IP solution rather than try and switch Apache to a different partitioning model. So please bear with me on that. Thanks.

I've tried breaking the script down and executing the commands serially as root, but that bind9 restart gets me every time. 

ubuntu 7.10 AMD64, fully patched up.

Thanks and advance...

---

### Post by ytene on 2008-05-06
Oops. The new build is 8.04/AMD64. 

I have this working OK under 7.10/AMD64.

Duh...

---

