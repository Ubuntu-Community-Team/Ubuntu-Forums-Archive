---
title: "Configuring Ubuntu Server"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by Moorey on 2011-06-16
Hi

Is there any easy way to learn the linux commands?? I want to learn Ubuntu but i am also an IT student goin for CompTia A+ therefore not much time to learn both. My job is a IT technician (For Windows) and the reason i want to learn Linux is my boss has given me the option that if I'm knowledgeable enough within time, Linux will be installed on all 60 PC's and the £££ that is now payed out to Microsoft for software and user access rights would then be in my pocket rather than Bill Gates.
I know you have to start at the bottom but i simply cant get my head round any of it.

Thanks

---

### Post by kukker32 on 2011-06-16
You want a list of all available commands in ubuntu?
or you want help setting up an ubuntu server?

i learned the ubuntu commands the more i began using ubuntu..

can you please be some more specific what you want help with?

---

### Post by Moorey on 2011-06-16
I want to be able to setup/configure server but do u think i am best knowing in and outs of desktop first or, just jump straight into the command line. I know some commands but not really enough to start a little network of my own for practice although, I have all the gear that is needed here at work.

Thanks

---

### Post by kukker32 on 2011-06-16
I don't think you can't jump straight on settiing up an ubuntu server without any knowledge of the desktop version..

so i recommend you to get some experience, with it first..

but you could of course also try it out now and get your experience from setting up the server, but would possibly cause you some more troubles.. 

but in the end you'll have the last word.

---

### Post by mastablasta on 2011-06-16
Both desktop and server use same commands. major difference is preinstalled software. it would be good to get some basics about linux first then try out the desktop and then jump into commands.
 
basic stuff is in Ubuntu manual free e-book (or a bit older in Ubuntu pocket guide free e-book).
 
linux commands are best explained here (free e-book available on site): [http://linuxcommand.org/](http://linuxcommand.org/)
 
It guides you through the command line with various tasks.
 
once you get through the basics try to up a server. you can do it from desktop installation.

---

### Post by Moorey on 2011-06-16
Thank you I will play about with desktop some more before I try to set up a server and will be back on when I know abit more about the OS

---

### Post by collisionystm on 2011-06-16
I have this book. Unix in a nutshell. 

Here it is on google books. You can see alot of it.

[http://books.google.com/books?id=YkNiiLupct4C&printsec=frontcover#v=onepage&q&f=false](http://books.google.com/books?id=YkNiiLupct4C&printsec=frontcover#v=onepage&q&f=false)

---

### Post by nothingspecial on 2011-06-16
Heywood?

Get down to Bury, hop on the tram to Timperley, find the nearest Pub and I'll tell you all about it if you're buying?

Seriously, if your Boss is going to install linux on all the PCs then you are going to have to know your way around both the desktop and command line anyway.

Start with the Desktop and mess about with a few commands.

---

### Post by alphacrucis2 on 2011-06-16
> **Moorey said:**
> Thank you I will play about with desktop some more before I try to set up a server and will be back on when I know abit more about the OS


You probably want to look into setting up some of the usual server software. A common combination to get started with a web server is Apache2, MySql and PHP. There is also lots of choices for email, news servers, file servers. This stuff can all be run on a normal desktop or laptop as well as a dedicated server type machine.

---

### Post by Moorey on 2011-07-01
I understand that the grub boot loader is so dual boot can be done. But is there anymore to it than that?????

---

### Post by nothingspecial on 2011-07-01
> **Moorey said:**
> I understand that the grub boot loader is so dual boot can be done. But is there anymore to it than that?????

Yeah, a lot more, what do you want to know?

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Moorey on 2011-07-01
Well im just trying to understand the basics at the min so almost anything baffles my head!!!! Where do you start in those situations????

---

### Post by Moorey on 2011-07-01
Could anyone tell me how I save files on my server remotely. Am i missing something, iv turned the firewall off, searched the web to see if there a syntax but no joy.........YET!!!!!!

---

### Post by nothingspecial on 2011-07-01
linux to linux?

---

### Post by SeijiSensei on 2011-07-01
1) Export shares off the server using NFS to *nix machines or Samba to Windows machines.

2) Use scp to copy files over a secure (SSH) connection.

---

### Post by Moorey on 2011-07-01
Yes Linux to Linux... Is the reason because it is actually running over a windows network here at work. Or is there just a simple answer to this like a command that will then let me cut and paste files over the network within the GUI???

---

### Post by nothingspecial on 2011-07-01
I take it you are still experimenting, in which case we'll do this the quick way.

You need to install openssh-server on the server if it isn't there already.

Then on the other computer do this

Open the file browser and in it's menu go file > connect to server

In the top box choose ssh

In the next one, put your username and the ip address of the server.

In the folder box you can put what ever you like but try /

Then click connect.

You'll have to type your password on the server.

---

### Post by Moorey on 2011-07-01
Haha Yes still experimenting. Thanks for that, will have ago now and see what other problems I come up with along the way. Ill be in touch :p

---

### Post by Moorey on 2011-07-07
I'm trying to connect my client to my server and succeeded a few days ago. But since i am still experimenting i decided to install the GUI on the server, once installed i then changed my mind and reinstalled server so the command line was my only interface. But now doing so I'm am not sure how i did it last time and my client wont connect, i have my static IP address on both machines and also have open-ssh installed on both, and i keep getting a message saying "Cannot display location -sftp://192.168.xxx.xxx"
                       "Host Key Verification Failed"

I am missing something and really cant think what i am doing wrong!!!!!!!     #-o

---

