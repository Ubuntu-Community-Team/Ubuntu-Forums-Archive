---
title: "Saw this story on Digg, but I'd like to know more...."
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2007-07-21
Below is a story I saw on Digg about a guy who helped his brother login to his computer from a long distance away.  There is a command in this story that I'd like to know more info about.... anyway, here's the story:

> I related the below story tonite in our Ubuntu Utah meeting and John asked me to blog the details and the howto.  This is for you buddy :)

A few months ago I was in Chicago to take the Redhat Certified Engineer exam. By day I attended class and by night I studied the book to prepare for the grueling test.  Well, one of the nights I was there (5 day course) my brother calls me in a panic begging me to come fix his computer.  I of course tell him that I’m in Chicago at the moment and not sure what I can do to help. At that I can hear his heart sink, so I ask him what the problem is.

He starts into this sob story about how he has a paper due in the morning but he can’t get logged into his computer.  Apparently his wife dropped something on the keyboard and the number row no longer works, which limits him from logging into his machine (numbers in passwords are good ideas boys and girls!).  He is, by my suggestion, using Ubuntu on his home machine so I know I can save the day.

As he continues this story I use ssh to connect to his machine…

    ssh user@remote-host

..and open the /etc/gdm/gdm.conf file.

vim /etc/gdm/gdm.conf

I change two lines from:

    AutomaticLoginEnable=false

    AutomaticLogin=

to

    AutomaticLoginEnable=true

    AutomaticLogin=username

I save the file and restart the gdm (Gnome Desktop Manager)

    sudo /etc/init.d/gdm restart

By this point he’s finishing his sob story about how he needs to get his paper written or he’s going to fail his class, never graduate and end up being homeless, etc, etc.

I interrupt him to tell him to look at his computer, which is now logged in as his user, never requiring a password or username for access.

The phone goes silent.  I ask if he’s still there. He is.. he’s speechless.

I remind him this is all due to the wonders of Linux and wish him good luck with his paper.. and to tell his friends about the wonders of Ubuntu!

Simple as that.  SSH connection, two commands and a very thankful brother all from 1,400 miles away… and a tutorial on how to activate automagic login on Ubuntu (which is probably not the most secure idea, but you’ve been warned.  Once he got a keyboard replacement I reverted the changes on his machine.)

Ok, the command I want to know about is the SSH command at the top, with the user@remotehost.

I was wanting to know about the syntax.  Say I wanted to connect to my PC using this method over the internet.  Would I have to type something like myusername@(ip address of my computer plus port number as assigned on my router)...

How would I get that all setup?

---

### Post by diablo75 on 2007-07-21
Also, in the comments section after this story on Digg, someone mentions having "DDNS" running on their router.  What is this and how would I use it?

---

### Post by zekopeko on 2007-07-21
for DDNS (Dynamic Domain Network Service) look here

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS). if you are going to use no-ip.com from thispage the client is in synaptic.


> ssh [email]zekopeko@mybox.com[/email] -p 56

zekopeko is the user name you use to log in.
mybox.com is like google.com or ubuntu.com. to get something like that you should read the upper link.
-p 56 means "use port 56 to connect"

for more info open the terminal and type 

```
man ssh
```

man is command for manual. almost all command/programs have them so that you can look for more options for ssh or any other command.

---

