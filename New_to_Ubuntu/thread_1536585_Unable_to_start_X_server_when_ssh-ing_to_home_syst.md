---
title: "Unable to start X server when ssh-ing to home system"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by rajnikhil on 2010-07-22
Hi I have 10.04 on my home system and I'm trying to ssh into that system from my office(8.04). Now I'm able to ssh to the home system but I'm not able to start X server. I've tried the following methods
1. startx
2. start gdm
3. xinit

but each of them throw the following error
'X: user not authorized to run the X server, aborting.'

Can someone help me out in this. Is there something I'm doing wrong or have missed out on.

Thanks in advance!!!

---

### Post by aeiah on 2010-07-22
the simple answer is: its the way ssh is set up.

you can export X over ssh though - either a specific program or an entire desktop, or you can tunnel VNC through ssh. it depends what you want to accomplish. why do you want to start the x server over ssh?


if you want to see your home computer's desktop, look into either ubuntus desktop sharing features or VNC

---

### Post by rajnikhil on 2010-07-24
> **aeiah said:**
> the simple answer is: its the way ssh is set up.

you can export X over ssh though - either a specific program or an entire desktop, or you can tunnel VNC through ssh. it depends what you want to accomplish. why do you want to start the x server over ssh?


if you want to see your home computer's desktop, look into either ubuntus desktop sharing features or VNC
Hi aeiah,
Firstly let me confess I'm not so knowledgeable in the SSH thing so the points of export X over ssh and ubuntu desktop sharing features went right over my head. And coming to VNC, I've heard its not really secure and so I'm a little sceptical about using it.

Coming to what I want to do by SSHing to my home system, for the moment I only want to be able to control my home system from my office system and as I'm not very familiar with terminal commands (and they are difficult to remember) I want to start X over SSH so that I can do it via GUI. And in a few months time I'm planning to start a project of my own for which I would be mostly using open office spreadsheet and word and would like to store files on to my home system.

I hope you or someone else can provide more help on how to do this over SSH or any other better (i.e. easy and secure) way.

---

