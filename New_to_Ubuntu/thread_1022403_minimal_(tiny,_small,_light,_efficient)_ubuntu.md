---
title: "minimal (tiny, small, light, efficient) ubuntu"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by crowhill on 2008-12-26
Hi there

I like Ubuntu because it recognizes most of the hardware on my DELL xps m1330 out of the box. I don't like Ubuntu because it comes with a lot of stuff that I never ever use (let me call it crap).

I would like to have a linux system on my laptop that recognizes my hardware but, much more important, that is super light and, therefore, fast. I only want to have that software that I really need (and I know what I need).

I tried the following solutions:

1. Debian! I love it! It let me create my minimal installation (on an older laptop) from the installation menu. In Ubuntu, it seems to me, you have no other choice but to install the whole thing. Unfortunately, I failed to install Debian on my new laptop (hardware issues).

2. Fluxbox and Ubuntu: A step in the right direction. However, Fluxbuntu seemed unstable to me (the windows didn't always do what I told them to do).

3. Openbox and Ubuntu: This is what I'm working with at the moment. I like it. However, still, there is too much junk from the Gnome installation on my system.

4. I tried Crunchbang Linux: I like it, though it crunched and banged in my case.

5. TinyMe: Very nice. However, no wireless and monitor recognition out of the box (probably, among other issues).

6. Damn Small Linux: No wireless out of the box and too much software that I don't want.

7. Puppy: Too much software that I don't want.

Here is my question:

How can I get a MINIMAL Ubuntu with Openbox and only the software I really want? Also, it should recognize the Hardware on my machine. How could I get started on a project like that?

Some advice to get me started would be very much appreciated.

Long live Linux,
cheers,
crowhill.

---

### Post by mister_pink on 2008-12-26
Use the alternate cd to install a command line only system. From this you can then build up only the software you want to install.

---

### Post by crowhill on 2008-12-26
> **mister_pink said:**
> Use the alternate cd to install a command line only system. From this you can then build up only the software you want to install.

OK, great. That sounds like what I want (if it lets me choose the desktop environment as well ...).

crowhill.

---

### Post by OutOfReach on 2008-12-26
Well, you could try Arch Linux, it only installs the basic tools (GNU utils for example) and lets you build from that.

Ubuntu isn't meant to be light, it's goal is to be easy to use. That's why I am suggesting to go to another distro if you are looking for a light OS.

---

### Post by kansasnoob on 2008-12-26
Well, you can get the minimal install CD here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Then from terminal:

```
sudo apt-get install gnome
```

That will give you a very basic gnome desktop, but you'll have to update components manually for the most part.

You could install:

```
gnome-desktop-environment
```

But it's not going to be much lighter than Ubuntu desktop.

There are other options:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by mkvnmtr on 2008-12-26
Google  "minumal install Ubuntu" you will find an install disk of about 14MB. It begins with a command line and with about 4 comands you can have a window manager and a package manager with a GUI. Then install anything you want.You will have the same Repositories as everone else.

---

