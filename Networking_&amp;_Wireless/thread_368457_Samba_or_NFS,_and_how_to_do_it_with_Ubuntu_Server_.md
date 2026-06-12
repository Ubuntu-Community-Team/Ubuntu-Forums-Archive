---
title: "Samba or NFS, and how to do it with Ubuntu Server from CLI"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by Stervyatnik on 2007-02-23
I hope there's a question at the end of my ranting. ;)

I have four computers I'm learning networking on. I originally loaded Ubuntu Server on one, and Ubuntu Desktop on the other three. But I found working with the CLI for Server to be frustrating, at best, so I re-loaded it with Ubuntu Desktop. I was intending to load Apache, MySQL and PHP and "make" it a server for my home network.

I am purposely NOT connected to the Internet at this time. For one thing, I have just a dialup connection. Secondly, I want to build a completely isolated home network, that we can share files across and printer/scanner/hardware resources. My goal is to get the networking aspect down, without having to worry about the Internet, for now. (Later - much later! - I hope to get broadband and connect via cable modem/router to the Internet.)

The problem is - and here's where I rant a bit ;) - every instructional tutorial I've seen assumes - in my case, WRONGLY! - that you're connected to the Internet, AND that you have - again, WRONGLY! - broadband capability.

I've tried to install the Apache, MySQL PHP, and Samba packages from the CD-ROM, where (I think) it says I can. But I keep getting an error message about dependencies, and it never installs. I have also edited the /etc/source.list, un-commenting-out the lines to allow from the "universal repository," but it assumes - again! - that I'm connected to the Internet.

I also tried to set up NFS file sharing (redundant?) but I was hopelessly confused by all the CLI machinations they wanted me to go through. Samba looks like my best bet, especially since (much later!) I hope to add two WinXP computers to my network.

I downloaded the tar.gz Samba package last night, and am about to try to install that on the desktop/mod-server. BUT, do I need Apache, MySQL and PHP running first in order to run it? That's my first question, and thankfully, there WAS a question! ;)

Second question is: Can I do what I'm envisioning - running an isolated, non-Internet-connected network - with four Ubuntu Desktop machines (all with GNOME GUI), with one of them "upgraded" to a server with Apache, MySQL and PHP, PLUS the GNOME?

Am I asking too much, or is it possible? Thanks for any help/pointers/directions.

---

### Post by Muzik83 on 2007-02-23
It is all possible to do, but made difficult by lack of internet connectivity.

First, the answer to your question, no you dont need apache, mysql, or php for samba.  You may need a few dependencies though, especially depending on what you want to do wtih samba (this is extra info, not related to what you want to do, but an example: To log in to your linux machine using active directory accounts, you will need krb5-libs, and a bunch of other stuff for krb5).

For samba configuration, I recommend SWAT.  If you built samba from source (.tar.gz, sounds like you did), then when it is installed you can go to [http://localhost:901/](http://localhost:901/) .  You dont need internet access to do this.   It's a graphical way to configure samba and smb.conf (but it over-writes smb.conf removing all comments if you have any...just a heads up)

As for installing apache et al, i'm not exactly sure how you can do it.  The only way I can think is to do it manually, getting each dependency.  Is it possible to dial into the internet in order to get the dependencies once?  If so, apt will download and save all packages in /var/apt/cache/, you could use those on other machines (so as not to download them 4x over)

I hope this helps a bit
-sean

---

