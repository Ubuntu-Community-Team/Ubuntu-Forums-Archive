---
title: "Installing Ubuntu"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Wovaki on 2009-01-27
Hello!

I am getting ready to install ubuntu on a dual boot, and I would like to know a few things before I start.

1. How much hard drive space, etc. should I give to ubuntu boot?
2. Will this work with Windows Vista?
3. If I decide to get rid of Ubuntu, after I have installed it as a dual boot (with partitioning), how do I do this?
4. Do I need to defrag my comp first if I am installing with Wubi?

Thanks in advance!
Wovaki

---

### Post by Svensk023 on 2009-01-27
well to answer your first question with another question; How big is your HDD and what are you planning to be using linux for? it generally needs 1-2GB for its basic install

Yes i currently dual-boot with windows vista and it works just fine, you just get an option to select what OS you would like to run at the beginning of your boot.

i cant think of an answer to your third question off the top of my head,but since vista uses the entire drive, partitioning your HDD is permanent, unless you re-format your entire drive with a windows disc down the road.

If u decide to use wubi. it would be wise to defrag your HDD prior to installation.

---

### Post by Wovaki on 2009-01-27
My HDD is aprox. 200+ GB

---

### Post by Svensk023 on 2009-01-27
then I would give it about 15GB that should compensate for casual use for some time, especially if you plan to be listening to most of your music in vista.

---

### Post by Wovaki on 2009-01-27
Give Ubuntu or Vista 15GB?

I'm planning on having music and video and stuff like that on Linux.

---

### Post by fugaki on 2009-01-27
ubuntu.
you will need to use part of that for swap as well, unless you want the whole 15G for storage in ubuntu

---

### Post by Wovaki on 2009-01-27
See I don't understand this swap stuff.

How many different things is there I need, and what should I put for each of them?

Also with Wubi, if I download an infected (virus) file, such as music, on Wubi, will that virus affect Windows? Like if I got a keylogger or something, it won't work right?

Thanks

---

### Post by pedja_portugalac on 2009-01-27
> **Wovaki said:**
> My HDD is aprox. 200+ GB

I presume you'll like very much Linux and Ubuntu. Every day you'll use it more and more, like lot of us, till the day you switch without return to microsoft. So I suggest you to free from vista at least half of your disk space but you don't have to if don't want. Ubuntu will run even on 10GB. I suggest you also to defragment first and then using Vista free the space for Ubuntu. After that, installation process is easy.

PS. From today on, there is very nice book about Ubuntu for free download. Maybe you'll prefer to read it first. Here's the link for download:

[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

---

### Post by Svensk023 on 2009-01-27
alrighty, well its really up to you, if i was in your shoes i would either just partition the HDD 50/50, if you plan on adding media onto your ubuntu partition,

also why we are talking about it im going to save you some possible heart ache in the future.

during the installation choose to "manually partition" your drive and here is how, in my opinion, you should partition your drive

make a swap partition at the end of your HDD for about 2GB-4GB

mount a ext3 partition at / 
Give this partition about 8GB of space

mount a ext3 partition at /home 
Give this partition the rest of the space that youre willing to spend on your Ubuntu OS

by doing this you can keep all your personal settings, music, videos ect. if u need to freshly install the system.

---

### Post by mkvnmtr on 2009-01-27
If you are going to use wibe you don't need to do anything to your partitions. It will install inside of windows. It will only take the space of what software you download for it.

---

### Post by Svensk023 on 2009-01-27
> **mkvnmtr said:**
> If you are going to use wibe you don't need to do anything to your partitions. It will install inside of windows. It will only take the space of what software you download for it.

ya this is true, you can try out Ubuntu this way, it will run slightly slower though, and if you decide you do not like it, you can just uninstall it in vista

But Ubuntu is a really great OS, i am sure you will love it

---

### Post by Wovaki on 2009-01-27
I know, I have been using Wubi for about a month, but right now my only internet connection is Dial up, and I can't get Ubuntu to work on it.

When I get high speed I think I will partition my drive.

But I just wanted to make sure that using Wubi was as safe as Partitioning my HDD.

And if I partition my drive, there is no way to remove Ubuntu without reinstalling Windows?

Thanks!

---

