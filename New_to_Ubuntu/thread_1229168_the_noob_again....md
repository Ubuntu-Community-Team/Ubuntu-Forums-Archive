---
title: "the noob again..."
date: 2009-08-01
forum: New to Ubuntu
---

### Post by hihihi100 on 2009-08-01
hello there again:

I want to install clamav-0.95.2 (downloaded as a tar.gz file) in my laptop, that runs Ubuntu 9.04. Now, to install any new software, if I cant use the "software sources" option, I must activate the "Terminal", right?

the instructions manual says:

---Briefly, the shell commands `./configure; make; make install' should
configure, build, and install this package.---

I have to type `./configure; make; make install' in "Terminal", am I right??

If not, what do I have to do??

Thx in advance

cheers

---

### Post by stoogiebuncho on 2009-08-01
There's a few ways of doing this that would be easier.

I'd suggest going to Applications > Add/Remove, make sure it's set to show All Available Applications, and then search for "clam".  It should come up with clamtk, which is the graphical interface for clamav.

Just click the checkbox, and then hit Apply Changes and it will download it and install it for you.

You can also install it through Synaptic Package Manager (System > Administration > Synaptic Package Manager), and again, just do a search for clam or clamav or whatever.  Mark what you want to install and click Apply.

The other nice thing about doing it these ways is that when a new version comes out it will update automatically.

edit: You may know this already, but ClamAV looks for Windows viruses, not linux viruses (there aren't really any linux viruses "in the wild").  So unless you are networked with some Windows computers, you don't really need it

---

### Post by donkyhotay on 2009-08-01
stoogiebuncho is correct, it is much easier to install from the package managers and it gives you free updates. Always try to install from them first before installing from source. However the commands you gave are correct for *most* installations from source packages.

---

### Post by kostkon on 2009-08-01
And here is a [good how-to]("http://www.psychocats.net/ubuntu/installingsoftware").

---

