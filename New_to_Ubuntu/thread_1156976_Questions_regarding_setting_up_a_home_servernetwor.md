---
title: "Questions regarding setting up a home server/network drive"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Scarlath on 2009-05-12
Hello!

Didn't quite know where to put this so I thought the absolute beginner section would be appropriate. :p

Anyway, I've got a spare computer and I thought I'd use it as a type of a home server. I'm not sure whether this is the right thing to call it, so I'll just explain exactly what it is that I want to be able to do: I want to, from any computer (that are using either Ubuntu or Windows) in the household (in the network, obviously), be able to access the files on that computer. I *might* also want to be able to connect to the computer and access the files from any computer outside of the network (over the internet). **Now, how should I achieve this?** I would prefer to use Ubuntu (or Linux at least). Should I use the server edition? As far as I've understood, on Windows (XP) you can simply right-click 'My Computer' to share certain folders through the network. As said though, I dont feel like using Windows and I (sort of) want to be able to do more than that. Hope this all above didn't sound too silly. If it did I'll try to explain it even more I guess... :p

I have been searching Google with no real results (perhaps I'm just using the wrong keywords...) so any help is highly appreciated!

Thanks in advance! :)

---

### Post by gn2 on 2009-05-12
Running an old PC will use up a lot of electricity, you could work out cheaper long term just buying a NAS drive, or an NSLU2.

---

### Post by 3rdalbum on 2009-05-12
Ubuntu Server Edition is command-line only.

It's a piece of cake to set up file sharing on Ubuntu. Install regular Ubuntu on the computer, and then install the "samba" package from the repositories. Right-click the folder you want to share, go to Properties and the Share tab. Choose a name for the share, click "Allow other people to write into this folder" and click "Create Share".

You may need to reboot, but then you might not need to. The server and its share will appear under Places > Network on the clients and the server.

If you want more control, you can install the "system-config-samba" package from Synaptic, which adds System > Administration > Samba. This is a great GUI frontend that gives you more control over users and different shares, and can even create "invisible" shares that are not advertised over the network.

---

### Post by 3rdalbum on 2009-05-12
> **gn2 said:**
> Running an old PC will use up a lot of electricity, you could work out cheaper long term just buying a NAS drive, or an NSLU2.

Agreed, although NASes are a bit expensive and have limited flexibility. I bought a Mini-ITX motherboard and case, running the operating system from a flash drive and sharing files from a WD Green HDD. The same box also does torrents.

---

