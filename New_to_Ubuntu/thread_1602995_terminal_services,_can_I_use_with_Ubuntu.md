---
title: "terminal services, can I use with Ubuntu?"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by digitography on 2010-10-22
Running a 10.10 desktop, and regularly and quite easily connect to windows computers using the Terminal Services Client.
I now have some other Ubuntu 10.10 boxes and want to do the same thing, however I just cannot connect.
I have setup remote desktop on the target machine, and can connect with Vinagre desktop viewer so long as I am already logged on to the target, but that's not really what I want.
any suggestions as to how to setup terminal services so I can connect and login?

as always thanks in advance.

---

### Post by Brandon Williams on 2010-10-22
You should be able to start an independent vncserver instance that is not associated with an active login session on the host computer. This can be a bit of a pain to set up, because the most common desktop environments (gnome, kde, and xfce) don't support multiple concurrent login session for the same user very well. Initially, it's easiest to use a different window manager for the vncserver session than you use for your standard login environment on the machine.

To start a stand-alone vncserver session, simply log in to the machine using ssh and run vncserver on the command line. This will start the vncserver as a separate display, and you can use vinagre on the client machine to connect to it. I use vnc4server, but I think this method should work with vino, too.

Use 'man vncserver' to get more information about command line options, configuration, etc.

---

### Post by digitography on 2010-10-22
Thanks 
I posted in absolute beginners cos as far as linux is concerned I am
so my next question is SSH? what is that and how do I get into it?

---

### Post by alphacrucis2 on 2010-10-22
> **digitography said:**
> Thanks 
I posted in absolute beginners cos as far as linux is concerned I am
so my next question is SSH? what is that and how do I get into it?


Secure Shell. There is an ssh client called putty that I used for a long time on Windows so I also use it on Linux. What I find to be a really useful feature is that any text you highlight with the mouse in putty is automatically stored in the copy buffer. Of course ssh can be used to encapsulate other protocols such as ftp and even X windows sessions. In that case the ssh is just being used as way of securing the ftp or other protocol. You can use OpenSSH server to handle the server side of things on Ubuntu.

[http://www.openssh.com/]("http://www.openssh.com/")

---

### Post by digitography on 2010-10-25
OK I installed Putty
now when I try to connect to the target machine I get "connection refused".
My limited knowledge tells me that I need to do something on the target to make this work, but what I do not know.

---

### Post by alphacrucis2 on 2010-10-25
> **digitography said:**
> OK I installed Putty
now when I try to connect to the target machine I get "connection refused".
My limited knowledge tells me that I need to do something on the target to make this work, but what I do not know.

That usually means that there is no SSH server active on the destination machine. Did you install the SSH server and start it?

---

### Post by digitography on 2010-10-26
OK thanks
I now have ssh and openssh-server installed on the target machine, but how do I kick it off?

---

