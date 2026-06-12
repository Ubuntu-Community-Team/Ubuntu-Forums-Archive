---
title: "looking to start a home server"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by Tubbstosterone on 2010-07-01
I'm pretty much a beginner when it comes to Linux and Ubuntu. My only experience is XUbuntu, which we used in my compsci class at school.  I have a little bit of experience with working with the command line and such, but I'm still pretty slow, and I often need to look up commands.

Now the problem:  I've got a spare computer that I am looking to set up as a home server.  I don't want to do anything too fancy, I just want to have a center hub for my house that serves as a back up for my upcoming projects, important files, etc, etc. I'm working on a massive project that I want to be able to access from several computers that are currently on a network I've set up.

My question is, would Ubuntu Server Edition be a good choice? I've been doing a little bit of research and I've found out that there isn't any kind of GUI for it.  I'm not slamming the command line, but it makes it hard to experiment and figure out what to do and how to do it if you can't really see what you're doing.  All I really want to do is set up a computer for a simple in house file share.  Is installing Ubuntu server edition a good idea?

---

### Post by cariboo on 2010-07-01
You can use the desktop version if you need a gui, If the server isn't going to open to the world you shouldn't have any worries.

I would suggest using NFS for file sharing between two computers running a linux variant. For a howto, have a look here [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo"). 

Another suggestion is to remove gdm, once you have everything setup, and only start X when you need it from the prompt by typing:

```
startx
```

For more info on setting up a server, have a look [here]("https://help.ubuntu.com/8.04/serverguide/C/index.html").

---

### Post by ubudog on 2010-07-01
> **cariboo907 said:**
> You can use the desktop version if you need a gui, If the server isn't going to open to the world you shouldn't have any worries.

I would suggest using NFS for file sharing between two computers running a linux variant. For a howto, have a look here [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo"). 

Another suggestion is to remove gdm, once you have everything setup, and only start X when you need it from the prompt by typing:

```
startx
```

For more info on setting up a server, have a look [here]("https://help.ubuntu.com/8.04/serverguide/C/index.html").

So it's not safe to run a home server with the desktop version?

---

### Post by lkraemer on 2010-07-01
If you have some older hardware laying around check out FreeNAS.
[http://en.wikipedia.org/wiki/FreeNAS](http://en.wikipedia.org/wiki/FreeNAS)

I think you will be impressed.  It works like a champ.

lk

---

### Post by k3lt01 on 2010-07-01
> **ubudog said:**
> So it's not safe to run a home server with the desktop version?It isn't that it's not safe it is more that the Server edition is specifically designed to be lightweight and secure for server work. Any additional programs, such as a GUI and/or web browser, installed add a possible entry point from the outside world.

My sever at home has the desktop edition but it isn't open to the internet, yet. When it is I will back up the relevant configuration files, do a clean install of the server edition and then reinstall the back ups.

---

### Post by Tubbstosterone on 2010-07-02
cool, thanks for the help

---

### Post by kaldor on 2010-07-02
> It isn't that it's not safe it is more that the Server edition is specifically designed to be lightweight and secure for server work. Any additional programs, such as a GUI and/or web browser, installed add a possible entry point from the outside world.

Exactly. X (the underlying program that powers the GUI, in basic terms) adds many security vulnerabilities. The Server edition will be better, but you can install a very lightweight GUI if you need to. 

The Linux commands are very easy to learn and it's easy to just look them up. I suggest you print off a "cheat sheet" for it. 

Ubuntu Server Edition or CentOS are my choices for a server OS.

---

### Post by ubudog on 2010-07-02
I ran a home server before, using my laptop and the desktop edition.  Didn't know about this.  Thanks.

---

### Post by kaldor on 2010-07-02
> **ubudog said:**
> I ran a home server before, using my laptop and the desktop edition.  Didn't know about this.  Thanks.

Not going to make a huge difference using Desktop as a server if it's a home thing. Mainly for "important" or larger setups is it truly a factor.

---

### Post by bodhi.zazen on 2010-07-02
> **kaldor said:**
> Not going to make a huge difference using Desktop as a server if it's a home thing. Mainly for "important" or larger setups is it truly a factor.

As a rule of thumb, if you are behind a "router" (firewall) and you do not forward ports you are fine.

If you do not use a "router" (firewall) , configure your server to limit connections and /or configure iptables.

Also, as a rule of thumb, if the machine is a dedicated server X adds very little. Most server administration is command line or editing text files, so gedit is no better then nano or vim.

If you want a graphical front end to configure your server use Webmin (or similar depending on your needs).

---

### Post by ubudog on 2010-07-02
Thanks!

---

