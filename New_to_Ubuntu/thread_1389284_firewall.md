---
title: "firewall???"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by madinc on 2010-01-24
hello to all :D
wich firewall should i use:confused:

---

### Post by OrangeCrate on 2010-01-24
[http://www.psychocats.net/ubuntu/security#firewallantivirus](http://www.psychocats.net/ubuntu/security#firewallantivirus)

---

### Post by madinc on 2010-01-24
thank you orangecrate

---

### Post by mcduck on 2010-01-24
Unless you have some specific reason (like running a server), you are not going to need a firewall at all. The default install of Ubuntu has no running services that would respond to incoming connections from network, and this being Linux you don't need to worry about apps 2calling home" either.. :)

Of course if you at some point install some server software that will listen the network, you might need to set up a firewall as well. In that case use the UFW that comes by default. Or Gufw if you want a graphical user interface. (although even running a server doesn't make a firewall absolute necessity, if you run a web server you probably want it to be accessible from the web, for example..)

Still, based on the fact that this is the beginner forum I'd say it's quite unlikely that you are running any software that would require you to set up a firewall.

---

### Post by OrangeCrate on 2010-01-24
> **madinc said:**
> thank you orangecrate

You're welcome.

:)

---

### Post by mkvnmtr on 2010-01-24
Your default install is running a very efective firewall. If you wish to install an app to configure  it differently be sure you learn exactly what needs to be done before you make any changes. The security forum here will get you started. There are some very good stickeys to read before you make a decision.

---

### Post by mcduck on 2010-01-24
> **mkvnmtr said:**
> Your default install is running a very efective firewall. If you wish to install an app to configure  it differently be sure you learn exactly what needs to be done before you make any changes. The security forum here will get you started. There are some very good stickeys to read before you make a decision.

No, it's not.

The default install of Ubuntu doesn't have an active firewall, because it doesn't need one.

What it *does* have is all the tools required to make a firewall (iptables/netfilter) and a CLI tool for configuring and managing a firewall (UFW). But out-of-the-box the firewall is not running, and it doesn't have any filtering rules.

With no services listening to any network ports it wouldn't really make any sense to filter/monitor data to these ports. That would be kind of like installing locks all over your walls even though there are no doors or windows, just a brick wall.

---

### Post by gnometorule on 2010-01-24
Well I don't know how a firewall could hurt really; I enabled mine. Ubuntu has firewall routines included in the kernel via 'iptables', which I have not tried to manipulate but I hear is a little hard to really dig into. That's why it also comes with a front end called 'UFW', for which there is a GUI, but it's actually pretty easy to use with the command line. This is nice, short description of how to use it (click the 'desktop' link too because I suggest that you do it command line, should you decide to enable it):

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

---

### Post by mcduck on 2010-01-24
> **gnometorule said:**
> Well I don't know how a firewall could hurt really; I enabled mine. Ubuntu has firewall routines included in the kernel via 'iptables', which I have not tried to manipulate but I hear is a little hard to really dig into. That's why it also comes with a front end called 'UFW', for which there is a GUI, but it's actually pretty easy to use with the command line. This is nice, short description of how to use it (click the 'desktop' link too because I suggest that you do it command line, should you decide to enable it):

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

Doesn't hurt (much), but doesn't help anything either.

Like I said, it's like installing locks to a brick wall that has no doors. It's impossible to walk through it regardless of how many locks you bolt into it.

Of course things change if you install some servers that are not meant for public use (like SSH, for example). But even in those cases you get better security by configuring the server itself. Firewall becomes a necessity only when you install some server that doen't have any configuration options for limiting who can connect to it.

---

### Post by houseworkshy on 2010-01-24
There is a firewall built in, this page is a good start to things in general [https://help.ubuntu.com/9.10/index.html](https://help.ubuntu.com/9.10/index.html)
This is more specific to the firewall
[https://help.ubuntu.com/9.10/keeping-safe/C/firewall.html](https://help.ubuntu.com/9.10/keeping-safe/C/firewall.html)
You can also install a gui for firewall management from the repositories the package is called firestarter.
As a newbie I found this little book very helpful, the pdf download is free
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
All the defaults are good anyway so it's not really worth messing around with them untill you know more.  Linux is not like windows.  It is much the same with regards to malware, only around 600 so far.  And even those have to trick you into installing them.  That will change of course so to be ready for it and because you will probably want to share files with windows users install clamtk from the repositories.  Anything in the default repositries is safe btw.

---

### Post by Enigmapond on 2010-01-24
> **mcduck said:**
> Doesn't hurt (much), but doesn't help anything either.

Like I said, it's like installing locks to a brick wall that has no doors. It's impossible to walk through it regardless of how many locks you bolt into it.

Of course things change if you install some servers that are not meant for public use (like SSH, for example). But even in those cases you get better security by configuring the server itself. Firewall becomes a necessity only when you install some server that doen't have any configuration options for limiting who can connect to it.
  With all due respects...you are incorrect and the default Ubuntu come with an active firewall that is set to deny incoming by default. You really need to do just a little research on that if you still find it hard to understand...ufw is defaut...right from the install.

---

### Post by mcduck on 2010-01-24
> **Enigmapond said:**
> With all due respects...you are incorrect and the default Ubuntu come with an active firewall that is set to deny incoming by default. You really need to do just a little research on that if you still find it hard to understand...ufw is defaut...right from the install.

No, it's not. And had you actually checked it, you'd know that as well.

UFW is installed by default, but it's not active by default, and has no rules for filtering any traffic until you make some yourself.

Easy to check on any freshly installed system:

```
$ sudo ufw status
Status: inactive

$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target    prot opt source   destination

Chain FORWARD (policy ACCEPT)
target   prot opt source    destination

Chain OUTPUT (policy ACCEPT)
target  prot opt source     destination
$
```
As you can see from the output, UFW is inactive and has no rules, and iptables has all input, forward and output set to ACCEPT. So, no firewall.

---

### Post by houseworkshy on 2010-01-24
I appologise for passing on incorrect information.  Mcduck is right.  So yes there *is* a firewall built in but please disregard what I said about defaults beings safe as the firewall is *not* active.  Thanks Mcduck.

---

### Post by Bartender on 2010-01-24
```
sudo apt-get install gufw
```

or go into Synaptic and search for gufw in order to get a simple GUI for ufw

---

