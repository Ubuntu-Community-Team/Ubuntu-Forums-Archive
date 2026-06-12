---
title: "VNC over the internet with a free DNS"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by f37u5g0d on 2008-06-24
I am trying to set up vnc over the internet so that with a windows client I can log into my ubuntu desktop over the internet.  I have a router with multiple machines set up on the server side of things.  I was following the tutorial on vnc over the internet in the ubuntu community documentation and I got to the part about me needing a static ip (seen by the outside world) and it suggested dydns.com which I tried to join and couldn't get a confirmation email.  Instead of struggle with that I found another website called [http://freedns.afraid.org/](http://freedns.afraid.org/) .  I got an account and it is working but I now have no idea what I am doing.  Ultimately I want to connect to my ubuntu machine from a windows client in a web browser like firefox over the internet.  Can anyone help me?

---

### Post by dmizer on 2008-06-24
what is your ultimate goal?  vnc is probably way more than you really need, and it's not generally fast enough to get any real work done.

for most situations, your best bet is probably just a simple ssh session with x forwarding.  this can be done with a windows based ssh client like [cygwin](http://www.cygwin.com/)

---

### Post by f37u5g0d on 2008-06-24
My ultimate goal is to connect to my ubuntu computer (it's at home) from a windows client (at work, or anywhere else in the world) without installing any software (hence through firefox).  From what I understand ssh is just a special, more secure connection.  Is there a difference between ssh and ssh tunneling?  What is x forwarding?  I have used vnc over my local network and it is fast enough for my purposes but if this method faster than why not?  I will need some help though :(

---

### Post by dmizer on 2008-06-24
vnc over your local network will be at least 10X faster than vnc over the internet. with vnc, you need to transfer massive amounts of data across the internet, so unless you have ultra fast connections at both your home and your remote location, vnc will most likely be unusable.

the difference between ssh and vnc is that, with ssh, you are only forwarding the one gui application you want to use.  with vnc, you're forwarding the entire desktop. so, with vnc, before you've even opened an application, your bandwidth is consumed.

the difference between ssh and ssh tunneling is that ssh gives you full command line access to your computer, just as if you were sitting right in front of it with a terminal open.  ssh tunneling allows another application (like vnc, or ftp) to make use of the encryption capability of ssh in order to secure connections that would otherwise be very insecure.

using ssh with x forwarding ("x" is the linux gui environment), will require a windows client.  but windows ssh clients (like cygwin) do not need to be installed.  you can load them on a usb key and run them from the key without installing locally.

---

### Post by f37u5g0d on 2008-06-25
So then does x forwarding only "forward" the windows or applications that I choose to run instead of the whole desktop?  cygwin will let me run linux apps on windows over ssh?  And last just making sure.  All I need on the ubuntu server is the openssh package?

---

### Post by dmizer on 2008-06-25
> **f37u5g0d said:**
> So then does x forwarding only "forward" the windows or applications that I choose to run instead of the whole desktop?
essentially, yes.

> **f37u5g0d said:**
> cygwin will let me run linux apps on windows over ssh?
yes.

> **f37u5g0d said:**
> And last just making sure.  All I need on the ubuntu server is the openssh package?
you will need to install the openssh-server package, but no further configuration is necessary.  just install it, and it will be functional.

the only other thing you'll need to do is make sure to configure your router so that port 22 is forwarded to your server.

before you do this, you should really think about security.  here's a good thread on how to secure openssh-server: [http://ubuntuforums.org/showthread.php?t=30709](http://ubuntuforums.org/showthread.php?t=30709)

---

### Post by f37u5g0d on 2008-07-10
I am now happily x-forwarding but I am a bit confused.  When I use the command ssh -X user@servername and type in the password I get a prompt from that computer.  The cli is entirely based on the home computer.  I see it's files only none from this (the client) computer.  But when I run a program (x-forwarding) it uses the settings and files from this (the client) computer.  For example if I type firefox& it opens a firefox window that has the favorites of this (client) computer!  Is this how it is supposed to work?  If so what is the point of x-forwarding at all?

---

### Post by Prefix100 on 2008-07-10
Can you be more specific with what you want?

Why do you want to access your home computer from work?

If its to get files, stream music etc, through firefox/ie then just set-up a LAMP server on your home computer, move the files/music etc to the webserver folder and you will be able to access the files from across the world.

I do this for college so I can get my work and listen to music with ease.

---

### Post by f37u5g0d on 2008-07-10
Well lets say that I want to access my firefox history and bookmarks from a client computer.  With x-forwarding I thought I was supposed to be able to open firefox on the server on see it on the client.  In other words run firefox with all my history/bookmarks of the server from a client.  What I am confused about is this.

I run the command ssh -X username@servername
I get a cli as if I am logged into my server (i.e. username@sever's name on server's local network)
I can then look at the servers filesystem (all well and good)
If I then run the firefox command it opens firefox but it is the firefox of the client computer.  All of the settings history/bookmarks/whatever else is of the client computer.  How is this any different than just running firefox on the client without connecting with ssh at all?  I get the exact same result if I just open a terminal on the client and type firefox as I do with the above described process.

I just noticed that firefox is the only program that does this!  If I run xclock both through ssh on the server (x forwarded) and on the client they report different times!  (off from each other by 2 minutes)  Also rhythmbox has a different library if I x-forward it from the server then when I open it from the client.  Also I noticed that I cannot open my servers bookmarks file in /home/ed/.mozilla/firefox/profilename.default on the server.  It loads a blank html page.

---

### Post by dmizer on 2008-07-11
use the command:
```
firefox -no-remote
```
to force firefox to use the remote settings.

also, make sure firefox is not already running.
```
sudo killall firefox
```

---

