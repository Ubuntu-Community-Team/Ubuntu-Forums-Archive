---
title: "Newb question about file transfer"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by Corfy on 2007-03-14
This is a newb question, I know, but in many ways, I am still very much a newb when it comes to Linux. I'm learning, but I'm learning as I go along. I also hope this is the right place to ask.

I have about 3-4 GB of files (pictures, documents, video clips, etc.) on my laptop (running Kubuntu 6.10) that I would like to transfer to my desktop (also running Kubuntu 6.10). They are both connected to my in-home network.

What is an easy way of going about doing that?

In Windows (sorry, I really don't mean to bring up the "W" word, but it is all I have experience with), I would set up a shared folder on the desktop, then connect to that folder from my laptop essentially as a mapped drive and move the files over. But I don't know what the procedure is with Linux. And chances are, it is a lot simpler in Linux (for that matter, it may be a lot simpler in Windows, but I don't care about that now). But when I don't know what I'm doing, anything is difficult. I've just never tried to get my two Kubuntu computers to talk to each other beyond "ping".

I should point out that, while I am running Kubuntu, I have both Gnome and KDE installed on both computers. So if I need a Gnome utility, I probably either have it or I can get it.

---

### Post by Malac on 2007-03-14
This is for Gnome but the procedure should be similar.
Right-click on the folder you want to transfer files from and choose "Share Folder". 
You should be asked for the admin password.
Then presented with a Window asking you what share name and whether you want to use NFS or Samba, as it's Kubuntu on both machines I'd use NFS.

You should then be able to navigate to that folder on the other machine using the Network button in the file manager.

Hope this helps.

---

### Post by Corfy on 2007-03-14
I don't know... that is pretty simple. Isn't there a way to make it, like, 10 times more difficult so I get to keep the Windows experience? I might get spoiled by this Linux thing.* 

Thanks for your help. I will try that tonight and let you know how it goes.




*-Actually, I was spoiled months ago, which is why I don't use Windows at home anymore.

---

### Post by Grout58 on 2007-03-14
I would like to do the same thing only on my Dapper LAMP server, how can I make a share on the CLI?

---

### Post by gus sett on 2007-03-14
look up ftp for network transfers, but also note that 4.7 GB DVDs are available. :arrow: 

> **Corfy said:**
> This is a newb question, I know, but in many ways, I am still very much a newb when it comes to Linux. I'm learning, but I'm learning as I go along. I also hope this is the right place to ask.

I have about 3-4 GB of files (pictures, documents, video clips, etc.) on my laptop (running Kubuntu 6.10) that I would like to transfer to my desktop (also running Kubuntu 6.10). They are both connected to my in-home network.

What is an easy way of going about doing that?

In Windows (sorry, I really don't mean to bring up the "W" word, but it is all I have experience with), I would set up a shared folder on the desktop, then connect to that folder from my laptop essentially as a mapped drive and move the files over. But I don't know what the procedure is with Linux. And chances are, it is a lot simpler in Linux (for that matter, it may be a lot simpler in Windows, but I don't care about that now). But when I don't know what I'm doing, anything is difficult. I've just never tried to get my two Kubuntu computers to talk to each other beyond "ping".

I should point out that, while I am running Kubuntu, I have both Gnome and KDE installed on both computers. So if I need a Gnome utility, I probably either have it or I can get it.

---

### Post by Corfy on 2007-03-14
> **gus sett said:**
> note that 4.7 GB DVDs are available. :arrow:

Well, if you want to send me an external DVD burner for my laptop, I will be happy to use it. Or if you want, I can buy one and charge it to you.



Anyway, I seem to be missing something. I have shared the folder (after installing NFS services), but I can't seem to be able to connect to anything on that computer. I can't even get any indication that there is anything on that computer to connect to. Do I need something else running?

---

### Post by Malac on 2007-03-15
> **Corfy said:**
> Anyway, I seem to be missing something. I have shared the folder (after installing NFS services), but I can't seem to be able to connect to anything on that computer. I can't even get any indication that there is anything on that computer to connect to. Do I need something else running?
Have you installed nfs on both systems and do you have a user account on both machines with the same name/password combination?

---

