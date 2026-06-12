---
title: "Firestarter firewall"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Berean on 2010-11-22
Hello,

Would someone be able to tell me the benefits of using Firestarter, or indeed any firewall, please?  I understand that Linux doesn't need anti virus software, but don't quite understand the point of installing a firewall.  Many thanks.

---

### Post by ibizatunes on 2010-11-22
A firewall stop hacker, and unauthorized access etc to your computer, ubuntu has a firewall install by default, and unless you need to configure it yourself ie ssh or something, i would just alone (if inst broke don't fix it)

---

### Post by rburkartjo on 2010-11-22
yes and firestarter hasnt been updated in years

---

### Post by HermanAB on 2010-11-22
Howdy,

A firewall is mostly a Windows thing.  Traditionally, Windows ran many undocumented services that could not be disabled.  Over the years, MS has cleaned up their act somewhat and most of these services have been identified by third parties.  So, in the past, the only way to keep a Windows machine safe, was to put an internet packet filter in front of it.  

On a Linux system, it is very easy to tell which services are listening and if you don't want it to listen, disable it.  So, on a properly managed Linux system, a firewall is not required.  Indeed, most firewall devices actually run Linux.

---

### Post by mcduck on 2010-11-22
Firewall is used to control and restrict network traffic, when you can't do it from the responsible programs or services themselves, or you don't trust them

On Ubuntu you shouldn't have problems trusting your software, at least as long as you stick yo using official repositories, and all the programs and services should already have suitable configuration option for limiting network access if you need to do so.

Anyway, the default install of Ubuntu has no running services that would listen for incoming network connections, thus there's absolutely nothing for a firewall to do. There's no reason to restrict traffic that nobody is listening to. You should only need a firewall if you install some additional software that would listen for incoming connections, like some server application for example. And even in that case you'd usually either actually *want* the server to be visible to  outside world, or be able to limit the connections form the server itself.

For example my Ubuntu system only has one program that would listen for incoming connections, the Apache web server. Were I running a production server, I would actually need it to be visible to the Net, so I wouldn't need  firewall. On the other hand I'm actually running a production server, and therefore limit the access to local network only directly in Apache's configuration, so once again a firewall wouldn't make any difference....

So, the simple answer is that you only need a firewall if you can't control the system and software themselves, or can't trust them to behave like they should. Neither one of these is a likely situation in desktop use.

However if you still want to use a firewall, the features required to crate one are built into Linux itself, you just need something to control it. And Ubuntu comes included with UFW, which does exactly that. If you want a graphical tool, use GUFW. (and keep in mind all these are just *configuration tools*, they dn't need to run for the firewall to be active).

---

### Post by 3rdalbum on 2010-11-22
> **Berean said:**
> Hello,

Would someone be able to tell me the benefits of using Firestarter, or indeed any firewall, please?  I understand that Linux doesn't need anti virus software, but don't quite understand the point of installing a firewall.  Many thanks.

If you are using fixed-line broadband such as ADSL or cable, your modem probably already includes a firewall that is already configured to block all incoming connections. You would not need an additional firewall running on your computer; the one in the modem will ensure that any "personal firewall" on your computer would never see anything to block.

On Ubuntu, there's virtually no point to running a personal firewall. I can only think of a couple of reasons why you would:

1. You have a computer that runs a testing web server that you want ONLY your computer to be able to access, and you don't trust the other computers on the same network or you are not behind a broadband router.

2. You have a portable computer that runs some other kind of server service for use on your home network, but you occasionally use this computer on public wifi or mobile broadband, so you would want a personal firewall to block off access to those servers temporarily.

A default install of Ubuntu will not listen to any incoming connections anyway, and if you install something that does listen for incoming connections, then you probably want those to be accessible anyway!

---

### Post by matt_symes on 2010-11-22
Hi

Wow. An excellent set of responses. Not much more to add really.

The firewall in Ubuntu is called netfilter and is disabled by default on install. It is controlled using a set of rules defined in IPtables and these are configured using ufw or gufw (the graphical version).

Kind regards

---

### Post by nlsthzn on 2010-11-22
> **rburkartjo said:**
> yes and firestarter hasnt been updated in years

Then again... is there anything to update?

One cool thing I saw that  Firestarter can do is share your internet connection with the rest of your network using only one NIC (like Windows ICS) which is sweet :)


Regards
Neil

---

### Post by QLee on 2010-11-22
> **nlsthzn said:**
> Then again... is there anything to update?

I'm going to agree with you about this, I don't imagine there is a lot of "updating" required for an application to serve as a GUI to iptables. After all, it's just an easy way to write rules for those who can't or won't learn to do it manually.

That being said, many users on this forum repeat what they have read in other forum posts that have been posted by long time users and admins. Some make a big deal about it not being maintained, but the truth is that the Debian maintainer still maintains firestarter and it will still be included with the newest stable release, Squeeze, which will be released "when it is ready" (Debian does not follow a hard and fast release cycle like Ubuntu).

On the other hand, I don't suggest it to users in the ABT forum because they might tend to use it like Zonealarm (or similar) on Windows and that can create a security issue because the firestarter GUI runs as root and Ubuntu has been crafted to use sudo for temporary elevation of rights to help avoid leaving an application running as root on a system. It's just not advisable, especially for new users. Can't see why anyone would want to anyway, the "hits" would probably drive you crazy unless you understand security, and there is no need to show them unless one is truly trying to watch something in particular. All that stuff is in the logs anyway and knowledgeable users, can parse them with a script. 

Posters 3rdalbum and mcduck have given very good answers, which boil down to something simple for new users, trust the system, what in the past was written as, "trust the force, Luke", a line from an old movie.

I wonder if I need to put my flamesuit on after this comment or if we are open to opinion.

---

### Post by nlsthzn on 2010-11-22
> **QLee said:**
> I'm going to agree with you about this, I don't imagine there is a lot of "updating" required for an application to serve as a GUI to iptables. After all, it's just an easy way to write rules for those who can't or won't learn to do it manually.

*snip*

Posters 3rdalbum and mcduck have given very good answers, which boil down to something simple for new users, trust the system, what in the past was written as, "trust the force, Luke", a line from an old movie.

I wonder if I need to put my flamesuit on after this comment or if we are open to opinion.

"Away put your weapon, I mean you no harm!" ;)

---

