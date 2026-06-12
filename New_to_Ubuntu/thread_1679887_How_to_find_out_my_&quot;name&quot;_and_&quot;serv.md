---
title: "How to find out my &quot;name&quot; and &quot;server name&quot;?"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by stalemath on 2011-02-01
I am new to Linux and I am using Xubuntu to set up a server. I am following a guide online, and it's telling me to enter my "name" and "sever name" that I chose when I set up Xubuntu; however, I don't remember exactly what it's referring to... So I was wondering if there is a way to look this info up.

---

### Post by lykwydchykyn on 2011-02-01
What guide is it?  Those are kind of vague terms without some context.  I would assume it refers to your hostname, which is displayed at the login prompt by default (or by looking in the /etc/hostname file).

Without some context, though, one can't be sure.

---

### Post by khelben1979 on 2011-02-01
Press ALT + F2 and start an X shell like [xterm]("http://en.wikipedia.org/wiki/Xterm") for instance. You see your username on the left side of the @ and your server name of the right side.

As an example **john@my_server**.

---

### Post by stalemath on 2011-02-01
This is the guide: [http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)

If you know of a better one, please let me know. This one seems like it may be a bit dated.

---

### Post by lykwydchykyn on 2011-02-01
> **stalemath said:**
> This is the guide: [http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)

If you know of a better one, please let me know. This one seems like it may be a bit dated.

Which part are you on?

---

### Post by stalemath on 2011-02-01
I'm on Part 4 - File Sharing

---

### Post by stalemath on 2011-02-01
I'm already having trouble as the smb.conf file I have differs from the one in the tutorial.

---

### Post by stalemath on 2011-02-01
It seems that I'm already having trouble as the smb.conf file I have differs from the one in the tutorial.

(sorry didn't mean to re-post this, I didn't think the first one went through... I don't know how to delete this message...)

---

### Post by lykwydchykyn on 2011-02-01
> **stalemath said:**
> It seems that I'm already having trouble as the smb.conf file I have differs from the one in the tutorial.

(sorry didn't mean to re-post this, I didn't think the first one went through... I don't know how to delete this message...)

That shouldn't matter too much, samba doesn't change a whole lot but some of the default config settings get tweaked from release to release.

I'm guessing you're wondering what to put for:
```

workgroup = "Name"
netbios name = "Server name"

```

Workgroup is pretty irrelevant, though you might want it to match the workgroup on your workstations for convenience.  

netbios name is just what the server will show up as when you  browse to it from a workstation.  It's typically just the hostname (a.k.a. computer name).  That's what we've told you how to find above.

---

### Post by stalemath on 2011-02-01
I don't know if I edited the smb.conf file correctly. I'm trying to find out, but I don't know how to find out my server IP address and how to access it from a Mac (the tutorial speaks of accessing it from Windows)

---

### Post by lykwydchykyn on 2011-02-01
You can find your IP address by typing "ifconfig" at a command line.  Look through the output and find the "inet addr:" value.

As for how to access it from a mac, I have no idea.

---

### Post by stalemath on 2011-02-01
Would that be under eth0, eth1, or lo?

---

### Post by lykwydchykyn on 2011-02-01
> **stalemath said:**
> Would that be under eth0, eth1, or lo?

Not lo, but I couldn't tell you whether it was eth0 or eth1; do you have both, and do both have an IP?

---

### Post by stalemath on 2011-02-01
> **lykwydchykyn said:**
> Not lo, but I couldn't tell you whether it was eth0 or eth1; do you have both, and do both have an IP?

eth0 has an inet6 addr
eth1 has an inet addr and inet6 addr
lo has an inet addr and inet6 addr

So, I'm guessing it would be eth1. I can't figure out how to connect to it though. When I typed in the inet addr from lo (on Firefox on my Mac) it took me to the Apache Test page, but when I tried the inet addr from eth1, it came up as an error saying it was unable to connect.

---

### Post by lykwydchykyn on 2011-02-01
You don't use firefox to connect to samba, samba is a file-sharing protocol -- like when you share out folders in Windows.

Firefox is trying to connect to a web service, which you presumably haven't set up yet.

"lo" means loopback, and it's IP basically means "this computer".   If you type that IP (127.0.0.1) on any computer, you are just referring to your own machine.   

I don't know how to connect to shared folders from a mac, but if look that up try to connect to that eth1 address.

---

### Post by stalemath on 2011-02-01
I figured out how to connect using this guide: [http://www.techrepublic.com/blog/opensource/how-do-i-connect-a-mac-os-x-machine-to-a-samba-share/173](http://www.techrepublic.com/blog/opensource/how-do-i-connect-a-mac-os-x-machine-to-a-samba-share/173)

However, I cannot seem to figure out how to access [homes]... I enabled it in smb.conf, but it's still only showing print$ (as was the default option in smb.conf)

---

### Post by stalemath on 2011-02-02
> **stalemath said:**
> I figured out how to connect using this guide: [http://www.techrepublic.com/blog/opensource/how-do-i-connect-a-mac-os-x-machine-to-a-samba-share/173](http://www.techrepublic.com/blog/opensource/how-do-i-connect-a-mac-os-x-machine-to-a-samba-share/173)

However, I cannot seem to figure out how to access [homes]... I enabled it in smb.conf, but it's still only showing print$ (as was the default option in smb.conf)

Nevermind, I figured out how to enable homes, but when I try to mount it, it says The volume "homes" could not be mounted.

---

### Post by lykwydchykyn on 2011-02-02
> **stalemath said:**
> Nevermind, I figured out how to enable homes, but when I try to mount it, it says The volume "homes" could not be mounted.

Homes is a special share; you don't go to \\servername\homes to access it, you go to \\servername\myusername.

---

### Post by stalemath on 2011-02-02
> **lykwydchykyn said:**
> Homes is a special share; you don't go to \\servername\homes to access it, you go to \\servername\myusername.

I know that

---

### Post by lykwydchykyn on 2011-02-03
> **stalemath said:**
> I know that

Sorry, that wasn't clear from your description of the problem.  Have you checked your samba logs at this point?

My guess is you need to setup unix user-> samba user sync.

---

