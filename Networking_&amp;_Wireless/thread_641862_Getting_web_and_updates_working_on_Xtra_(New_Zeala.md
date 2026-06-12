---
title: "Getting web and updates working on Xtra (New Zealand)"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by dougkiwi on 2007-12-15
Hi.  This is my first post.

After some struggle, and some help from this forum, I've got web (Firefox) and updates
(like Synaptic and apt-get) working with my ISP, which is Xtra, which is part of Telecom
New Zealand.  I'm using a D-Link ADSL modem which Xtra provided.  Since a lot of New Zealand newbies will be connecting to Xtra via a D-Link modem (the name "D-Link" is on the top of the modem) I thought I would reveal what I needed to do.

When I started with Ubuntu (I'm using 7.10 Gutsy Gibbon), I could not get web pages, not even google.  I could not download or update software with apt-get or Synaptic.

 There are two things you've got to do, basically.

First of all, you must disable ipv6.  I have it from a good source inside of Telecom New Zealand, Xtra's owner, that Xtra doesn't handle ipv6 very well.

Then, you must supply Telecom's nameservers in the file /etc/resolv.conf .  Either the modem or Xtra will probably mess up if you don't.  If you type 
sudo apt-get update
and get "1.0.0.0" over and over again in amongst the messages, then you have this problem.


If you google "disable ipv6" you will get a lot of suggestions for that. I actually did 4 things:
1) I started firefox and typed in "about:config" (no quote marks) as if it were a web address.  Then, in the box marked "filter" I typed in "ipv6".  Click on "network.dns.disableIPv6" until it says "true" on the right hand side.  That should get Firefox working.
2) Edit a file called "/etc/modprobe.d/blacklist" and put in this line:
blacklist ipv6
3) Edit a file called "/etc/modprobe.d/bad_list" (it doesn't exist yet) and put in this:
alias net-pf-10 off
4) Edit the file /etc/modprobe.d/aliases and change the line 
alias net-pf-10 ipv6
to read this instead:
alias net-pf-10 off

now in a terminal give these commands:
ifdown -a
ifup -a

which restarts your networking.

Experts will probably say you don't have to do all that, and they're probably right.  Being a beginner, I used a big hammer on the problem.

Now you want to change your /etc/resolv.conf file:
It probably looks like this:
nameserver 10.1.1.1
make it look like this:

#nameserver 10.1.1.1
nameserver 202.27.158.40
nameserver 202.27.156.72

Those nameserver addresses I found on the Xtra help site.

Maybe restart your networking again for good luck.

I hope that helps and good luck!   Someday maybe New Zealand Xtra and D-Link will work OK without any effort on your part but that day is not yet here.

dougkiwi

---

