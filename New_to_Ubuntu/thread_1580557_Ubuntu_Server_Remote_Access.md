---
title: "Ubuntu Server Remote Access"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by Zanthir on 2010-09-23
I'm setting up an Ubuntu Server at home, but I want to work on it from my laptop (workstation - kind of) after the initial setup. What applications do you recommend that can allow me to do this? 
 
I'm looking for three things: command line access, file access, and desktop access.
 
To start I guess, what service to you suggest I run to gain remote command line access? And can you point me to a guide to setting it up and using it?
 
I know I can transfer files with the command line, but I prefer GUIs. What is your favorite file transfer service to run on my server, and matching client for use on my laptop?
 
Last, how can I get GUI control of my server from my laptop, as if I was sitting at my server? Can I use LTS from Edubuntu for this?
 
That is all. Thank everyone in advance so much for even reading this post. And thank you even more if you actually reply with some helpful advice.
 
I'm new here on the forums, and to Linux, btw. So be gentle.

---

### Post by HermanAB on 2010-09-23
Server version has SSH installed by default.  So all you need to do is connect to it:
$ ssh user@serveripaddress

You can also install webmin.

---

### Post by Zanthir on 2010-10-05
Thanks. That was great. I am very happy now, and plan on installing webmin, especially since my VNC install has failed. :(

---

