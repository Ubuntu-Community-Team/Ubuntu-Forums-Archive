---
title: "home server"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by cichlidius on 2011-01-15
Hello, I currently have a windows home server.  I was very happy with it until recently.  It was one of those things that I just setup and forgot about.  I had remote access to all my movies, pics, and documents, worked great.  I am interested in setting up a linux server to replace it.  All I really need is the storage and the ability to stream content to my PS3 and Roku.  (I am planning on cancelling my cable) I could even give up the remote access.  Is there something simple that I could just setup and forget about like my WHS.  I don't have the desire to be constantly messing with it and trying to get it to work.  I have searched but pieces of information I have been able to find have been incomplete and convoluted regarding setting one up.  Is there such a solution for my needs?  If so could someone please point me in the direction of where to find a step by step approach to setting one up?  Thanks for any help here.

---

### Post by sandyd on 2011-01-15
> **cichlidius said:**
> Hello, I currently have a windows home server.  I was very happy with it until recently.  It was one of those things that I just setup and forgot about.  I had remote access to all my movies, pics, and documents, worked great.  I am interested in setting up a linux server to replace it.  All I really need is the storage and the ability to stream content to my PS3 and Roku.  (I am planning on cancelling my cable) I could even give up the remote access.  Is there something simple that I could just setup and forget about like my WHS.  I don't have the desire to be constantly messing with it and trying to get it to work.  I have searched but pieces of information I have been able to find have been incomplete and convoluted regarding setting one up.  Is there such a solution for my needs?  If so could someone please point me in the direction of where to find a step by step approach to setting one up?  Thanks for any help here.
is the windows home server from HP?
if it is, its a no-go. Windows Home Servers from HP have a SiS ethernet card which doesn't work with ubuntu.

---

### Post by cichlidius on 2011-01-15
no, I built the box myself and loaded WHS.  Thanks

---

### Post by Paqman on 2011-01-15
Is the box headless? How do you want to administer it?

Ubuntu comes in desktop and server versions. The server version is command line only by default, as servers are normally headless. However, you can very easily add the packages to it to create a graphical environment, and likewise you can add server packages to the desktop.

Alternatively, there are popular tools like Webmin that allow you to remotely administer a server through a browser.

There are a vast amount of high-quality server packages available for Ubuntu. The main problem you're likely to have is selecting which method you want to use, as there are likely to be multiple solutions for achieving any one thing.

---

### Post by cichlidius on 2011-01-15
Thats what I liked about WHS.  the only time I had a monitor on it was when it was setup.  After that I just administered from my other PC's.  It would also do automatic nightly backups.  I understand that its going to be command line, I was just hoping that I could load some GUI initially and just administer it from my laptop.  Could you suggest a tutorial for beginners working with ubuntu that could get me started?  Thanks again

---

### Post by Paqman on 2011-01-16
> **cichlidius said:**
> I understand that its going to be command line, I was just hoping that I could load some GUI initially and just administer it from my laptop.

What OS is the laptop running? And how did you want to administer it? A web interface like Webmin? Command line? Remote desktop into a GUI running on the server?

What sort of tutorial you want really depends on what you want to set up on the server. From the sound of it all you really want to do is set up a file server running something like Samba. I'm not familiar with Roku devices or PS3s, but i'm assuming they'd be happy with Windows networking protocols. A Linux server with Samba installed can share files using the Windows SMB/CIFS protocol. IIRC a file server with Samba is one of the ready-rolled options you can choose when you install using the Alternate CD, so you wouldn't have to install anything yourself.

What about the storage? Are you going to be messing about with RAID/LVM or encryption?

Automated backups on Linux are easily done, what a lot of folks do is set rsync (which is awesome) to run as a cron job.

Sorry to throw so many questions at you, but if we know exactly what you want to set up we can be a lot more help.

---

### Post by cichlidius on 2011-01-16
Thanks Paqman.  My other PC's are running windows 7.  What I would like is to be able to log into the server and administer it from the PC's running 7.  I just remembered that norton is running on both PC's with 7 so i can just use that to accomplish the backups.  I don't feel comfortable enough to be messing about with a command line so I would like to log into some sort of GUI.  Is it possible to get remote access like I was getting with WHS with a linux box?  Thanks for the help

---

### Post by sandyd on 2011-01-16
> **cichlidius said:**
> Thanks Paqman.  My other PC's are running windows 7.  What I would like is to be able to log into the server and administer it from the PC's running 7.  I just remembered that norton is running on both PC's with 7 so i can just use that to accomplish the backups.  I don't feel comfortable enough to be messing about with a command line so I would like to log into some sort of GUI.  Is it possible to get remote access like I was getting with WHS with a linux box?  Thanks for the help
Definately webmin...
go to [http://webmin.org](http://webmin.org)

download the deb package
then after installing, go to [http://localhost:10000](http://localhost:10000)

---

