---
title: "problem with updating system after installing Gyachi"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by didik juniarta on 2009-10-10
i have a problem with my ubuntu jaunty, every time i try to update (apt-get update)but this following statement keep showing up :W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0D3C959DB2035A6
W: You may want to run apt-get update to correct these problems

few days ago i tried to install gyachi in my pc, it require this :(deb [http://ppa.launchpad.net/loell/ppa/ubuntu](http://ppa.launchpad.net/loell/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/loell/ppa/ubuntu](http://ppa.launchpad.net/loell/ppa/ubuntu) jaunty main
sudo apt-key adv –recv-keys –keyserver keyserver.ubuntu.com 0xc23b005d874996dc8d03a3c0d0d3c959db2035a6)
to be added in source list.

could anyone help me with this problem??

---

### Post by j7%&lt;RmUg on 2009-10-10
So im assuming you have added that PPA to your sources.list if it comes up with that error.

To use a PPA you need to grab its GPG key which is at this link:

[http://ppa.launchpad.net/loell/ppa/ubuntu/dists/jaunty/Release.gpg](http://ppa.launchpad.net/loell/ppa/ubuntu/dists/jaunty/Release.gpg)

You need to copy and paste the text on that page into a text editor and save it anywhere you like, i name my keyfiles this way: name_of_program.asc, save and exit the text editor.

Then go to System > Administration > Software Sources, then go to the Authentication tab and click import, then browse to where you saved your PGP key and click OK.

Then click close and reload in the box that should come up, if it doesnt, open a terminal and type:

sudo apt-get update

Thats all you have to do.

---

### Post by didik juniarta on 2009-10-10
it's working..on progress

---

### Post by didik juniarta on 2009-10-10
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0D3C959DB2035A6
 i did what you've told me to do but i got this notice....what should i do now??
i already uninstall the Gyachi packages from my pc.

---

