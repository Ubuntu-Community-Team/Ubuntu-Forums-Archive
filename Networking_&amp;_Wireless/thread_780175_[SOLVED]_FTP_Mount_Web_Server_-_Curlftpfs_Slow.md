---
title: "[SOLVED] FTP Mount Web Server - Curlftpfs Slow"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by jethin on 2008-05-03
Hey there,

I'm a Web developer and a Ubuntu newbie. I'm looking for a good/easy way to connect to (mount) my Web server and be able to edit the files there. (BTW, it'd be great if someone would bundle this functionality into one of the Web dev packages out there). I'm assuming this means I must mount the server as a local drive and I've been exploring Curlftpfs to do this. Problem is, I can connect, but it's painfully slow -- almost as if Curlftpfs is creating a page file for my (very large) site each time it accesses a folder. It appears to be eating up a lot of cpu too. I also get a permissions error when I try to copy files.

Any thoughts on how to correct this? I'm using Xubuntu 8.04. Also, if you have any suggestions for good (powerful/professional) Web editors I'd love to know them. I've downloaded Quantas but haven't played with it much yet (b/c I can't connect to my server!). Thanks, Jeremy

---

### Post by jethin on 2008-05-17
Just in case some other hapless newbie stumbles upon this post I'm going to solve it myself. Quanta Plus (and others?) does indeed support editing server/remote Web files over persistent ftp (ssh, etc.) connections. I think my confusion about this issues stemmed from two sources:

1. Quanta Plus uses "projects" to manage ftp accounts and server environments. This is different from Homesite (my Windows editor of choice) which just uses the (more intuitive) 'ftp connections' verbiage.

2. Nowhere on the Web or in any documentation did I find any good answer to a simple keyword-laden question like 'Linux Web development package ftp support edit files on remote server'. All of the info I could find seemed to point to mounting a remote server via Curlftpfs, fuse, etc. A confusing process for a new Linux user.

So, here's the rub: Get your hands on a good Web development package and figure out how to establish persistent connections to your Web server within it instead of struggling to mount a server as a local drive in order to edit the files on it. The end.

---

### Post by gnowak on 2008-07-18
Hmm I have used Kate for ftp connections for ages. I am a Kubuntu user. The problem for the application to manage your ftp connection is, that you can easily establish many connections to the server. Some hosting companies disallow more than 4 connections (one.com), which can be a problem when more than one dev is working on a site.

I use curlftpfs, though I find it pretty slow.

---

