---
title: "Can't log in...error messages included"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by mtguy on 2011-04-09
I have a multi-boot system with ubuntu 10.04 as my primary partition (where I do most of my work) and xubuntu 10.10 on a secondary partition.  I logged into xubuntu and did a few updates, and mounted my ubuntu partition by following the instructions here:  [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Then when I tried to log into ubuntu, I got the following:

The ubuntu welcome screen, followed by a black screen for a few seconds.  Then a small box appeared on screen that said:

"Could not update ICEauthority file /var/lib/gdm/.ICEauthority"

The only button said "close" so I clicked it and another small box appeared saying:

"There is a problem with the configuration server.
(usr/lib/libconf2-4/gconf-sanity-check2 exited with a status of 256)"

Again, clicked on the close button.

Then got what appeared to be a login screen, but only had my host name on it and no way to sign in.  No menu in the bar below and the only way I could figure out how to get out was to power off and back on.

No idea what happened or how to fix it.  Help would be VERY appreciated.

---

### Post by mtguy on 2011-04-09
Perhaps this question should be asked in a more advanced forum?  I've no idea, so help me out here.

---

### Post by TeoBigusGeekus on 2011-04-09
Boot up in terminal and try
```
sudo chmod 755 /etc/gconf/gconf.xml.system
```

---

### Post by mosquitogang201 on 2011-04-09
Check the file permissions on the files you are having trouble with and make sure you have read write access. Try what the previous poster mentioned and also

ls -l /var/lib/gdm/.ICEauthority

That command will tell you the owner and permissions set on the file. I am typing from KDE so just guessing that it should be owned by root. Then,

sudo chmod a+rw /var/lib/gdm/.ICEauthority

will allow read and write access to everyone. If this is the problem, that command should fix it.

If running the ls -l command shows that the file does not exist, you could try issuing a

sudo touch /var/lib/gdm/.ICEauthority

to create it.

---

### Post by mtguy on 2011-04-09
> **TeoBigusGeekus said:**
> Boot up in terminal and try
```
sudo chmod 755 /etc/gconf/gconf.xml.system
```
How do I boot into a terminal?  I suppose I should mention that I've installed burg and my choices are only the two operating systems.  Burg is intalled from the ubuntu partition into which I cannot boot.  Sorry, but I'm a newbie and still learning.  I've tried lots of stuff and been able to follow directions pretty well, so far only minor problems, but this one nailed me.

Thanks for the reply.

---

### Post by mtguy on 2011-04-09
> **mosquitogang201 said:**
> Check the file permissions on the files you are having trouble with and make sure you have read write access. Try what the previous poster mentioned and also

ls -l /var/lib/gdm/.ICEauthority
How to I do that?  If I type that into a terminal, it will just tell me what is present in the xubuntu partition, right?

> That command will tell you the owner and permissions set on the file. I am typing from KDE so just guessing that it should be owned by root. Then,

sudo chmod a+rw /var/lib/gdm/.ICEauthorityI cannot get into the ubuntu partition at all, so how do I do that?

> will allow read and write access to everyone. If this is the problem, that command should fix it.

If running the ls -l command shows that the file does not exist, you could try issuing a

sudo touch /var/lib/gdm/.ICEauthority

to create it.I appreciate your reply, but I cannot get into the ubuntu partition so I can only run commands from the xubuntu partition.  I imagine there is a way to get into the ubuntu partition from xubuntu, but at this point I'm quite skittish about trying anything that isn't specific instructions for my situation.  Still a newbie and learning.

---

### Post by TeoBigusGeekus on 2011-04-09
Don't you have the option to boot into recovery mode?

---

### Post by mtguy on 2011-04-09
> **TeoBigusGeekus said:**
> Don't you have the option to boot into recovery mode?
Chalk it up to stupidity, but no.  I installed Burg from the ubuntu partition and now I have a nice pretty screen that gives me exactly 2 options: Ubuntu or Xubuntu.  That's it. #-o

---

### Post by mtguy on 2011-04-09
BTW, I can access the partition from Xubuntu...can I just open thunar as root, scroll to the appropriate folder, and create a new file called .ICEauthority and give it permissions for everyone?  Will that work?

---

### Post by TeoBigusGeekus on 2011-04-09
No.
Navigate to your ubuntu partition from xubuntu and give 
```
chmod 755 /etc/gconf/gconf.xml.system
```
It shouldn't require sudo. Try then to reboot to ubuntu.

---

### Post by mtguy on 2011-04-09
> **TeoBigusGeekus said:**
> No.
Navigate to your ubuntu partition from xubuntu and give 
```
chmod 755 /etc/gconf/gconf.xml.system
```It shouldn't require sudo. Try then to reboot to ubuntu.
Thanks, I'll give that a shot.  Hopefully I'll reply on the other side :)

---

### Post by TeoBigusGeekus on 2011-04-09
> **mtguy said:**
> Thanks, I'll give that a shot.  Hopefully I'll reply on the other side :)

Wait a minute. On second thoughts, giving this as the file's path will try to change ownership for the xubuntu's file.
Better navigate in the correct ubuntu folder from xubuntu and simply give
```
chmod 755 gconf.xml.system
```

---

### Post by mtguy on 2011-04-09
> **TeoBigusGeekus said:**
> Wait a minute. On second thoughts, giving this as the file's path will try to change ownership for the xubuntu's file.
Better navigate in the correct ubuntu folder from xubuntu and simply give
```
chmod 755 gconf.xml.system
```
Okay, well, I tried the first one, got "operation not permitted" and did it with sudo, but it didn't work, got the same two error messages and no way to log in.  I'll see if gconf.xml.system is where it's supposed to be in the ubuntu partition from xubuntu.

---

### Post by mtguy on 2011-04-09
Here's what I did and it didn't work:

Opened a terminal and typed this:
cd /media/79445867-9f40-4259-a139-68b1047b45a8/etc/gconf

The long number is the UUID of the ubuntu partition.

Then issued the following command:
sudo chmod 755 gconf.xml.system

Was asked for pass, gave it, then hit enter and got returned to a prompt, so assumed everything was ok.

Exited terminal, rebooted, got same two error boxes :(

---

### Post by TeoBigusGeekus on 2011-04-09
See [this]("http://ubuntuforums.org/showthread.php?t=917306") thread.

---

### Post by mtguy on 2011-04-09
> **TeoBigusGeekus said:**
> See [this]("http://ubuntuforums.org/showthread.php?t=917306") thread.
<sigh>
Tried every solution mentioned in that thread, none of them worked.

Thanks for trying ;)

---

