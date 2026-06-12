---
title: "Silly question--wireless startup without login"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by iscariot on 2008-08-17
I tried searching but either got a mound of answers or none at all.  I've a wireless machine that I've gotten to work fine, but the wireless card only works after I login.  How do I get the wireless card to connect without logging in locally?  I need to be able so ssh into the thing and control it remotely.

---

### Post by DGortze380 on 2008-08-17
> **iscariot said:**
> I tried searching but either got a mound of answers or none at all.  I've a wireless machine that I've gotten to work fine, but the wireless card only works after I login.  How do I get the wireless card to connect without logging in locally?  I need to be able so ssh into the thing and control it remotely.

You're either going to need to add a script to run at startup (init.d I think) or set auto login for a user with VERY few privileges. since you're going to ssh to the machine you can just ssh as your user. not sure realistically how secure either of those options are, but they should work.

---

### Post by iscariot on 2008-08-17
I an do with a script.  How do I go about writing a script?

---

### Post by DGortze380 on 2008-08-17
> **iscariot said:**
> I an do with a script.  How do I go about writing a script?

I can through something together tonight. but quick lesson...

1st line MUST be 

```

#!/bin/bash

```

after that just add the commands you need.

Add it to /etc/init.d and it should run at start up. Someone else jump in if I missed anything.

---

### Post by lswest on 2008-08-17
nothing wrong with the above, but it's a bit more complicated than just "adding it to init.d" you have to do this: ```
sudo cp /path to script/Wireless.sh /etc/init.d/Wireless.sh
sudo chmod 755 /etc/init.d/Wireless.sh
update-rc.d Wireless.sh defaults
```

Where the script is what I called "Wireless.sh" and the first command copies the script from whereever you made it (probably the desktop?) to /etc/init.d/, the second line sets the permissions (755 means read and execute access for everyone and also write access for the owner of the file) and the last one sets up the links for boot to execute the file.

I always do this with my wireless, because it survives kernel upgrades too, meaning you won't have to re-add ndiswrapper to /etc/modules (none of my cards are supported out of the box).

---

### Post by iscariot on 2008-08-17
Thanks, I knew that part.  I just haven't done wireless from the command line in awhile.

---

### Post by lswest on 2008-08-17
> **iscariot said:**
> Thanks, I knew that part.  I just haven't done wireless from the command line in awhile.

No problem, good luck with it all.

---

### Post by iscariot on 2008-08-25
What exactly do I put in the script anyway?

---

### Post by DGortze380 on 2008-08-25
> **iscariot said:**
> What exactly do I put in the script anyway?

A script is just a collection of commands. It needs to start with this statement to tell the computer to run it in a Bash Shell (or your choice of shell, just make sure it's installed):

```

#! /bin/bash

```

there is a lot you do with scripts, but for a VERY simple one, you might just want to put the command to start your wireless card. Something like:

```

sudo ifup wlan0

```

You can use loops and even whole other languages to make scripts do a lot of different things. Search or google shell scripting.

---

### Post by iscariot on 2008-08-25
I hate to reply to my own post but you can do it by using the /etc/network/interfaces and putting a bunch of information in there

The only problem I have now is when I try to reboot I get some sort of recovery screen how do I fix this?

---

### Post by dmizer on 2008-08-25
All the information you needed was in the sticky at the top of this forum called [How To: Manual Network Configuration without the need for Network Manager](http://ubuntuforums.org/showthread.php?t=684495)

Your recovery console is probably related to this command:
```
update-rc.d Wireless.sh defaults
```
I'm not exactly sure what it does, but you'll need to remove its effects. I'm still researching this, but it could be a while before I come up with an answer because I'm at work.  I believe it may add the Wireless.sh script to /etc/rc.local ...

---

### Post by iscariot on 2008-08-25
I'm not using wireless.sh.  I altered my /etc/network/interfaces to start it

---

