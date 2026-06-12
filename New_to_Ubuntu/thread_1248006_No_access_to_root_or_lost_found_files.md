---
title: "No access to root or lost/ found files"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by preta on 2009-08-23
Hi, all:
Currently using NBR 9.04 on an ASUS eee 1000HE and enjoying it immensely. Just one question, I noticed when browsing my file directory in Nautilus that access  is blocked to my 'root' and 'lost + found' files. There is a big 'x' next to the file icons and when I double click on the folder I get a message that says, "you do not have the permissions necessary to view the contents of 'root' or 'lost + found' (depending on which was selected). 

I am the only user on my system. The manual I'm using (the Ubuntu book, 3rd ed., which was written for 8.04) states that /root "is the home directory for the main superuser." So, I guess my questions are:

1) Is it possible for me to access these directories?
2) Is there someting I can do to let Ubuntu know that I wish to be recognized as the main superuser (if this is possible)?

Ther reason I am asking is because I am coming across power users who are always telling other forumites to ensure they placed some dependency or file in root. 

Any help you can provide would be greatly appreciated

Thank you.

---

### Post by marcusesses on 2009-08-23
The command

```
gksudo nautilus
```

should work for you. 'gksudo' is a command for accessing graphical commands as superuser.

You could also access the filesystem from a terminal using 

```
sudo cd /lost+found
```.

As usual though, be careful!

---

### Post by ajgreeny on 2009-08-23
>  /root "is the home directory for the main superuser.I am very surprised that any guide says exactly that, without explaining a bit further.
The main, or first user of ubuntu is able to get root privileges, ie, become superuser, but is not the main superuser without using sudo, or gksudo for gui applications , in front of the command used.  Therefore as marcussesses says in his post, when you open nautilus with gksudo, you are able to do activities as root, ie, as superuser.

For more information on root and sudo have a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by loomsen on 2009-08-23
> **preta said:**
> Hi, all:

1) Is it possible for me to access these directories?


As for /root:

Yes, you gotta login as root. From a terminal you could do 
su -l
<enter your password>
and you'll be dropped to /root.

However, /root shouldn't be used, no need to neither. The "forumites" saying to place files to root usually mean /.
/root isn't really used.

> 
2) Is there someting I can do to let Ubuntu know that I wish to be recognized as the main superuser (if this is possible)?


Using sudo should usually cover most tasks you need superuser permissions for.
However, there are some situations where sudo isn't satisfying, for instance if you want to alter some hardware state by 
echo VALUE > DEVICE
In this case you may use 
su -c 'command to run'

I recommend using sudo for any tasks and if possible avoiding a login as root (actually it usually does more harm running things as root than it provides advantages)

If you need/want to change a file you lack write permissions on for example, copy the file to your userspace, edit it there, and then only put it back into place using sudo (after you backed the original file up).
```

cp /foobar ~/foobar
nano ~/foobar
#save and close foobar
sudo cp /foobar /foobar.orig && sudo cp ~/foobar /foobar

```
Is the safe way to edit files which arent in your home dir.
You should whenever possible avoid running commands as root.

See [http://ubuntuforums.org/showpost.php?p=7834923&postcount=4](http://ubuntuforums.org/showpost.php?p=7834923&postcount=4)

---

### Post by preta on 2009-08-23
Thanks, Marcusesses:
This is going to sound foolish,  (I'm a complete newb so that probably goes without saying): What, from a precautionary standpoint, should I be paying attention to if I decide to start fiddling about with something like, oh say, a realtime audio kernel (which activity I am by no means ready to attempt). Also, is the "gksudo nautilus" command above something I would be entering in terminal? Please realize any confusion is completely my own and thank you very much for your prompt and courteous reply.

---

### Post by preta on 2009-08-23
Thanks marussesses, loomsen and ajgreeny:
I think my primary confusion stemmed from conversations in which users were referring to '/' instead of actually manipulating anything as a superuser.  Thank you all for your input as it will be of great help if decide to labor under the delusion that I can make a go of pro audio on ubuntu. And AJ, I looked again at the guide and you were right, they were simply describing what that directory was and did not define the term "superuser"; probably because they assumed I wasn't going to need to access these files immediately or at all. 

Thanks, again

---

### Post by loomsen on 2009-08-23
Btw, lost+found is a folder used internally by your filesystem, so nothing in there you would want to know of.

---

### Post by marcusesses on 2009-08-23
Yes, type "gksudo nautilus" in teh command line.

As for what to watch out for, my rule of thumb is the more dependencies a program requires, the less I muck about with it. So I usually don't mess around with anything in the root directory unless I KNOW for absolute certain that it won't completely destroy the X-server, for example (which I have done before. Luckily, I fixed it).

As long as you're sure you know what you're doing, then it's ok. You sound relatively inexperienced, so I'd make sure I knew what I was doing before I logged in as root and messed with things. 

Anywya, if you use common sense (as most people do), then you have nothing to worry about.

---

