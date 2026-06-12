---
title: "dependancies missing-what then/"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by blurt on 2009-03-09
This is the proverbial 'dumb question'; I recently decided to play around
with virtualbox, and downloaded a couple of packages. When I clicked on them, I got the synaptic package manager, which got stumped by: "error:
missing dependancy: libxxx" Now, over in dos/windows land, this is not hard;
find out where libxxx is, get it, and install it to a specified directory.
  Not so in linuxville it seems. Linux has multiple folders with the same
name; where do I even get the dependancy;what the deuce do I do with it when
I get it? I understand this makes linux harder to hack, but it results in a
magical-mystery-tour for the user. --blurt.](*,)

---

### Post by issih on 2009-03-09
I suspect you are doing it wrong:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

the windows mentality of downloading someting from a website and then installing it is not the ubuntu way.

First port of call is the repositories

Second is finding a ppa repository you can add to your list to get access via synaptic

Third is downloading a .deb from the net

Fourth is compiling from source.

The whole point of the package manager is to manage all the dependencies and automate the download of any necessary extra files, you will be much happier if you get used to using it. I'm willing to bet there are several virtualisation packages that do exactly what you want merely a mouse click away, you just have to let go of how you think things are done.

Hope that helps

---

### Post by sowelie on 2009-03-09
Yes, correct.  So the easiest way to install the latest version of virtualbox is this (assuming you're runing Ubuntu 8.10 (intrepid):

1. Add the following apt url (system -> administration -> software sources click third party software tab).

```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
```

2. Close the dialog, click no do not reload sources.

3. Run this in the terminal to get the apt key from virtualbox:

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

4. In the terminal run:
```
sudo aptitude update
```

5. Finally install virtualbox:

```
sudo aptitude install virtualbox-2.1
```

This will install virtualbox and keep it up to date as updates come out.  You won't have to worry about dependencies.  Alternatively, if you don't need the very latest version you can install the version that is in the ubuntu repos by running:

```
sudo aptitude install virtualbox
```

More information can be found on the virtualbox website:

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

---

