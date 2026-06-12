---
title: "Domain Controller replacement?"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by okdewit on 2008-09-20
Hey fellow Ubuntu users!

First of all, I'm pretty new to these forums, so who am I?

> I am a dutch IT-guy, I deploy (small to medium) business networks. Almost always just with MS windows 2003 and XP workstations, just the "mainstream" setups with office '07 / exchange etc, etc...

The company I work for is REALLY MS oriented, and since the day I started there I'm trying to educate my collegues in the direction of alternatives.

I'm not a "hater"/"fanboy" of any OS, but I think one should always be open minded, and create a mix of systems with the best of all worlds.

Personally, I have always been attracted to Debian and later Ubuntu because it is so beautifull (not as in spacey desktop effects, but in its philosophy and inner workings).

Now I hope someone could help me or point me in a direction.
I have read a lot about Samba as a domain controller, and I would love to experiment using Samba on Ubuntu server as a temporary replacement for a broken Windows 2003 Small Business Server. Would it be possible to create an ubuntu based disc (CD/DVD) that could feature a (either text or gui) wizard-process, to create a temporary replacement DC?

Installing Windows 2003 and configuring Active Directory takes up a lot of time, so when a server gets fried in the afternoon, the business is often without a DC during a big part of the next day. Changing the domain name requires a complete reinstall of the server, so we can't react fast to these emergencies.

And I would like to prove to my company that linux is great for small companies too, because I have seen beautifull implementations. 

If anyone could point me in some direction, I would be really thankful! I have experimented with Samba already, but editing the smb.conf takes some time too, so I'm looking for a way to migrate from AD to Samba as fast as possible :D

Would there also be a solution for mail in such a setup? No complete exchange replacement, just something to handle mail quickly while a new exchange server is configured.

Thanks a lot!

---

### Post by calraith on 2008-09-20
You don't ask for much, huh?  ;)

Anyway, I found an interesting [howto](http://www.howtoforge.com/installing-zivios-server-on-ubuntu) this morning for a project called [Zivios](http://www.zivios.org/).  I'd never used Zivios, but just from my brief browsing, it appears to turn Ubuntu into an LDAP controller with a web-based Active Directory Users & Computers, DNS, and so forth.  Maybe it's what you're looking for?

---

### Post by Iowan on 2008-09-20
Check this [howtoforge]("http://www.howtoforge.com/howtos/linux/ubuntu") link..  They have several "perfect server" articles.

---

### Post by okdewit on 2008-09-20
Thanks a lot for the quick replies!

I'm going to experiment tomorrow with these suggestions (it is 0:30 here now :P)

I didn't expect to get an answer so soon :)

---

### Post by frk2 on 2008-09-22
It will work as much more than a simple domain controller. Through a Samba plugin, we can tie in all functions of Samba to Zivios, furthermore - It automatically enables the smbk5pwd module which means that password changes from Windows will reset your ldap and kerberos passwords automatically.

The 'service' part currently does not provide amazing functionality but it lets you put up a Samba domain controller, add/remove shares, control individual users password/netlogon settings, etc. Things like advanced ACLs on shares, etc (and even smart card integration) is in the works.

And yes- the philosophy behind Zivios is that plugin developers manage the likes of 'smb.conf' for you, and not you directly.

Check out the project and feel free to leave comments on our mailing lists!

---

### Post by chongzivalve0809 on 2008-09-22
a professional [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) China manufactuer and supplier,established in 1983The main product is:cast steel [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm),forged steel gate valve ,pressure seal gate valve,plate [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm).  BFV Valve also possess the test lab with various of examination equipment for material chemical composition analysis, physical property and non-destructive examinat-ions such as RT,UT,MT,PT .[gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) manufacturer website:[www.valvesupplier.net/forged-steel-gate-valves.htm](http://www.valvesupplier.net/forged-steel-gate-valves.htm)

---

