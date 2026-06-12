---
title: "Initiate an ssh connection from behind a router"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Hospadar on 2009-02-02
I have this great idea to provide some security/theft retrieval for my laptop.

I want to run a cron job that periodically sends my IP address to my home server.  This I know how to do just fine, and would really go a long way in terms of recovering my potentially stolen/lost machine when someone connected to the internet with it.
This I know how to do just fine.

The other thing I'd like to do is to be able to ssh into my laptop after it is potentially stolen/lost to delete saved passwords, sensitive data, etc.  The problem here is that assumedly the machine will almost never connect to the internet directly, and unless the thief is so kind as to forward port 22 to his newly stolen laptop, I won't be able to ssh into it.

Is there any way to initiate a connection from my server to a client if I can login with the client?

Something like this:
[Stolen Laptop] --> [SSH Client] --> [Thief's Router] --> [The Internet] --> [My Home Server]
Now I detect the connection and my server automaticaly connects to the stolen laptop, such that I can do whatever I'd like

---

### Post by jbrown96 on 2009-02-02
You want to make a reverse ssh connection. I found some stuff on Google about it, but I'm lazy so here's the first result and you can go from [here.]("http://articles.techrepublic.com.com/5100-10878_11-5779944.html")

---

### Post by jerome1232 on 2009-02-02
As interesting as this idea is.

Why not fully encrypt the laptop's hard disk drive?

---

### Post by Hospadar on 2009-02-02
Well the reason I'd rather not encrypt the hard drive is that I'd prefer the potential thief use the machine, sending me valuable information about it's whereabout and identity, rather than just popping the hard drive out and wiping it because it's encrypted.  I care a lot more about my nice compy that the data on it.

If it was a work laptop or something like that, I'd absolutely encrypt the whole thing.  But mostly it has notes for classes in it.

Also: either they are dumb enough to not notice my secret data-sending, and I'll be able to protect my data and get the machine, or they are smart enough to notice it, in which case the probably have better ways of stealing people's identity.  (Unless they checked my crontab with the password they would first have to guess, or ran htop all the time and stared at it for hours noticing brief curl and ssh calls) If they did all that, i'd probably have time to get in and do my stuff anyways.

Anywho, jbrown, thanks for the link, I think i'll be able to figure it out from there, I'll probably post a howto somehwhere when I get it all working

---

### Post by mrbiggbrain on 2009-02-02
> **Hospadar said:**
> Well the reason I'd rather not encrypt the hard drive is that I'd prefer the potential thief use the machine, sending me valuable information about it's whereabout and identity, rather than just popping the hard drive out and wiping it because it's encrypted.  I care a lot more about my nice compy that the data on it.

If it was a work laptop or something like that, I'd absolutely encrypt the whole thing.  But mostly it has notes for classes in it.

Also: either they are dumb enough to not notice my secret data-sending, and I'll be able to protect my data and get the machine, or they are smart enough to notice it, in which case the probably have better ways of stealing people's identity.  (Unless they checked my crontab with the password they would first have to guess, or ran htop all the time and stared at it for hours noticing brief curl and ssh calls) If they did all that, i'd probably have time to get in and do my stuff anyways.

Anywho, jbrown, thanks for the link, I think i'll be able to figure it out from there, I'll probably post a howto somehwhere when I get it all working

you have to remember most of the world uses windows, those who know computers are going to restore any PC before turning it on fully (its not even worth cracking passwords when disks are availible)and the few other (not dumb ones) will take it to a pawn show who will likely resotre it before reselling it.

so you have one shot to connect and send out a message, before the avaerage person would jsut resote to windows

---

### Post by Hospadar on 2009-02-04
Well I figured out how to do it!

As suggested, I use a reverse tunnel.  This command that is run on the supposedly stolen laptop (via cron) would be```
ssh -nNT -R 12345:localhost:22 <my server username>@<my server ip>
``` this opens up an ssh tunnel.
Then, on my server, I can do ```
ssh -p 12345 <my laptop username>@localhost
``` to connect to my laptop. The only tricky part is for ssh to actually work in cron, I have to set up ssh so that my laptop can login to my server automatically, not a big deal though, as either I would have control of the machine, and be able to lock down/delete the ssh key, or theif would have already wiped the disk.

I have yet to fully test this in all sorts of situations, but preliminary results are encouraging.

---

### Post by simon.hanna on 2009-05-11
I'm new to the reverse tunnels...
I have a small server and I'd like to have it create the same reverse tunnel every time it boots. I know i can tell cron to do it at a certain time or day, but is there a way to make it execute the command every time the server boots up??!!

---

### Post by Peter09 on 2009-05-11
The only other thing to resolve is leaving port 22 open without a password. Someone twigs that and they can get into your server from the remote machine.

---

