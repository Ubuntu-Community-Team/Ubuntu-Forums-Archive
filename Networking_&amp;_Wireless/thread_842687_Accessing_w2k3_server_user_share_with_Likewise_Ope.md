---
title: "Accessing w2k3 server user share with Likewise Open authentication"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by ic3000 on 2008-06-27
Hi to all i'm a newcomer to the Ubuntu community for the past years i have been using Fedora and windows before that.

The main reason i have started to use Ubuntu is because the way things work for a normal Desktop PC user. They just work fine and there is no need for some kind of waist of time to get things like adobe pdf reader, flash, audio and video plug ins, drivers, etc... things that almost every normal desktop user needs.

I could enumerate many other reasons but that's not what brings me today here! My Question is about Likewise Open and the integration with an existing Windows 2003 Server Active Directory.

The scenario i have is an existing Windows AD infrastructure with a server and about 45 clients. Basically is a network with a domain controller and file server on the same machine(i work in a non profit foundation and we haven't many founds to have more servers)  with windows 2k3 and until a few days ago there where only windows XP connected to the AD on that server.

So a few days ago i decided to give it a try with Ubuntu with Likewise-open authentication against that w2k3 AD server on 2 Desktop clients, my own and the college on the secretary beside me so i can give a windows user some help on the first days of the experience.

After learning all the steps needed to join the Ubuntu client to the W2k3 AD it is very easy and simple no really big problems and things are working ok.

Working so fine that a few of my colleagues are asking why not to have Ubuntu on more clients.

For me it would be a joy to have more open source free computers on the network using Ubuntu, its not possible to use on all because on the server and on some clients we have some proprietary financial application that only support windows but i think that more than half the desktops clients we have can work without windows. I also need that some users could use both OS because sometimes they need to use that financial applications.

Its here that is my major problem and i haven't found a way to do it. My colleagues use different computers that on windows the documents folder is redirected to a share exclusive of that user, so they can access there private documents anywhere on the network.

With Likewise-open i can authenticate a Ubuntu client to the server and i  can manually connect to that folder using smb:// or connect to server, i receive an authentication windows but it works ok.

My question is of this cold be done by automatically when a user logins to a Ubuntu client?

I thought on something like a .gtkbookmarks on the Places menu or a mount on the desktop for that specific user share on the w2k3 server. Maybe a login script for when the user logs in it creates this mount or bookmark.

I really don't know if this is possible or if it is a good idea or there maybe be others ways to do it... i really lost here...

Anyone knows a way to accomplish the objective described?

Sorry for my bad English.

Thanks!

---

