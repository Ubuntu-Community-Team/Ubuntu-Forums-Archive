---
title: "How to get ypbind or equivalent on Ubuntu?"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by Tsu Dho Nimh on 2007-07-25
My network admin says I need to have ypbind installed and active so I can see and use the network shares on the file server.

Where is it or its equivalent, and how do I install it?  I have checked the "Add Applications" and the Synaptic Package manager and they don't have it.

---

### Post by Synflux on 2007-07-25
Hello,

I have no idea what ypbind is or does ("finds the server for NIS domains and maintains the  NIS  binding information"  according to Google). However, you should be able to install it by:

sudo apt-get install nis

Should be able to find it in synaptic but I haven't tried.

Hope that helps you out.:)

---

### Post by Tsu Dho Nimh on 2007-07-25
Thanks.  It must be a part of NIS?  

Anyway, NIS is a package available thorugh Synaptic, so I'll try it.

---

### Post by toddpedlar on 2007-07-25
It should be part of NIS - I'm looking to use the same kind of networking/disk sharing, so I'm about to try getting it.  :)

TKP

---

### Post by sgbotsford on 2007-07-31
NIS = Network Information System  This is an early method to manage user login information at a single point.  If you have a hundred computers in your school, you don't want to remember a password for each one.  

NIS used to be called Yellow Pages, but the owner of that trademark fussed at Sun, and so the name was changed.  However all of the commands start with the letters yp.

In NIS a server (running a program called ypserv) starts, and listens for requests.
Data is in the form of simple maps with a single atribute, and corresponding data.

The client runs ypbind (surprise...) 
When I log in to a client, if it is running ypbind, and the configuration file nsswitch.conf is set up to use NIS, and the appropriate entries are made in /etc/passwd shadow and group, and the server doesn't use a slightly different format for hte data file than your computer expects, then your client will issue a request asking the server, "Request a match in map passwd.byname for user Tom"  And the server will respond with a line that looks exactly like the line in the passwd file would be if Tom was a local user.

It should be easy to set up if the NIS server at your school is also a linux box.  If it's another form of Un*x then there will be some additional hoops the jump through.

Hope this helps.

---

