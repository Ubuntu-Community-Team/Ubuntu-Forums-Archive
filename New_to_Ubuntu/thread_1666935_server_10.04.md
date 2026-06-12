---
title: "server 10.04"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by powte on 2011-01-14
First off I am new to linux. I have been using the netbook version for 4 days and installed server on my server last night. With that being said I installed server and to make it easier I have installed the gui. My goal is to install a mail server and host some websites. After installing the gui I cannot find any of these options.

---

### Post by WRDN on 2011-01-14
To host websites, you'll need a web server. Two common options are Apache2 (the most popular web server) and lighthttpd.

For email servers, you may want to take a look at postfix.

All the options are in the repositories.

---

### Post by powte on 2011-01-14
What do you mean by repositories. Is this the ubuntu software center? I am not sure what I did wrong because when I installed the server I thought it added those things

---

### Post by powte on 2011-01-14
What do you mean by repositories. Is this the ubuntu software center? I am not sure what I did wrong because when I installed the server I thought it added those things

---

### Post by WRDN on 2011-01-14
The Ubuntu Server distribution can generally be considered a "base" system. It uses a kernel optimised for servers (seperate scheduler to desktop systems), and has the base tools required (all common Terminal programs, such as ls, find, sed etc.).
You have to build up what you want on top of the server distribution. For example, on my Ubuntu Server (Jaunty), I run a web server, repository hosting and a few other things. 

The Ubuntu Software Center, like Synaptic and other tools, is just a front end to the repository (i.e. database) of available software to install.
There are multiple repositories, including main, universe, restricted, multiverse and external (3rd party) repositories.

Generally, servers do not have window managers for a number of reasons. Primarily, you save resources, and there are less security concerns if you run a command line only server.

I think you should get used to using the Terminal for the administration of the machine, and the command line software management tools.

The main tools for installing software are "apt-get" and "aptitude".

As an example, to install Apache2 (the web server), open the Terminal and type:

```
sudo apt-get install apache2
```

Once this is installed, on the same machine, navigate to "http://localhost/" in a web browser, or access the machine remotely (use local IP address on LAN, or port forward and use public address on WAN).
The web pages are stored by default in /var/www/

---

