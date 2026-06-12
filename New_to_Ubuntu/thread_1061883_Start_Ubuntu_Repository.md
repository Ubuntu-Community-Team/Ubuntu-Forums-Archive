---
title: "Start Ubuntu Repository"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by nebu on 2009-02-06
I want to make my computer a repository for my local lan.....
so the software i install on this computer will be available to all other computers in my local lan....
how do i do this....

---

### Post by perlluver on 2009-02-06
There is a program called apt-cacher, it will cache all the files on one machine and be accessible to all the others, detailed instructions can be found here: [http://ubuntuforums.org/showthread.php?t=564301](http://ubuntuforums.org/showthread.php?t=564301), hope this is what you need.

---

### Post by Hospadar on 2009-02-06
First off, I'm assuming there is a good reason you don't want to download them from the internet (dial up connection?) If you are worried about security, don't worry, apt is a very secure service, and the ubuntu apt certificates come on the cd, so it would be very difficult for someone to mess with you through apt.  So assuming it's not economically feasible for you to download the same packages more than once:

Well It is possible to install your own apt-server, I don't know how to do it, but I'm sure there are guides on the internet (google "make your own apt server" or something like that), but on a more practical note, It'll probably be a huge pain.

Use your server's apt cache:
There may be some more practical things you can do.  For starters, every package you install on your computer gets downloaded to /var/cache/apt (or something like that).  You could point your other machines at your computer's apt cache and get the debs, and install them by hand, it might take a while to get all the dependancies straightened out it will work, but it won't be all that hard.  The issue here is that you won't be getting updates (the internet computer will, but not the others, you could of course manually re-install the updates as they come).

Use the programs installed on your server through ssh:
You can connect to your server with a protocol called ssh, and run programs remotely with X11 (the linux window manager) forwarding.  This forwards all the graphical stuff from your server to the local machine.  It's a little slower than running stuff locally, but on a typical home router, it's perfectly usable for most applications. (this is very similar in functionality to citrix on windows if you are familiar with that).  If you go to the community docs in my sig and search for "ssh x11 forwarding" you'll find some good stuff.  Mainly you'll need to install "ssh" on your server from synaptic, then connect with a terminal from the remote machine with a command like "ssh -Y server_username@server_local_ip" then run whatever programs you like (starting them from the command line)

A third option:
This is probably more difficult than the above two options to set up, and quite clever (if I do say so myself), but you could mount your /var/cache/apt to your server's /var/cache/apt, and as long as your server get's updated first, your local machines will (all machines do this) check the cache before downloading a package, they will always find what they need (since you already installed/updated it on your server), and they will just use the packages in your server's cache.
You'd probably want to use something like sshfs (it's the easiest to set up in my opinion) to do the actual network mounting.  Check the community docs for info about sshfs, or google it.  Feel free to PM me about it too.

---

### Post by namdung on 2009-02-06
I'd recommend *apt-mirror*.
[http://ubuntuforums.org/showpost.php?p=6474511&postcount=2](http://ubuntuforums.org/showpost.php?p=6474511&postcount=2)

---

### Post by hyper_ch on 2009-02-06
[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

---

