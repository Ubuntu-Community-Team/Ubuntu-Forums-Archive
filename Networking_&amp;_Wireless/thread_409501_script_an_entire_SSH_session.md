---
title: "script an entire SSH session?"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by mikedep333 on 2007-04-14
Hey,

I am soon going to need to administrate a number of computers running the openssh daemon. I would like to know if there is a way that I can write a script or something so that logging in and running a bunch of commands is entirely automated (assuming I use the same login credentials on all of the comps.) I know that I can run ssh with -l to save myself one step, but I would like to do more than that. Anyone know how to do this or anything to this effect?

-Mike

Edit: NM, I think I will try this:
[http://www.cyberciti.biz/tips/ssh-public-key-based-authentication-how-to.html](http://www.cyberciti.biz/tips/ssh-public-key-based-authentication-how-to.html)

---

### Post by rmemm on 2007-04-14
Normally what I do is setup ssh auto login so you don't have to use passwords.  Basically you have to create an RSA or DSA key pair and then transfer the public key to the remote systems.  I think the ssh man page tells how to do this.

Once you do that -- just write a script on your local host and append every command with ssh <theHostname> "<the command>".  Ex:  ssh myhost1 ls

Also do a little searching around -- there are tools available that just do this multiple command thing.  Probably Ubuntu -- at least Ubuntu-Universe collection would have at least one of these.  I'd search synaptic or I'd search [www.freshmeat.net](www.freshmeat.net) and find something I liked and see if Ubuntu has it.  Sorry I don't have a specific package name.

Rob

---

