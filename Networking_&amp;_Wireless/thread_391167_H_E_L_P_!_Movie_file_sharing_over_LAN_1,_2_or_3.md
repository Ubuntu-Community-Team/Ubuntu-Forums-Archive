---
title: "H E L P ! Movie file sharing over LAN? 1, 2 or 3?"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by Neobuntu on 2007-03-22
I have a notebook running Feisty and it can play a movie via TV out.

The movie is on my desktop. I want to use my home LAN (100BT) network (instead of sneaker net) to copy it over to the notebook (that will be unplugged from the network later; when it is moved over to the TV and playing) because I think it would be a faster transmission speed at 100BT. 

Problem: Time to set up.

Before I get knee deep in networking, which way should I use?

1. I already have a Samba net shared folder with the file to copy in it BUT the notebook is not (apparently) set up to see it and I have already forgotten how to do it. It includes working around the firewall and making sure samba is installed and set up I THINK.  But then there #2

2. What's with this Zeroconf thing? I set the same desktop shared folder to be used by "Zeroconf" but the laptop deos not see it.

3. Linux networking? When should I use this? Is it the same as Zeroconf? Let's see...Lisa or something like that, it's called?

My real question is why would I use one over the other and why does networking take so much darn time; over sneaker net?

Please tell me I am missing a better way. Everything else works so well.

Windows seems MORE time consuming and with less choice BTW. Do I need to use samba though; because I can dual boot all my computers? Just for comparison, now-a-days.

PLEASE HELP
:confused:

---

### Post by Mr. C. on 2007-03-22
Wow, that's a lot of questions!

At the roots of Linux networking is TCP/IP.  It's the protocol of the internet, and has been the primarle protocol in Unix for ... forever.

Samba allows you to setup and use Windows' style SMB networking.  Its works over TCP/IP.

Samba once set up, works fine.  Many people get very confused by the configuration required.  There are plenty of HowTos, but despite all of them, many people have trouble with the configuration.  You can browse your network in Windows to find your shared folder.  Browse windows networking.

You can alternatively scp, FTP or Web transfer, depending upon which servers you have setup.  There are many other alternatives too.

Since you're in a mixed environment, NFS really isn't a good option.  If you don't know what that is, no worries.

Zeroconfig allows systems to connect to a local network without user intervention or configuration.  Its the Plug-n-Play of the networking world, typically used in wireless networks, but also for local-link configuration (eg. two systems connecting to each, w/out a DHCP server will each select a local-link IP address).

Perhaps the easiest way for you to copy your movie is to enable a shared folder on your laptop, and from Ubuntu copy it to that share.  That way, you don't have to worry about finding your samba shares on Windows.

Anyway, just a bit to get you thinking.  As more specific question if you need more help.
MrC

---

### Post by Neobuntu on 2007-03-23
Thank you so much.

Hey that's pretty cool. I forgot all about simple scp. I could have used a simple command (and referenced "man scp" for reminders). I guess I'm just wondering what a new user would do.

Excellent idea to just share a folder on the laptop. 

Thanks for the run down.

Any body else?

---

### Post by crouton on 2007-03-24
Zeroconf isn't a wireless-only thing, fyi. [http://en.wikipedia.org/wiki/Zeroconf](http://en.wikipedia.org/wiki/Zeroconf) is a good primer.  The Avahi daemon is the Linux version of a Zeroconf utility.  The whole thing is rather 'smoke and mirrors' as in it mysteriously works, when it works. :)  

That said, you could certainly stream the movie from your desktop to your laptop.  Samba is probably the easiest way, and it sounds like you're already halfway done.

---

### Post by Mr. C. on 2007-03-24
Thanks for the correction.  I've updated my original statement to be accurate.

MrC

---

