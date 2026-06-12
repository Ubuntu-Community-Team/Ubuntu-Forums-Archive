---
title: "Firewall Suggestions?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by deaner51 on 2009-11-12
I am running 9.10 on a Dell B110 that is always left on. On my network I have iMacs, Windows Vista, XP, the Ubuntu Dell and a wireless printer all connected together, either hardwired or wirelessly. 

It is my understanding that I should install a firewall.  Assuming that this is the case, and given that the Dell Ubuntu is always on, would it make sense to install the firewall on that computer?  If yes, what would you all recommend?  I read on the internet about a program called "mason" that is supposed to load up and run pretty easily.  Is that a good choice and if so, will it run on Ubuntu?

Any thoughts and opinions on the matter will be greatly appreciated!:D

---

### Post by Zzl1xndd on 2009-11-12
Given whats on your network your probably have a NAT enabled router and that is a pretty good firewall in its self. As long as you don't need something to watch outgoing connections you should be fine. 

I would also recommend heading over to [http://www.grc.com](http://www.grc.com) and using shields up. Great tool for seeing how open your network is.

---

### Post by The Funkbomb on 2009-11-12
ufw (uncomplicated firewall) comes with ubuntu.  It's light weight and relatively easy to configure.

Go into terminal and type:

```
sudo ufw enable
```

Firewall is now enabled but not blocking anything.

Type this:

```
sudo ufw default deny
```

This will block all ports.

Now, if you're using a program like Transmission Bit Torrent Client, you need to open a port on tcp.  Let's say it's port 51300.  You would type this:

```
sudo ufw allow 51300/tcp
```

This opens that port.

You can check the status by typing in:

```
sudo ufw status
```

To delete a rule, just type:

```
sudo ufw delete allow 51300/tcp
```

Rule deleted!

That's just the basics.  You can set it up so only certain IPs can access that open port and a whole bunch of stuff.

Good luck!

---

### Post by coldReactive on 2009-11-12
> **The Funkbomb said:**
> ufw (uncomplicated firewall) comes with ubuntu.  It's light weight and relatively easy to configure.

Yeah, ESPECIALLY with the way you did it. :|

Just use gufw :P

---

### Post by The Funkbomb on 2009-11-12
I tried gufw and firestarter.  They worked but here is my rationale behind using terminal and manually configuring UFW.

I have a keybind for terminal on my system.  Instead of going to the menus, I have instant access to terminal and can edit my UFW or anything else I want to do.  Three keystrokes to do anything.  Pretty impressive.  Plus, for absolute beginners, it's good for them to get familiar with terminal.  Why not start on something that you can't really mess up?

---

### Post by coldReactive on 2009-11-12
> **The Funkbomb said:**
> I have a keybind for terminal on my system.  Instead of going to the menus, I have instant access to terminal and can edit my UFW or anything else I want to do.  Three keystrokes to do anything.  Pretty impressive.  Plus, for absolute beginners, it's good for them to get familiar with terminal.  Why not start on something that you can't really mess up?

The reason for the 1000 papercuts or whatever was to make sure that newbies would get used to ubuntu without having to use the terminal much. :|

---

### Post by The Funkbomb on 2009-11-12
> **coldReactive said:**
> The reason for the 1000 papercuts or whatever was to make sure that newbies would get used to ubuntu without having to use the terminal much. :|

I don't understand why.  Terminal is by far the best part of linux.  People should get used to it so when they have to use it, they aren't clueless.

---

### Post by coldReactive on 2009-11-12
> **The Funkbomb said:**
> I don't understand why.  Terminal is by far the best part of linux.  People should get used to it so when they have to use it, they aren't clueless.

There's even a GUI for building packages from source into DEB:

[https://launchpad.net/giftwrap](https://launchpad.net/giftwrap)

---

### Post by deaner51 on 2009-11-15
Thank you all for the responses to my question.  I found them all informative and helpful. I looked into my router, a TrendNet TEW-432BRP and found that it does have a built-in firewall.  I am already using the MAC filtering for the wireless signal, so it looks like I am pretty well protected. I will read the suggested article about security, though.
Thank you again!

---

