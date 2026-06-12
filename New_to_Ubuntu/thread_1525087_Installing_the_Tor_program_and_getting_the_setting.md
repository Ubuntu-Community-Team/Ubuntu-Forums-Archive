---
title: "Installing the Tor program and getting the setting right"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by explore on 2010-07-06
Day two of experience with Ubunto OS. I am very enthused about NEVER giving Bill Gates another thin dime for his crappy OS.


I have downloaded Tor while using Ubunto as the OS and There appear to be many settings that I do not  understand. 

I need a step by step  guide on the settings to get this program to work

I noticed there is a Anon program in the download site for Ubunto and I down loaded that too and installed but I don't see that it is working. My IP has not changed.  

Please let me know what information you need. I can reinstall and go through this step by step if someone is willing to assist.

Thanks, Explore(r)

---

### Post by jmszr on 2010-07-06
explore,

Perhaps this will be of some help: [http://maketecheasier.com/install-tor-in-ubuntu/](http://maketecheasier.com/install-tor-in-ubuntu/)

---

### Post by mkvnmtr on 2010-07-06
The best tutorial I have found is on the Tor sight. It explains everything you need to do to install with a repository, install tor button and use popoli It will be to your benefit if you follow that tutorial.

---

### Post by explore on 2010-07-06
Thank you folks for your responses. 

I will go and look at these sites. I will make another attempt to get this issue resolved.

---

### Post by explore on 2010-07-07
I went to the Tor site and here is the first instruction : You'll need to set up our package repository before you can fetch Tor. First, you need to figure out the name of your distribution. If you're using Ubuntu 9.10 or 10.04, it's "karmic", while 9.04 is  "jaunty", 8.10 is "intrepid", and 8.04 is "hardy". If you're using Debian Etch, it's "etch", and Debian Lenny is "lenny". Then add this line to  your /etc/apt/sources.list file:

Question: Although when I do a search for this file I can find it, I don't know how to add the line to the file: 
deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main

---

### Post by oldos2er on 2010-07-07
If you're using Gnome, click the menus System, Administration, Software Sources, Other Software, Add. [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by GSF1200S on 2010-07-07
For what its worth, I have only had success using Privoxy in combination with Tor- none of the others worked for me. Im sure they do, but if you have issues, its something to keep in mind.

---

### Post by explore on 2010-07-08
Message: 


Your Broadband Router May Not Be Plug 'n Playable!
Message: TorK can't contact your router to optimize it's configuration for Tor.
This means: Check that UPnP is enabled on the router and that your computer firewall allows traffic to and from the router. You can still be a server, but the ports Tor uses will be the defaults rather than 443 and 80.

Question: How do I address this issue? Please remember I have very  little experience with these computers.

---

### Post by oldos2er on 2010-07-08
You'll need to login to your router to change its settings (assuming it's yours to change). Try opening [http://192.168.0.1](http://192.168.0.1) in Firefox.

---

### Post by explore on 2010-07-08
> **oldos2er said:**
> You'll need to login to your router to change its settings (assuming it's yours to change). Try opening [http://192.168.0.1](http://192.168.0.1) in Firefox.

Would that be the Comcast business gateway? 

The writing on this page is   "This Gateway helps you set up and secure your Local Area Network,  support your applications and servers, and manage your users' access to  the Internet.  Feature Settings provide you with many options to help protect and  manage your network. You can block certain Web sites, configure your  security features or block outside computers from the network. You can  also get detailed information on your gateway and change a variety of  other settings-- it's all right here.
  Thank you for choosing Comcast Business.
   **Feature Descriptions**
  Feature Settings: This section is for all users to view or change the features  available on the gateway. Please note: Changes made to these settings  may affect Internet connectivity and LAN network settings."If So: Which one of these tabs do I need to click? features or block  outside computers from the network. You can also get detailed  information on your gateway and change a variety of other settings--  it's all right here.  Thank you for choosing Comcast Business.
   **Feature Descriptions**
__

This section is for all users to view or change the features  available on the gateway. Please note: Changes made to these settings  may affect Internet connectivity and LAN network settings. If This is the correct page for this setting, which tab should I click?
             **Site Navigation**
Main
feature settings
-Administration
-Lan
-Firewall
-gateway summary

---

### Post by oldos2er on 2010-07-08
> **explore said:**
> Would that be the Comcast business gateway? 


 No, it's a generic router IP. May I suggest you Google your router's make/model for info; or if Comcast owns it, contact them.

---

### Post by explore on 2010-07-09
Question: Where do I get Privoxy program of which you speak, GSF 1200S  ?

Post Script: It appears you have a lightening fast machine with massive memory.

---

### Post by MacFall on 2010-09-13
The instructions at [http://maketecheasier.com/install-tor-in-ubuntu](http://maketecheasier.com/install-tor-in-ubuntu) do not work for me. 

When I enter: sudo sh-c 'echo "deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) Ubuntu main" >> /etc/apt/sources.list'

I get the reply: sudo: sh-c: command not found

If I enter: it with "ubuntu lucid" as the distro version I get the reply: bash: /etc/apt/sources.list: Permission denied

Also, in my Vidalia settings it is looking for the Tor software in /usr/sbin/tor, which does not exist. How do I create it there?

PS, I'm a total noob and I'm not so good with computers in general. I failed QBASIC in highschool and Java in college. So you're going to have to talk to me like I'm an idiot.

---

### Post by MacFall on 2010-09-14
Ok, I got Tor to install, and Vidalia has located it. However, when I try to run Tor through Vidalia, I get this message: 

> Vidalia detected that the Tor software exited unexpectedly. Please check the message log for recent warning or error messages.
The message log has this to say:
> Sep 14 14:15:51.013 [Notice] Tor v0.2.1.26. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Sep 14 14:15:51.013 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Sep 14 14:15:51.013 [Notice] Opening Socks listener on 127.0.0.1:9050
Sep 14 14:15:51.013 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Sep 14 14:15:51.013 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Sep 14 14:15:51.013 [Error] Reading config failed--see warnings above.
If I try to kill the existing Tor process and let Vidalia open its own, the terminal returns "Operation not permitted."
This is perturbing.

---

