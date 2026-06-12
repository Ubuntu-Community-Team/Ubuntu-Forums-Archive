---
title: "A Simple File Server"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by cbk1994 on 2007-04-05
Hi everybody, and thanks for the help in advance. I'll get straight to the point -- I need to set up a file sharing server where I can add multiple (around 5-10, if that matters?) users, each with permission to different folders. For example, USER1 has a password of 'bike'. He's an admin, so his permissions are basicly *. USER2 has another password, but is a normal user, so has permissions to say ... /Users/USER2/ and /PUBLIC/ (Making those folder names up ... I'll need to be name folders basicly anything.) I'm using edubuntu, and I've read this is the best for making servers like this simply. I really need help, I have no clue. I'll have several Macs, several Windows, and two Linux that will all need to be able to connect to this. I'm using a Linksys router. I'd prefer it if there were no big wires running out to every single room with a computer. I'm pretty sure this is possible if this computer has wireless.

Thanks for all the help, I love you all!
Chris K.

PS: I'm a Mac geek, need to set some stuff up. I always thought Mac was the best OS, but I was wrong. Ubunut/Kubuntu/Edubuntu is much better than Mac. I love the educational tools in edubuntu aswell, planning on eventually setting one up in my classroom.

---

### Post by Kaput1982 on 2007-04-05
Samba will do what you want.  It allows you to set up shares on a linux box that other PC and laptops can access.  This is a link to the official [[COLOR="Blue"]Samba HowTo[/COLOR]]("http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/").  You may have to install Samba on your machine first.  If you need more help I can get you a copy of my smb.conf file

---

### Post by cbk1994 on 2007-04-05
I have no idea how to do that. Is there any sort of GUI thing? I can't get SWAT to work, because it's not installed, and I can find nowhere to download it.

---

### Post by dmizer on 2007-04-05
the first link in my sig provides a more clearcut (in my opinion) way of configuring the samba server.

unfortunately (for new useres at least), you're going to find that most server application configuration is going to be done via conf files at the command line level.  this is because a majority of linux server configurations never have a gui installed.

this may seem like a real pain at first, but remember ... this is server configuration.  furthermore, it's commercial grade server configuration, not windows file and printer sharing, and certainly not workstation configuration.  even in windows, for enterprise server configuration, there are many things done at the command line level.

working with the command line is a price you pay in order to have a superior server configuration.

---

### Post by cbk1994 on 2007-04-06
I followed that nice tutorial, and everything is set up nicely. The only problem is ... it's not in the network! I have this computer connected to my MacBook Pro which has internet sharing (connected via ethernet). I can't even access the network from my MacBook. How can I find the LAN IP of this? Thanks.

Chris K.

---

### Post by dmizer on 2007-04-06
yeah ... i've had difficulty with mac's being able to browse samba shares hosted by linux.  not sure why.

if you have a windows machine in your network, you should be able to ping your ubuntu box.  so just ping whatever name you used next to "netbios name" in your smb.conf file.  for example, the relevant portion of the smb.conf file on my server looks like this:
```
[global]
    ; General server settings
    netbios name = tsubame
    server string =
    workgroup = denshya
```
to get the actual ip of my samba server, i would ping tsubame.

but since you're internet connection sharing via a mac book, there could be other issues at work here too.  if it's at all possible, i'm thinking that you'll have many of your problems solved by using a router instead of an internet connection sharing setup.

---

### Post by cbk1994 on 2007-04-06
Okay, I'll shut down my computer right now and try to get the wireless card in. Linux does support that, right ...? Sorry, really new.

---

### Post by dmizer on 2007-04-07
> **cbk1994 said:**
> Okay, I'll shut down my computer right now and try to get the wireless card in. Linux does support that, right ...? Sorry, really new.

to be honest, that's something of a craps shoot.  it really depends on what wireless card you have and what chipset it has inside it.  for the most part, i've only been successful with the cards i own.

---

