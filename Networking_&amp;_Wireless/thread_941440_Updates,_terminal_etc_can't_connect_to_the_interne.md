---
title: "Updates, terminal etc can't connect to the internet"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by tivey on 2008-10-08
Hi, fairly new to ubuntu starting using it a couple of months ago. Just moved to university and for some reason the updates can't connect to the server and I can't connect through the synaptic package manager either. Firefox and Opera both work as I've changed the connection settings to automatic proxy config and typed in the URL the uni provided me with. Other apps work fine such as evolution and pidgin without any problems too.

I'm guessing that I just need to change a few settings in the network settings?

Thanks

---

### Post by Marshal0505 on 2008-10-08
Never had any similar problems , but a quick forum search revealed this post

[http://www.ubuntuforums.org/showthre...997#post652997](http://www.ubuntuforums.org/showthre...997#post652997)

[http://www.google.nl/search?q=university+blocking+apt+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a](http://www.google.nl/search?q=university+blocking+apt+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a)

Hope it helps

---

### Post by tivey on 2008-10-08
Hi thanks 

[http://ubuntuforums.org/showthread.php?p=652997#post652997](http://ubuntuforums.org/showthread.php?p=652997#post652997)

This seems like it could be the solution however I can't figure out how to add to the bash.bashrc file??

Thanks

---

### Post by Marshal0505 on 2008-10-08
> **tivey said:**
> Hi thanks 

[http://ubuntuforums.org/showthread.php?p=652997#post652997](http://ubuntuforums.org/showthread.php?p=652997#post652997)

This seems like it could be the solution however I can't figure out how to add to the bash.bashrc file??

Thanks

Easy way is to open a terminal by pressing alt+f2 and typing 'terminal'.

Also, it's good practice is to backup system files before editing them,so start with
```
sudo cp /etc/bash.bashrc /etc/bash.bashrc.old
```

Once that's done you can proceed with the instructions from the other thread

```
gksu gedit /etc/bash.bashrc
```

All this does is open the bash.bashrc file in a text editor so you can add the text given in the instructions.

Add your lines and save the file before closing it.
Voila, You're done

Ps:I did not take the effort in reading the other thread, but I hope it helps you.

---

### Post by tivey on 2008-10-08
Followed the instructions from the other thread but it hasn't worked. Any more ideas?

Thanks

---

