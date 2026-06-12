---
title: "Tor installation help needed! 9.10"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by OSAppleX on 2010-05-30
Hey all,

I've been trying to install Tor on my Xubuntu 9.10 for a long time but can't get it to install.. I've followed the instructions on this website:

[FONT=monospace]http://www.torproject.org/docs/debian.html.en[/FONT]

but I still get errors and it doesn't install... Any kind of help or anything would be helpful.  It would also be nice if someone could point me to someplace where I can download a .deb for Tor?  I've tried a couple of .deb downloads for Tor but get errors...  Thanks in advance!

---

### Post by kaldor on 2010-05-30
What kind of errors? Copy/pastes are fine :)

---

### Post by OSAppleX on 2010-06-02
Ok here we go thanks for the reply!

So first I put this line into the end of the sources.list file in /etc/apt/sources:

deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main


But replacing DISTRIBUTION with "karmic" no quotes.  
Then I ran these commands in the terminal:


gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

[FONT=Verdana]
and it's all smooth sailing until i do this:


[/FONT]apt-get update
apt-get install tor tor-geoipdb


And it gives me this after I run the apt-get update: 


W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<karmic>/main/binary-i386/Packages.gz  404  Not Found [IP: 88.198.151.34 80]


And when I do the second one it gives me this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tor has no installation candidate

And thats it.. it didn't install anything..

---

### Post by gandaran on 2010-06-02
> W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<karmic>/main/binary-i386/Packages.gz 404 Not Found [IP: 88.198.151.34 80]

this is the correct url
deb.torproject.org/torproject.org/dists/[COLOR="Red"]karmic[/COLOR]/main/binary-i386/
or the line for apt
deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) karmic main

---

### Post by inameiname on 2010-06-02
I'm not sure why you are having an issue with getting them, as I have that very same repo installed, and installed tor and tor-geoipdb just that way.

Regardless, here is where you'd find those two deb files, which aren't automatically downloading for you:

[http://deb.torproject.org/torproject.org/pool/main/t/tor/?C=M;O=D](http://deb.torproject.org/torproject.org/pool/main/t/tor/?C=M;O=D)

UPDATE:

Oh duh...I didn't even notice he forgot to remove the "<" and ">". Good catch, gandaran.

---

### Post by Jakiejake on 2010-06-02
> **OSAppleX said:**
> Hey all,

I've been trying to install Tor on my Xubuntu 9.10 for a long time but can't get it to install.. I've followed the instructions on this website:

[FONT=monospace]http://www.torproject.org/docs/debian.html.en[/FONT]

but I still get errors and it doesn't install... Any kind of help or anything would be helpful.  It would also be nice if someone could point me to someplace where I can download a .deb for Tor?  I've tried a couple of .deb downloads for Tor but get errors...  Thanks in advance!

Ubuntu Software Center?

---

### Post by OSAppleX on 2010-06-02
Oh okay thanks guys!  I didn't think to remove the <'s, and thanks for the page with the .debs too, that is easier than all this terminal stuff

---

