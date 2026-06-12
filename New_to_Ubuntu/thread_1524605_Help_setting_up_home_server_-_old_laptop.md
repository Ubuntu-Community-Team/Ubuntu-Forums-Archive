---
title: "Help setting up home server - old laptop"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by pBeseda on 2010-07-05
Hello all Ubuntu geniuses. I've been around the Ubuntu block a few times since 4.10 but I still consider myself a beginner. I've come across an unused computer and some free time and want to try some things out. I want to set up my own server to... serve things.

The machine: 
HP Pavilion ze2000
Mobile AMD Sempron 2800+ (1.60-GHz)
256-MB DDR2 synchronous DRAM
8X DVD±RW/R
(Yes, its a little ancient)

My roommates and I have a working knowledge of computers, networks, the internet, and how to try things without breaking stuff.

Some things I want to do and believe are possible from the server.

1. A small website
2. Media sharing across the local network
3. Printer sharing
4. Manage backups from several machines (two or three main desktops)

From the research I've done, there a lot of different ways to do these different things. I've never done work with servers and want to do it the best way possible.

That means:
-as streamlined and simple to use as possible
-reliable serving capabilities
-minimize risk from attack or infection to the server and our machines on the network
-ability to manage it from my main machine or others on the network

So let me get to my first questions:

One: What operating system should I use?
Two: Server software?
Three: The best way to secure our stuff?
Four: How to network the server and other Windows + Ubuntu machines?

After that, I will have about a million more questions. Most of those the internet will provide, some I might need y'all for.

Lastly, thank you, I know I could spend weekends doing research and trying different set-ups but I hope this will save me some time and effort. The people here have always been super helpful and cool.

/longestpostever

---

### Post by CharlesA on 2010-07-05
Samba would work for sharing files and printers (but I only use it for files, since I've got a network-connected printer already set up).

What OS are the machines that you want to backup run? I've got mine set to throw everything in a folder on the server and then have the server rsync it to an external drive.

---

### Post by pBeseda on 2010-07-05
There would be my 10.04, a Windows 7 machine, and one Windows XP.

That sounds like it would work, just setting up a place for each of us to store backups, and have them sync automatically.

---

### Post by CharlesA on 2010-07-05
Yeah, that would work.

The laptop is a bit old, but you could probably run Ubuntu Desktop on it and use something like Webmin to configure apache, samba, ssh, etc.

The flip side is that you'll have a bit of overhead, but it would work if you don't like editing files manually from a command-line shell.

---

### Post by Hanzerik on 2010-07-05
That's not old...This is Old: [http://hanzerik.servehttp.com/~hanzerik/phpsysinfo/](http://hanzerik.servehttp.com/~hanzerik/phpsysinfo/)  :P

But Yeah, you could do all of those things with that Laptop. I used the Debian NetInstall CD to install mine, and only installed what I needed. I does not have any type of Desktop/X Windows installed, and everything is done from the CLI. I don't use this for anything other then streaming mp3's to computers on my LAN, serving simple www pages, and storing some files via Samba. I don't have a printer so can't help there. And I don't do any backups, other then for this system itself, due to low hard-drive capacity.

WWW = use lhttpd or Apache, whichever you are familiar with
File Sharing for Windows Clients on your LAN = Samba or httpd
File Sharing for Linux Clients on your LAN = NFS/Samba/httpd

---

### Post by theozzlives on 2010-07-05
I use Ubuntu Server 10.04, Ubuntu Desktop 10.04, and Windows 7. My "7" Box does backups to my server automajically. My laptop, using the desktop software, I just create a tarball of my /home and save it on my server. The only thing I backup on the server is my web site.

---

