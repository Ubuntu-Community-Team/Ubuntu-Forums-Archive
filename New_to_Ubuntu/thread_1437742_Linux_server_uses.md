---
title: "Linux server uses"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by ave2 on 2010-03-24
Okay this is going to show my ignorance, but I was thinking about setting up an ubuntu server on a spare machine at home, just to mess around with it and learn something new- but I have never even seen a server, much less worked on one.... so as a home user are there any practical uses for a server- things I could use it for in my day to day activities.

---

### Post by HereInOz on 2010-03-24
The first thing you could use it for is to store all your files - use it as a file server - and access those files from Linux or windows machines.

---

### Post by undecim on 2010-03-24
You can use it as a file server to make backups of all your files in case your hard drive goes out.

You can set up a caching HTTP and DNS server to speed up your web browsing.

You can set up an SSH server with port forwardarding so that you can connect to your computer from anywhere on the internet to give yourself a safe tunnel when using unsecured public wifi.

You can set up a package cache that will speed up Ubuntu upgrades if you have multiple Ubuntu computers on your network.

And lots more. My server does all of the above, and is also connected to my HD TV so that I can watch movies on it.

---

### Post by HermanAB on 2010-03-24
Howdy,

There really isn't anything magical about a server.  The only reason why people are not familiar with the concept is because Microsoft charges lots of money for theirs, so people think that it must be something special...

You can do a normal Ubuntu install and then install a file server, web server, FTP, DNS, DHCP, yadda, yadda, whatever you want.  No biggie.  It's all in the repos.

---

### Post by Calash on 2010-03-24
I had a server for a while that did several things.  It offers a backup location for important files.  It also acted as an MP3 server so we could share our music to all the computers in the house.

Later on it became a general media server, offering recorded television and videos both as a file share and using uPNP.

Right now I migrated to a NAS.  It uses less power and is a bit easier to maintain.  However building the server was very worthwile and helped to learn how to configure Ubuntu on a network.

The first questions to ask is what you want out of the server.  There is a server edition of Ubuntu however I never used it so I am not sure what it comes with.  My rig was built from Mythbuntu as it handled the television recording and playback perfectly.

---

### Post by Darkpegasus333 on 2010-03-24
You could also use it to host music, create a wiki, blog...I forget all the things I used mine for in the past. One of the most convenient is using it as a medium to share pictures and other files with friends. You just copy and paste and send them the link.

---

### Post by undecim on 2010-03-24
I also like having an http server on my network. I have a subdomian from freedns.afraid.org pointing to my IP address, so whenever I need to share a file with someone, I just copy it to my public_html folder and sent them a link like [http://[mydomain]/~undecim/file.jpg](http://[mydomain]/~undecim/file.jpg)

---

### Post by The Cog on 2010-03-24
> **HermanAB said:**
> You can do a normal Ubuntu install and then install a file server, web server, FTP, DNS, DHCP, yadda, yadda, whatever you want.  No biggie.  It's all in the repos.

I will second this. The ubuntu server distro has two major differences to the desktop version that I know of. Firstly, it installs without a GUI (although you can use the command line to install one) - after all, a server sits in a server room with no local users, not even a screen or keyboard normally. Secondly, its scheduler is optimised for server throughut rather than single user reactivity. If you are playing with it in order to learn, you are better off with the desktop version and installing your web/ft/etc server programs on that.

---

