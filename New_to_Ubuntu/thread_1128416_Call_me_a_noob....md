---
title: "Call me a noob..."
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Essar Allen on 2009-04-17
Hey, I just started using Ubuntu and I really don't have much of an idea of what I'm doing yet. I have no clue how to install things... Take the gtkpod tarball (that's a .tar.gz, right?) for example. I downloaded it to my desktop, what do I do now? I've looked around to see if someone explained how to install things, because I'm sure someone else has had the same problem, but I can't find anything. Any help would be greatly appreciated!

---

### Post by owenll on 2009-04-17
There is some info here:

[https://help.ubuntu.com/8.04/add-applications/C/install-file.html](https://help.ubuntu.com/8.04/add-applications/C/install-file.html)

---

### Post by Bachstelze on 2009-04-17
.tar.gz files are archives, just like ZIPs or RARs. They can contain anything. In your case, it is most likely source code that you will need to compile. It is one of the several ways of installing software in Ubuntu, but it is definitely not the preferred way for beginners.

All the information you need about installing software in Ubuntu is [here]("https://help.ubuntu.com/8.10/add-applications/C/index.html").

---

### Post by js6seaj on 2009-04-17
> **HymnToLife said:**
> .tar.gz files are archives, just like ZIPs or RARs. They can contain anything. In your case, it is most likely source code that you will need to compile. It is one of the several ways of installing software in Ubuntu, but it is definitely not the preferred way for beginners.

All the information you need about installing software in Ubuntu is [here]("https://help.ubuntu.com/8.10/add-applications/C/index.html").
Perhaps an odd question, but what is the way to install software on Ubuntu for beginners?

---

### Post by adamitj on 2009-04-17
Ubuntu works with binary packages as same as Debian does. Generally, "tar.gz" or "tar.bz2" are source code archives. That means you need to compile then and manually install with make or gmake (see below).

You can install software in Ubuntu in many ways, but I'll explain the most commom:

1) From repositories: Ubuntu cames with a lot of packages inside their repositories over the web. To install software, just go to the menu "Applications",  "Add/Remove". There you can search for a lot of software.

If you know the name of package you want to install, go to "System", "Administration", "Synaptic Package Manager".

Pros:
  - It's easy;
  - Installed packages can be update from the Update Manager when a new version is available;
  - Packages are almost all tested and are stable (not for ALL repositories);
  - Auto resolve dependencies;

Cons:
  - Sometimes the repository version is not the newest of a package because Ubuntu team do not tested yet;


2) From source code: you can download a source code archive, uncompress it, configure, compile and install the software. Note that not all source code came with a user-friendly script. So in many cases you'll need to add icons and links with "ln" manually.

Pros:
  - Sometimes you can compile source code with specific performance options;
  - You can have the newest available version;

Cons:
  - It's hard for newbie users;
  - It cannot be updated (only by removing and installing a new version manually);
  - Can conflict with the same installed package from repositories;

3) Installation Packages: some applications have a good installation package, as in Windows OS. An example is NetBeans 6.5.

Pros:
  - Easy;
  - You can have the newest available version;

Cons:
  - It cannot be updated (only by removing and installing a new version manually);
  - Can conflict with the same installed package from repositories;


After all, I recommend you to install applications from repositories, ever. If you can't find, post some message on the forum (maybe it's with a different name you are looking for). If the desired software don't exists in repositories, try to install from source.

---

### Post by Therion on 2009-04-17
> **js6seaj said:**
> Perhaps an odd question, but what is the way to install software on Ubuntu for beginners?
Add/Remove Software from the Applications menu.

---

### Post by js6seaj on 2009-04-17
> **Therion said:**
> Add/Remove Software from the Applications menu. Thanks

---

### Post by LowSky on 2009-04-17
or form terminal

sudo apt-get install gtkpod

or use synaptic (more stuff listed than in add/remove

System> admin> synaptic

---

### Post by Therion on 2009-04-17
> **LowSky said:**
> 

... or use synaptic (more stuff listed than in add/remove
My Thinking:

Step 1: Add/Remove
Step 2: Synaptic
Step 3: Install from source

---

### Post by Essar Allen on 2009-04-17
> **LowSky said:**
> or form terminal

sudo apt-get install gtkpod

or use synaptic (more stuff listed than in add/remove

System> admin> synaptic

Thank you very much LowSky...that was quite easy. Does that work for most things?

---

### Post by Paqman on 2009-04-17
> **Therion said:**
> My Thinking:

Step 1: Add/Remove
Step 2: Synaptic
[B]Step 3: PPA or 3rd party repo
Step 4: .deb file[/B]
Step 5: Install from source

I'd add another couple of options in before falling back on source code. There's enough PPAs and .debs around these days that I haven't had to compile anything in a loooooong time.

---

### Post by adamitj on 2009-04-17
> **Paqman said:**
> I'd add another couple of options in before falling back on source code. There's enough PPAs and .debs around these days that I haven't had to compile anything in a loooooong time.

Indeed. I really forgot PPAs and other .debs.
Other important information that some beginners can be confused about: "apt-get", "aptitude" and Synaptic application does the same actions on packages (add, remove, reinstall, etc) each one in a different way.

---

### Post by Bölvaður on 2009-04-17
youtube video about Add/Remove
[http://www.youtube.com/watch?v=yGzEV_hJyX4](http://www.youtube.com/watch?v=yGzEV_hJyX4)

> **Therion said:**
> My Thinking:


Step 1: Add/Remove
Step 2: Synaptic
[B]Step 3: PPA or 3rd party repo
Step 4: .deb file[/B]
Step 5: .tar.gz that contains compiled program
Step 6: executable installer file
Step 7: Install from source

added 2 more.

---

### Post by Mercury_Alpha on 2009-04-17
> **Essar Allen said:**
> Thank you very much LowSky...that was quite easy. Does that work for most things?

Yes. Sometimes the package versions available through the official repositories (which you're accessing through Add/Remove Programs and Synaptic) are not the newest available, but they are the ones that have been tested to work with Ubuntu. Newer versions, which may be unstable or otherwise glitchy, can be found at [Launchpad.net]("https://launchpad.net/"), which is a developer testing and distribution site run by Canonical (the makers of Ubuntu).

I don't recommend going anywhere near getdeb.net, because those packages are not signed, can have messed up dependencies, and are otherwise unreliable.

---

### Post by oldos2er on 2009-04-17
> **js6seaj said:**
> Perhaps an odd question, but what is the way to install software on Ubuntu for beginners?

[https://help.ubuntu.com/community/Applications](https://help.ubuntu.com/community/Applications)

[https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

