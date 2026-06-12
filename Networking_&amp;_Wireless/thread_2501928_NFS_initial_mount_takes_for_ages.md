---
title: "NFS initial mount takes for ages"
date: 2024-10-26
forum: Networking &amp; Wireless
---

### Post by Lee_Nowell on 2024-10-26
Hi

I am running version 22.04 and for some time I have been having issues with NFS clients taking a long time (say 30 seconds) to connect first time. Once connected it seems to be fine.   I saw a post suggesting that it could be timing out on the name server before connecting to the right one.  Looking at /etc/resolv.conf on the server, it has the following

nameserver 8.8.8.8
nameserver 127.0.0.53


Which if that means it is going out to check the Google DNS server for the local host  name first before looking internally then this may explain the behaviour.  Could this be the issue and if so, what do I do to fix it?  If not, any ideas what else I can check?  The client in question is a FireTV stick so can't run anything on it / change config so hoping it is a server side issue.

Thanks

Lee.

---

### Post by TheFu on 2024-10-26
You'll need to describe the setup both the client and the server more clearly to get any help.  Be certain to point the config files from the NFS server and the client. Otherwise, nobody can help.

---

### Post by Lee_Nowell on 2024-10-26
To be honest, not sure what config file would be helpful so as a starter for 10

This is the entry from /etc/exports on the server

/media/PrimaryData/Documents    *(rw,anonuid=65534,anongid=65534,async,all_squash,insecure,no_subtree_check)

As the client is a FireTV stick not sure what config I can get from there?

Thanks

Lee.

---

### Post by TheFu on 2024-10-26
I don't understand. Please assume we cannot read your mind.   "not sure what config file would be helpful so as a starter for 10"  - doesn't mean anything to me.  10 what?  Do you have 10 NFS clients?

---

### Post by ajgreeny on 2024-10-26
@ TheFu

"Starter for 10" is a well known phrase in UK and is a quote from a TV program called "University Challenge".

Sorry Lee, but I can't help with the NFS query; I've never used NFS.

---

### Post by TheFu on 2024-10-26
Thanks, so it it like saying "I'll take foreign cultures for 50, Bob" ... or is it a reference to 10 Downing?

I'd use this:
```
/media/PrimaryData/Documents    192.160.1.*(rw,async,root_squash,no_subtree_check)
```
lacking any other information.  My actual NFS exports look like this:
```
/d/D1           hadar(rw,async,root_squash,no_subtree_check,fsid=1)
```
because I don't want to blindly export file systems to the world.  The fsid number just needs to be unique for each export location, not for each client.

The extra options aren't needed for any Linux NFS server in about 20 yrs.  They are negotiated based on the client and server.

My real problem is with the '*' you are using to allow any clients to have access.  This can slow things down greatly.  Put in the static IP for your firestick. If it doesn't have one, give it one and use that.  DNS lookups can be slow and are used in all sorts of calls that nobody really expects.  For example, **sudo** does DNS lookups because the config file might be setup to support many different host systems with different settings, each limited by the hostname/DNS name.

I've had problems with DNS on Ubuntu for about 15 yrs - all started when they added resolvconf, then when they switched to systemd-resolved and mDNS it got worse.  You probably want to swap the order of your DNS servers in the config file, so the local one is checked first, before hitting the internet. I run a pair of local DNS to prevent this, but that's beyond what most people would want.

BTW, you could also try using the mDNS name rather than the '*' in the exports file.  You'll need to know the firestick's mDNS name .... I have no idea what it may be. Sorry.  Hopefully, it is unique and different from everyone else's in the world.

As for the client-side config, There's probably some menu that shows the NFS settings, right?  I have Roku, but it won't access NFS storage.  Plus, no way would I allow that Roku to be located on the same network as my important systems.  

The FBI has been pretty clear that we shouldn't trust any IoT devices on our networks. They suggest putting them onto a different subnet.  [https://www.fbi.gov/contact-us/field-offices/portland/news/press-releases/tech-tuesday-internet-of-things-iot](https://www.fbi.gov/contact-us/field-offices/portland/news/press-releases/tech-tuesday-internet-of-things-iot) is always a good reminder, if we forget.  Heck, in the last 2 weeks, huge numbers of IoT devices were found, again, to have been hacked and were bring used in botnets.  This stuff isn't going away. It will only get worse and worse for the rest of our lives.

---

### Post by ajgreeny on 2024-10-27
Just to clarify the "Starter for 10" is a question to the two competing teams in this very erudite quiz for UK Universities, the next three questions are to the team from which the person who answered the "Starter" comes.

---

