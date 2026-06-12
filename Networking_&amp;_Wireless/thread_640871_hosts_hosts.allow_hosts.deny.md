---
title: "hosts hosts.allow hosts.deny"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by andrewabc on 2007-12-14
So I use use a hosts file from [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm) to block all advertisements from connecting to my computer. In windows XP, I simply let it overwrite the hosts file it has there. then I edit the file with all 127.0.0.1 to 0 to make the file smaller (it works the same as 127.0.0.1).

Now with ubuntu, I can get it to work, but only in the hosts file and if I keep 127.0.0.1 in front of each bad website.

I am wondering what hosts.allow and hosts.deny are for. I tried adding the bad websites to hosts.deny but that did nothing.

I would continue to use the normal hosts file, but I am not sure if that is the correct thing to do and also if I go to system->administration->network->hosts tab  it can cause my computer to freeze because it is trying to put the whole hosts file in the small amount of space.

I manually enter the info into the ubuntu hosts file by copying/pasting below the text that is there by default

---

### Post by heindsight on 2007-12-15
The hosts file is used to translate hostnames to IP addresses. With the hosts file setup you're describing, each time your computer wants to look up the IP address for one of the hostnames you've listed in the hosts file, it gets the address 127.0.0.1 instead of the real address for that hostname, and so makes a connection to itself. In other words, it is not so much preventing those sites from connecting to you, as preventing you from connecting to those sites.

hosts.allow and hosts.deny are used as a simple method of access control to specify hosts on the network that are allowed or not allowed to connect to certain services running on your machine. For example, I run an ssh server on my computer and I use hosts.allow and hosts.deny to prevent everyone except machines on my local network from connecting to my ssh server. By default, Ubuntu does not run any services that other hosts can connect to, so effectively these files don't do anything.

I suppose there's nothing wrong with using your hosts file in this way to prevent connections from your machine to certain host names, as long as you keep the default entries in the hosts file intact. However, this seems to me to be a bit excessive. If you're using firefox as a web browser, you can install the adblock or adblock-plus firefox extensions to achieve more or less the same effect (preventing firefox from connecting to malicious sites or sites hosting advertisements). It is unlikely that you will need to prevent other software from connecting to these sites, unless you install some malicious software on your machine.

Also, note that using the hosts file in this way, does not completely prevent your machine from establishing connections to the sites you have listed. It only prevents correct translation of those hostnames to IP addresses. So if, for example, some website contains an link to a malicious site specifying its IP address instead of the hostname you have listed in /etc/hosts, then your /etc/hosts file will not protect you from connecting to that malicious site.

---

### Post by andrewabc on 2007-12-15
I thought adblock+ only hid the advertisements, and did not prevent connection/download of the advertisement.

This makes a hosts file very useful with dialup connections.

---

### Post by heindsight on 2007-12-15
I've never used adblock, but with adblock plus, blocking an item means that firefox won't download it.
For example, I use the filter rule
```
*doubleclick.net/*
```
which blocks any ads hosted by doubleclick. The result is that as long as I have adblock plus enabled, firefox never connects to any host with doubleclick.net in the hostname (unless I tell it to).

---

### Post by andrewabc on 2007-12-15
Thanks for the info :)

I remember at one point seeing an advertisement show up and then very fast adblock+ would make it disappear, so I figured adblock plus only hid advertisements.

---

