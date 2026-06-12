---
title: "MythBuntu on Ubuntu Server 8.10?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by dragon_reborn on 2009-02-11
Hi, I am an absolute beginner to Linux and I am considering installing Ubuntu Server 8.10 on my IBM x346 server. I want to use Ubuntu Server because I want to set the server up as a mail and proxy server for my home network.I want to also use this server as a MythTV server, My question; Will this work or should I use Ubuntu desktop?

---

### Post by 7mkgw7q on 2009-02-11
Why not just use Mythbuntu?

---

### Post by Thelasko on 2009-02-11
I'm not an expert on MythTV/MythBuntu, but I believe you just install the [mythtv-backend-master]("http://packages.ubuntu.com/intrepid/mythtv-backend-master") package.  To do so type:
```
sudo apt-get install mythtv-backend-master
```

Remember, Ubuntu Server has no GUI and neither does this package.  Any configuration you need to do will have to be done via the command line.

I should also note that installing the [Mythweb]("http://packages.ubuntu.com/intrepid/mythweb") package will add a web based interface with this machine.  To do so type:

```
sudo apt-get install mythweb
```

This is probably not the best route to take for someone who is new to Linux.  Ubuntu Desktop or Mythbuntu will provide simple GUI tools that will likely be easier for someone with no Linux experience.

---

### Post by dragon_reborn on 2009-02-13
Thanks, If I use MythBuntu, can I still set up the server as a internet gateway and mail serve?

---

### Post by hellion0 on 2009-02-13
Yes. All the apps you'd use on Ubuntu Server are also compatible with Ubuntu Desktop (and by extension, Mythbuntu). You may have to install some of these services after-the-fact, but configuring those tools on the desktop is pretty much the same as configuring them on the server version.

---

