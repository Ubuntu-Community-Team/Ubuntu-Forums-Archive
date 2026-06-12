---
title: "Is there a small webserver that can be run as a normal user?"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by encompass on 2007-02-03
Does anyone know of a small webserver that can run from a normal user and be shutoff by that same user?
I need it to integrate into a webcam program I am creating.  Right now the smallest and simplist I can find it this...
[http://www.jibble.org/miniwebserver/](http://www.jibble.org/miniwebserver/)
but it STILL needs root.  Anyone got some other ideas?
It needs only to be able to use a specified port and be a very basic webserver

---

### Post by phossal on 2007-02-03
Why does it have to be small? You can *write* a few hundred lines of Python, Perl or Java code and create a small server that does everything you may need. Speaking of Java, why not run Tomcat from your desktop - on whatever port you want? It supports CGI (and servlets obviously). I can't think of anything *better* or easier to install, and as immediately useful.

---

### Post by encompass on 2007-02-03
I have thought of it... but I need to have it small and simple enough to integrate into one program.  That way it is easier for me to program and I don't have to worry about getting rid of the features I will never use.
The webcam program I am making only needs a very basic of very very basic webservers.  It needs to start on a peruser bases.
I also want to interate into my current programming.  And I don't know the first thing about that kind of webserver programming.
Can it run in one command?  no need to install?

---

### Post by phossal on 2007-02-03
What exactly do you want it to *do?* The simplest practical web server I know of simply opens a port and establishes a socket. That's the *essence*, isn't it? It's just a socket. What features should your little web server have? Are you thinking you're going to *write* and/or *add on* to this server? It's going to be a *part* of your program? In that case, what language are you comfortable with? Python? Perl? Java? C?

---

### Post by encompass on 2007-02-03
I need to server a small java application, from a webpage, over the net,  with a specified port, so that others can see it.
The problem lies in making it small and not having to use root to run the webserver.
Any ideas how this could be produced?
Could I run that aplication I listed above without root?

---

### Post by encompass on 2007-02-03
I program in Python and Java.  Python more than Java.

---

### Post by phossal on 2007-02-03
A small *java* application? Like a *Java Web Start* application? What does the application *do?* There are a million ways to deploy java, as you probably know. I still don't get it.

---

### Post by encompass on 2007-02-03
Let me show you....

---

### Post by phossal on 2007-02-03
I can't click that link for a variety of reasons. Sorry. If you're talented with Java, run **Tomcat** from your desktop. Perhaps your app will integrate smoothly as a Servlet. Consider a web start option. Without seeing source, I can't make additional recommendations. Good luck.

---

### Post by encompass on 2007-02-03
Sigh... Java isn't my thing... Just started learning it this last year.  But I will do my best.

---

### Post by wdaniels on 2007-02-03
I don't see any reason that the webserver should need to be run as root other than the fact that it's trying to bind to port 80 by default.  Ports below 1024 are considered 'privileged' and require root access.  If you alter the webserver to use a port above this range then I expect it will run fine as a normal user.

---

### Post by phossal on 2007-02-03
Even that isn't necessarily true. You can run Tomcat on port 80 as a normal user. The question is what is he trying to do. He's already deploying *links* as he sent one in an email. I'm not sure what he's deploying.

---

### Post by encompass on 2007-02-03
Thanks... I didn't know that... Let me play with it for a while and see if it will do the job.

---

### Post by encompass on 2007-02-03
Looks like webfs does what I need in the most basic way.
Thanks for everyone help.  You don't have to click on the link anymore... it was my live webcam example.  Shows me and the clients side of what I have been working on.
Thanks guys.

---

