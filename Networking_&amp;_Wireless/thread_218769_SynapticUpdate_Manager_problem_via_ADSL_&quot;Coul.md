---
title: "Synaptic/Update Manager problem via ADSL: &quot;Could not download all repository indexes&quot;"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by aminoz on 2006-07-19
My Ubuntu Dapper Drake laptop (Dell 1300) can't run Update using my home ADSL connection;  both update manager and package manager stall on the download and I have to cancel out, then I get an error message telling me all the stuff they couldn't do.  

But I _can_ download stuff using Firefox from other sites with no problems (after I fixed the Firefox IPv6 bug).

_And_: when I bring my laptop to the office and use it behind our  Netgear ADSL/router, everything works fine!  Update Manager is able to download all the latest Ubuntu updates and patches.  Then I take my machine home and get the same failure as before. 

So I presume this is some gnarly interaction with my D-link model G604T ADSL/router.  I've updated it to the latest firmware, but it made no difference to the problem.

I'm not running a DNS or DHCP server or any other exotica on my machine.  And I'm not using the wireless facility yet (that's another issue to grapple with after this; it's currently disabled in the ADSL/router).  This problem is happening via ethernet cable using eth0.

Is there something obvious I've missed, or is it just that I bought a dud ADSL/router?

---

### Post by OpsVentus on 2006-07-19
The router shouldn't be a problem (normally).
But can you connect to the internet properly?
What are your internet settings?
Can you ping an internetaddress? (#ping [www.hotbot.com](www.hotbot.com))

---

### Post by aminoz on 2006-07-19
> **OpsVentus said:**
> The router shouldn't be a problem (normally).
But can you connect to the internet properly?
What are your internet settings?
Can you ping an internetaddress? (#ping [www.hotbot.com](www.hotbot.com))

...

I can connect ok apart from the Synaptic package manager and the Uodate Manager; they aren't working; firefox works ok.  I can ping my ISP ok, and I can ping your example, [www.hotbot.com](www.hotbot.com).  My ADSL settings for the D-link look pretty normal, using the ISP's DHCP service, and taking the ISP's DNS addresses.  

What I need to know is what are the Synaptic package manager and the Uodate Manager doing that gives this result?  This is my first experience of Ubuntu and these two programs.

---

### Post by Derek Djons on 2006-07-19
> **aminoz said:**
> ...

I can connect ok apart from the Synaptic package manager and the Uodate Manager; they aren't working; firefox works ok.  I can ping my ISP ok, and I can ping your example, [www.hotbot.com](www.hotbot.com).  My ADSL settings for the D-link look pretty normal, using the ISP's DHCP service, and taking the ISP's DNS addresses.  

What I need to know is what are the Synaptic package manager and the Uodate Manager doing that gives this result?  This is my first experience of Ubuntu and these two programs.

Well, let's see what we can find out. Can post the following two things:

**1. sources.list**
You will find this at: /etc/apt on your hard drive.

**2. update**
Open a terminal (for example: Applications -> Accessories -> Terminal) and type the following command:

sudo apt-get update

You'll see quite some text scrolling down. Copy the output and post it.

- - -
This way we can check if your repositories are fine. That will be one possibility less to the issue.

---

### Post by KFASheldon on 2006-07-19
I have a simualr problem for last two days, not all repo index can be downloaded, if I try again then it normaly works as repos are just too busy I guess, odd though I can connect directly to the repo from firefox no problem. Have any changes been made to Synaptic recently that may have been unoticed or maybee the last kernal update is causing trans errors and the index loading is not error checked ? unlike firefox dont know but any help would be good.

---

### Post by aminoz on 2006-07-20
**1. sources.list**
You will find this at: /etc/apt on your hard drive.

*HERE IT IS - the addresses look back to front, don't they? It's the way DNS uses them, I believe.* 
/etc/apt$ cat sources.list  

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main re stricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univer se multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted un iverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


**2. update**
Open a terminal (for example: Applications -> Accessories -> Terminal) and type the following command:

sudo apt-get update

You'll see quite some text scrolling down. Copy the output and post it.


*THIS IS THE RESULT:*
amcb@amcb-laptop:/etc/apt$
amcb@amcb-laptop:/etc/apt$ sudo apt-get update
Password:
44% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

*Note :  a couple of other lines flashed up very quickly before the one above appeared; presumably they were only c/r and not l/f terminated.  I couldn't see what was in them,  From the single line you can see, it looks like it's getting the wrong address.*

The LAN address of my ADSL/router is 10.1.1.1   The similarity to the funny address above looks significant.  The subnet mask is 255.0.0.0  

The WAN Settings are
        Virtual Circuit  	   	
	Status 	Connected 	
	Connection Type 	pppoe 	
	IP Address 	125.255.18.220 	 
	Subnet Mask 	255.255.255.255 	 
	Default Gateway 	203.9.190.190 	 
	DNS Server 	61.8.0.113

---

### Post by OpsVentus on 2006-07-20
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univer se multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted un iverse multiverse

Should be:
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

44% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]
This is wrong as well. The ip-adres of au.archive.ubuntu.com is not 1.0.0.0 it's 130.95.3.26. And security.ubuntu.com is 130.239.18.158.

What ip-adres does it say it pings when you ping security.ubuntu.com?
In terminal go:
#ping security.ubuntu.com
Maybe your dns is the problem. You can also try to replace all the dns-name's in the sources.list by there ip-adresses and try to "sudo apt-get update" again.

Cheers,
Bart.

---

### Post by aminoz on 2006-07-20
Newsflash!

I found another posting in a "Ubuntux" where somebody described a similar if not the same problem, and it gave me a clue.
([http://www.ubuntux.org/problem-synaptic-update-manager-could-not-download-all-repository-indexes](http://www.ubuntux.org/problem-synaptic-update-manager-could-not-download-all-repository-indexes))

I connected to my ADSL/router, and reconfigured its DNS settings to disable  "DNS Relay", which means it's not giving my laptop DNS IPs' any more.  But I took the two DNS IPs it had automatically acquired and put them into /etc/resolv.conf  -- then I ran sudo apt-get update and it appeared to work! I tried Update Manager and it did too.  

At that point, my wife, also hooked up to ADSL/router, called down the hallway that the internet was very slow, and then that it was broken.  After a short conversation in which I assured her I hadn't done anything, I tried Synaptic and attempted to download a couple of things.  That failed. I looked at resolv.conf and it had been clobbered back to its orginal contents, removing my modifications.  

Needing time to think, I quietly restored the ADSL/router back to its original configuration and my wife stopped complaining,

I call that progress.  If I can stop resolv.conf being clobbered, then unobtrusively reconfigure my wife's OSX machine, I'll be set.  (Until the ISP changes its DNS numbers, I suppose.)

---

### Post by aminoz on 2006-07-20
[http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univer se multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted un iverse multiverse

Should be:
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

*Sorry, it's getting late, I can't see the difference here.  *

44% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]
This is wrong as well. The ip-adres of au.archive.ubuntu.com is not 1.0.0.0 it's 130.95.3.26. And security.ubuntu.com is 130.239.18.158. *Ah! 1.0.0.0 is the dud IP that my ADSL/router is giving out!*

What ip-adres does it say it pings when you ping security.ubuntu.com?
In terminal go:
#ping security.ubuntu.com
*Currently I can't ping; see my last message, the one I added in excitement after yours because I hadn't seen it while I'd been experimenitng,*

Maybe your dns is the problem. You can also try to replace all the dns-name's in the sources.list by there ip-adresses and try to "sudo apt-get update" again.  * Maybe this suggestion might work; it'll be better than me changing my ADSL/router anbd my wife's machine (see other post)*

Cheers,
Bart.

*Thanks for the help!*

---

### Post by OpsVentus on 2006-07-20
Ok it's your dns, now we're getting to the problem/solution!
Normally if you tell your router not to relay dns, then it will give you the dns-servers required from your ISP.
So if you have got DHCP running then you can try the following:
Disable dns relay in your router.
In terminal go:
#dhclient eth0

Now check if you can ping [www.hotbot.com](www.hotbot.com), if not, check resolv.conf to see what dns-servers are in there.
If it does work, check synaptic again and run to your wife and make sure you reconnect to the network. (How I don't know, but one way is to reboot)

Cheers,
Bart.

---

### Post by six on 2006-07-20
FYI, I'm using a Dell Inspiron 1300 as well (to type this). It worked right out of the box with my (wired) Safecom modem/router. No problems with eth0, or updating with Synaptic.

I don't know if this will be of any use to you, but here are my networking settings (from System->Admin->Networking):

Network Settings
Location: (blank)

Connections tab
Ethernet connection
The interface eth0 is active
Default Gateway Device: eth0

General tab
Host name: inspiron
Domain name: (blank)

DNS tab
DNS Servers
(primary ISP server IP address
+secondary ISP server IP address)

Hosts
IP Address, Aliases
ff00::0 ip6-mcastprefix
127.0.0.1 localhost.inspiron
fe00::0 ip6-localnet
ff02::2 ip6-allroutes
ff02::1 ip6-allnodes
::1 ip6-localhost-ip6-loopback
127.0.1.1 inspiron
ff02::3 ip6-allhosts

I didn't have to change anything; all these entries were there by default. And I haven't needed to do anything to Firefox with regards to ipv6.

EDIT:

Forgot to include my sources.list (changed from gb.* to au.*). I'm just starting out with Ubuntu, so it'll be a good base to build on. I've commented out the source repositories, as I've read that it's rare you'll need them. At the bottom is the Canonical repository so you can get Opera 9 and some other stuff if you want.

I'm not saying this is the definitive source.list to have, it's just what I've picked up on so far.




## Add comments (##) in front of any line to remove it from being checked.   

## Use the following sources.list at your own risk.  



deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

## deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse



## MAJOR BUG FIX UPDATES produced after the final release

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

## deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse



## UBUNTU SECURITY UPDATES

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse



## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

## deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
## deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free 

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

