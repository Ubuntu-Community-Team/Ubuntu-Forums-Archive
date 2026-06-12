---
title: "Install software from cli"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by zac123 on 2011-05-28
Hi all,

I'm setting up a 10.04 basic server. I want to try an use this server with no GUI installed. 
I'm a total noob when it comes to the CLI. 

What need to do is install some software which is like web based control panel but how on earth can I do this when I can't see what I'm doing?

I have the URL where I can down load the software. 

Also my portable cd drive doesn't appear to be recognised. How to I install the drivers?

Sorry if these are silly questions :-(

Thanks
Zac

---

### Post by audiomick on 2011-05-28
Hi. 
If you haven't already, perhaps you should look through this

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by ikt on 2011-05-28
> **zac123 said:**
> What need to do is install some software which is like web based control panel but how on earth can I do this when I can't see what I'm doing?

Which web based control panel? And is it in the repositories?

---

### Post by zac123 on 2011-05-28
thanks audiomick i'll check that out.
 
no unfortunatly its not in the repros

---

### Post by ikt on 2011-05-28
> **zac123 said:**
> thanks audiomick i'll check that out.
 
no unfortunatly its not in the repros

which web based control panel is it?

is it webmin?

---

### Post by zac123 on 2011-05-28
> **ikt said:**
> which web based control panel is it?
 
is it webmin?
 
 
no its HC8
 
i think i worked it out.
 
i download it like this:
 
wget -c [http://www.nameofsite.com/path/etc.file](http://www.nameofsite.com/path/etc.file)
 
then to unpack it i do this:
 
tar -xzf filename.tar.gz
 
then to install it i have to open the containing folder and do this:
 
./thefile   (to start the install)
 
 
my problem is now that the error keeps coming back that either the file or dir does not exist but i know it does but i'm using ssh Win scp to view the files so i can see its there.
 
thanks, all help is much appreciated
 
zac

---

### Post by audiomick on 2011-05-28
> **zac123 said:**
> 
my problem is now that the error keeps coming back that either the file or dir does not exist but i know it does but i'm using ssh Win scp to view the files so i can see its there.

I'm guessing, but I think you are perhaps in the wrong directory when you are trying to issue the command to start the install. This is just a guess, though. I am not really a huge CLI expert.

When I want to issue a command or whatever pertaining to a file in a particular directory, I often use the command "ls" to see if I am in the right place.

There is something called a "path" that tells the terminal (on a standard gui install) where to look for commands that are issued in the terminal. Apart from the instances covered by this, commands have to be issued from the directory that the file is in that the command pertains to.

If you are getting the error message that the file or directory doesn't exist, it is highly likely, I think, that you are just not in the directory that the file is in.

Use "cd" to move to the right directory. Use "ls" to show the contents of the directory you are in. You should be able to see the name of the file you want to execute the commmand on. When you have established that you are in the right place. try your install command.

---

### Post by 3rdalbum on 2011-05-28
You might benefit from looking at the following things:

[www.linuxcommand.org](www.linuxcommand.org)

Ubuntu Server Guide ([https://help.ubuntu.com/10.04/serverguide/C/serverguide.pdf](https://help.ubuntu.com/10.04/serverguide/C/serverguide.pdf))

As for your second question about your CD drive, you do not need any extra drivers to use an optical drive (CD-ROM, DVD-RW etc). However the disc needs to be '[mounted]("http://en.wikipedia.org/wiki/Mount_(computing)")' before it can be used. When you're running a full desktop environment like Gnome, KDE or XFCE this function is usually done automatically by an integrated program. When you're using a server there's no program running to automatically mount, so you have to do it manually.

The best article I can find on the topic of mounting is this one: [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by webofunni on 2011-05-28
that seems to be a commercial CP. Did you purchase that ? In that case they will help you to install it, I guess. Also are you downloading a compressed file ? In that case you need to extract the content to execute the script.

---

### Post by zac123 on 2011-05-31
> **webofunni said:**
> that seems to be a commercial CP. Did you purchase that ? In that case they will help you to install it, I guess. Also are you downloading a compressed file ? In that case you need to extract the content to execute the script.
 
 
yes they do actually offera free install service but i wanted to achieve it myself as thats the best way for me to learn.
 
 
thanks everyone for your input.
 
it actually turned out to be an issue with the fact my OS is 64bit and the CP was designed for 32bit. so i found a little command which forced it to run/install as 32bit and it all running smoothly.
 
>  
sudo apt-get install linux32 ia32*

 
 
thanks again.
 
zac

---

### Post by webofunni on 2011-05-31
> **zac123 said:**
> yes they do actually offera free install service but i wanted to achieve it myself as thats the best way for me to learn.
 
 
thanks everyone for your input.
 
it actually turned out to be an issue with the fact my OS is 64bit and the CP was designed for 32bit. so i found a little command which forced it to run/install as 32bit and it all running smoothly.
 
thanks again.
 
zac

It always good to share the solution and change the sunject to solved :-)

---

