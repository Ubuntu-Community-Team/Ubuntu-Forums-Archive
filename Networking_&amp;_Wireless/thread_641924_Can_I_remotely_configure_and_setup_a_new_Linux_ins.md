---
title: "Can I remotely configure and setup a new Linux install from off-site?"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by tuproxy on 2007-12-16
I want to be able to work on my installation from a remote site, when I'm out of the office.  I'm figuring that I should be able to login via SSH, is that correct?

Once I do that I should be able to run all CL options to install whatever I want.?

Is this correct?  Can I do anything remotely as long as I have OpenSSH server setup?

I want to know if this is possible so I can have other people help setup my system.  Thanks:)

---

### Post by mjpolifka on 2007-12-16
Yes, openssh will allow you to access your system from anywhere (assuming you set up your router to forward port 22 to that machine).  You can also use the ssh -X command to allow you to view X Window programs (like firefox, gaim, and nautilus) on a remote computer.  However if you want to do this from a windows machine you'll also need xming in addition to the putty ssh client.

What you asked seems sort of vague, if you have any specific questions please post them. (such as how to download/setup openssh)

---

### Post by tuproxy on 2007-12-16
Thanks for the info. I have setup OpenSSH server before and have successfully ssh'd into the machine. I've just never done it from offsite through the router.  This is where I get hung up.  I understand that I need to forward port 22 to my Linux box's IP.  

I guess I get stuck when I need to configure the client.  Do I just put my home IP addy in and will it automatically go to my linux box?  Do I do xxx.xxx.xxx.xxx/22?  

I've never used the ssh -x command and I think that is what I was looking for.  I wanted to know how to know how to use the graphical interface via a remote connection. This is where I need the help. Thanks:)

---

