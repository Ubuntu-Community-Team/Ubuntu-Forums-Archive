---
title: "FreeNX through port 80?"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by gumbald on 2006-07-18
Not sure where the best place for this was, so here goes...

I've got my Ubuntu machine set up to serve FreeNX and can access it fine behind my router. Before I came to work today, I forwarded port 22 appropriately with the intention of being able to access it here. However, I've now found that I only have port 80 available in and out of the site. Is it possible to connect to my machine at home, and if so, can somebody point me in the right direction?

Any help appreciated,

Jamie

---

### Post by harisund on 2006-07-18
FreeNX works directly of SSH, so basically you are modifying the SSH port. You have a couple of options. 

First, it would be easier if you could just configure your router to forward port 80 external to port 22 of your machine internal. That would solve all problems. 

If you can not do that (for example, your router might forward an external port to the same internal port, and can't do 80 to 22) you have to change the port on which your SSH server is listening. 
(.) Edit the /etc/ssh/sshd_config file. There will be a directive that says "port 22". Change it to 80 :D
(.) Edit the /etc/nxserver/node.conf file. Search for SSH. Somewhere along the 50th line (in my server. I used the FreeNX off Seveas' repos. What about yourself?). There will be a comment (starting with #). Make it look like
SSHD_PORT 80

Remember to restart your SSH server (sudo /etc/init.d/ssh restart). Also just to check, do "sudo netstat -plant | grep LISTEN" to see if your machine is indeed listening on port 80 as you want it to. Then of course do the port forward (Ensure no other software is already listening on port 80 first. Generally a webserver by default)

Once you have done that, go to your work place and connect back home. What is your client operating system? Either way, remember the following: 

If you have installed off seveas' repos, the server is version 1.5 and you will *HAVE* to use client version 1.5 (on any OS). Else it wouldn't work. 

Second, since you are connecting behind a firewall (router) on your client machine at work, you will have to enable an option called "Enable session encryption of all traffic". This would use only port 22 (you will have to change the port of course), otherwise it will try to connect on some arbitrary port. 

Enjoy NX! I simply love it

(If you do a search on the forums for topics by me containing NX, I had posted similar queries, and some good soul answered me. I am just passing it on :) )

---

### Post by gumbald on 2006-07-19
Yeah, that all makes sense, I'd read stuff like that when I was setting up but never paid attention because I didn't seem to need it.

So does that mean that because my workplace is restricted to port 80, I can only have one thing at my end running on it? I know each port can only have one thing, but find it silly that their restriction should restrict me...

---

### Post by harisund on 2006-07-19
Something that surprises me greatly is that you are allowed to access only port 80 from your work place. That means if a website is on some other port, say 8080 for example, you won't be able to access it? It is indeed kind of funny that they allow only port 80 outgoing. That probably means you can't send mail using SMTP etc? 

If that is right, then unfortunately it appears you can access only port 80 on your machine, and so which ever is running on port 80 (currently SSH). 

I am not much into tunnelling yet, so if there is a possible solutions with SSH / TCP IP tunnels, I won't be able to help you out there.

---

### Post by gumbald on 2006-07-19
I work in a school, we find our restrictions annoying but can't do anything because our connection is provided by the local authority. SMTP and maybe one other are available, but that's it. It is a ridiculous situation, but our hands are tied.

I'll just have to use 80 for now, until there's a better way.

---

