---
title: "Firefox &amp; VMWare"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Synt4xError on 2009-01-30
I had VMWare running perfect. Installed a driver that screwed a few things up. I reversed the problems. But now I can't access my VMWare through firefox browser.

VMWare 2.0 ([https://127.0.0.1:8333](https://127.0.0.1:8333))
It use to work perfectly fine before the sound driver I tried to install!!! :(

ANyone got any ideas?

---

### Post by yeats on 2009-01-30
Just for clarity's sake - you are running some sort of server program with VMWare and you've verified that VMWare itself and the virtual server are running correctly?  Is this a problem with VMWare or with Firefox?

---

### Post by Synt4xError on 2009-01-30
The problem is with firefox I suppose. I know for a fact I didn't touch any settings for VMWare. 

Firefox just says "Firefox can't establish a connection to the server at 127.0.0.1:8333"

So it seems something is being blocked. I made a blacklist and all but I think I got rid of all the blacklist files I made.

Thanks for your reply..

---

### Post by Synt4xError on 2009-01-30
Can anyone help me out with this? It's for my studies, and I can't do anything. I really do not feel like re-installing. Honestly, I don't even know where to start for uninstalling. 

Anyone know anything about VMWare and Ubuntu?

---

### Post by pytheas22 on 2009-01-31
What is the output of:
```

netstat -a | grep 8333
```

Are you sure that 8333 is the right port for your VMware server and that it didn't get changed somehow?  I don't have any experience with VMware (I prefer VirtualBox) and I'm not quite sure what you're doing accessing it in a web browser (is it over VNC or something?), but obviously the first thing to do is make sure that the port is correct.

Also, do you have any luck connecting if you put:
```

localhost:8333
```

in the address bar instead of 127.0.0.1:8333?

And if you open Firefox from a terminal (by typing 'firefox') and then try to connect to VMware, do you get any output in the terminal that's relevant to the problem?  Probably not, but worth a try.

Finally, can't you just open your virtual machine normally, through the VMware player?  Is there a reason you need to access it via Firefox?

---

### Post by Synt4xError on 2009-01-31
There is no output of netstat -a | grep 8333.

I am dealing with Server 2 Beta x64 for linux. The instructions say use a web browser to the address [https://127.0.0.1:8333](https://127.0.0.1:8333) or 8222. The old windows way is VMware player. And that is just workstation.

localhost is the same as 127.0.0.1, I don't get any response on that.

When opeing firefox from terminal, I get the same error.

See, I installed a sound driver. I don't really remember exactly what I did, but I blacklisted Alsa and some other programs. I fixed the blacklist, but I don't know what else to do. I am lost.

I don't even know where any of the config files are in linux.

Like, is there any type of file I could have made to make this not work? If so, is there a certain place that file should be? 
How do I search in Ubuntu for file/folders?

I mean, I guess I canfigure it out on my own, I just need a bit of advice using ubuntu, or even linux period..

Thanks for your reply!

---

### Post by pytheas22 on 2009-01-31
Having never used VMware server personally, I can't easily tell you where to look to figure out what's wrong.  If 'netstat -a | grep 8333' returns nothing, then it means that no service is listening on port 8333, which implies that your virtual machine is either not running at all, or is on a different port.  Does 'netstat -a | grep -i vmware' return anything?

Do you get any errors when you try to start the virtual machine?  Do you have any proof that it's actually running?

You might want to look at dmesg in case there's a clue there about why it won't start, or if VMware keeps its own logs (they'd most likely be inside /var/log somewhere), check that.

Finally, are you sure that the address is http**s**://localhost:8333, not simply [http://...?](http://...?)  Notice http vs https.

---

### Post by Synt4xError on 2009-02-01
Sorry for the late reply. I had to re-install. It's work fine now, since it is a fresh install.

I was going insane the other night so I just sat there and re-installed VMWare. Thanks for ur help though!

---

### Post by ibuclaw on 2009-02-01
heh, was just browsing through this thread thinking "I wonder if he has recompiled the vmware modules for the kernel he is running".
But glad you have figured it out before I mentioned it :)

Next time, I think running this may rectify your problem:
```
sudo vmware-reconfigure.pl
```
At least, I think that is what it is called... I haven't really used VMWare since it turned 2.0.

Regards
Iain

---

