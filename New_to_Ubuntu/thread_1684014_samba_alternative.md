---
title: "samba alternative"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by degarb on 2011-02-08
I am thoroughly convinced there is not one person here that really understands samba.  Firstly, when you click on network or a machine 7 to 10 seconds go by before anything that happens--even on a working samba.  This indicates poor design.  Then the config is **** poorly written.   It is junk when it works.  And fades out from half working to half not.  Also very fragile.

I cannot convert to linux if home networking is not working.  I cannot watch videos over network, share files etc. Dropbox cannot replace a home network.

Okay, blame MS.  Fine, but just write a jar OS independent file sharing for the home user, without the poor design of Samba.  Make it free. 

Samba is the Achilles' heal of linux, at least one.  I have three machines and samba works like crap on 2 and no go on third.   Hundreds of pages of reading and I know no more than on day 1.  Total waste of time. The entire premise of how samba is setup with smb.conf and command lines user add is a mess.

---

### Post by Tyggna on 2011-02-08
And you haven't tried NFS. . . because. . . why?

It's primarily for *nix--but you can pay for windows NFS client software.  It'll be free and readily available on all machines with Linux, and its very easy to use, maintain, and tune for performance.

>  Firstly, when you click on network or a machine 7 to 10 seconds go by before anything that happens--even on a working samba. This indicates poor design.
Have you ever done this with just windows machines?  It's the exact same result.

Here's why: Samba queries every machine available on the network and asks if its the server.  After it's queried them all, if no one is clearly stating that it is the server, then it re-queries them all again to decide which one would make the best server.  That machine is then designated as the server for that given transfer.   

Also, the Samba protocol is a Microsoft standard--not an open standard.  The Samba implementation in Linux is the result of some brilliant reverse-engineering.  You're right, it is designed poorly--in the absence of a designated server.  I believe the reasons for that are largely marketing--Microsoft wants you to buy their server software.  

Again, Samba has nothing to do with Linux in the first place--so how could it be the Achilles heel of it?  Might want to read before you rage next time.

If you want to fix your samba problems, look into making a designated Samba server (either a Microsoft Active Directory server, or the Linux samba server).  I've done that on my home network in the past and it's worked just peachy.

---

### Post by degarb on 2011-02-08
Great tips. I will see what I can do with them.

> And you haven't tried NFS. . . because. . . why?

It's primarily for *nix--but you can pay for windows NFS client software.  It'll be free and readily available on all machines with Linux, and its very easy to use, maintain, and tune for performance.

Interesting, but the pay part for the windows machine lost my interest.

> 

Have you ever done this with just windows machines?  It's the exact same result.

Not on my machines.

> 
Also, the Samba protocol is a Microsoft standard--not an open standard.  The Samba implementation in Linux is the result of some brilliant reverse-engineering.  You're right, it is designed poorly--in the absence of a designated server.  I believe the reasons for that are largely marketing--Microsoft wants you to buy their server software.  

This is the problem, they should just create a new standard with jar or dotnet.  And make it easy and fool proof.


> 
Again, Samba has nothing to do with Linux in the first place--so how could it be the Achilles heel of it?  Might want to read before you rage next time.

Linux is a pile of components.  As is MS.  Any small piece that fails to work, means we must think hard about all alternatives.

[/QUOTE]
If you want to fix your samba problems, look into making a designated Samba server (either a Microsoft Active Directory server, or the Linux samba server).  I've done that on my home network in the past and it's worked just peachy.[/QUOTE]
Most important quote, I think. Not heard of this either. I am taking it, make some master server by some means, then some special clients..... This would be better than standard samba perhaps.

---

### Post by Tyggna on 2011-02-08
> **degarb said:**
> 
This is the problem, they should just create a new standard with jar or dotnet.  And make it easy and fool proof.

No need for a whole new standard--NFS works perfectly fine for small (2-8 computers) to medium (8-200 computers) sized networks.  Most larger networks can still successfully deploy it, but often switch to NAS devices at that point.  Newegg sells NAS devices for home use also--might be worth while to look into one of those as a solution.

Hmm, a java based NFS client wouldn't be too hard to implement.  Wonder if there's an existing project out there?

Looks like there is: [http://j-ftp.sourceforge.net/]("http://j-ftp.sourceforge.net/")  

If you could get that to work on a windows machine, then all your problems would be solved by implementing NFS.  NFS is the open standard that is pretty dog-on easy and nearly fool proof.  First time I set it up required a single package, one line in a config file, and a single command to get it working flawlessly.


Highly recommend the home server though. When I finally set out to try it (with a P3 1ghz laptop that had 256Mb of RAM), most all my frustrations with networking went away throughout the course of about two weeks.  When I set up a media server for my dad, he was absolutely tickled that he could watch his TiVo recorded shows anywhere in the house.

I have since upgraded to a P4 3ghz box with 1Gb of RAM that I picked up at a surplus sale for $20 running arch linux, and it's just humming away in my basement giving me encrypted password-protected internet access to all my files and documents.  Best choice I ever made with my home setup.

Good luck, and if you need any tips for setting up a dedicated box, feel free to pm me.

---

### Post by luvshines on 2011-02-08
Doesn't SFU already provide both NFS client and server for Windows ?

---

### Post by Tyggna on 2011-02-08
> **luvshines said:**
> Doesn't SFU already provide both NFS client and server for Windows ?
Don't know--don't really use windows for anything but my steam games.  I defer to the wisdom of the masses.

---

### Post by Dragonbite on 2011-02-08
> **Tyggna said:**
> Here's why: Samba queries every machine available on the network and asks if its the server.  After it's queried them all, if no one is clearly stating that it is the server, then it re-queries them all again to decide which one would make the best server.  That machine is then designated as the server for that given transfer.   

Is there any way to configure Samba to use a designated system as the server and skip this repeated polling?  Give it a specific computer name or IP address?

My thinking is if the system has one server only, then you *KNOW* that it has to be the server (esp. if you only have 1 client and 1 server ):P )

---

### Post by Tyggna on 2011-02-08
> **Dragonbite said:**
> Is there any way to configure Samba to use a designated system as the server and skip this repeated polling?  Give it a specific computer name or IP address?

My thinking is if the system has one server only, then you *KNOW* that it has to be the server (esp. if you only have 1 client and 1 server ):P )

If it finds a server, then it caches the ip address of it until you reboot the machine, or clear out the netbios cache.  You can actually read this cache in the windows commandline by typing in
nbtstat -r

That'll list any servers that it's communicating with.  Haven't bothered with the Linux client enough (mostly just worked with the servers) to know what the equivalent is--but it's part of the protocol.

---

### Post by OldGrampa on 2012-09-27
Tyggna:    Did you mean netstat -r  

>>> If it finds a server, then it caches the ip address of it until you  reboot the machine, or clear out the netbios cache.  You can actually  read this cache in the windows commandline by typing in
nbtstat -r

---

### Post by Toz on 2012-09-27
This thread is almost 2 years old - probably not much use to the OP anymore. Closing.

---

