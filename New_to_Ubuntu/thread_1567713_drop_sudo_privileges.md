---
title: "drop sudo privileges"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by jeslinmx on 2010-09-04
running wine with sudo messes things up big time, i read. so if i were to say do something like "sudo apt-get install something" and after that i want to use wine, is there a fast way to get rid of sudo?

---

### Post by Silent Warrior on 2010-09-04
I think there's a notification-thingy that will let you do that... but I can't be 100% sure. I know for a fact, however, that running a command using su -c 'insert command here within apostrophes' drops root-privileges immediately after finishing.
I'm not sure how it works, but I think sudo is more like on-demand - once active, any application THAT ASKS FOR ROOT-PRIVILEGES seems to get them without prompting for up to 15 minutes (?). If an app doesn't ask for root, which I've never seen Wine or any Windows-y software I've ever run on my end do, it won't magically act like it is elevated.
In short:
Avoid sudo wine something, as you already know.
Look through your applets for something about Policy.
Try su -c 'apt-get update/install' instead of sudo.

---

### Post by t0p on 2010-09-04
I don't understand your problem.  *sudo* operates if you invoke it, ie

```
sudo apt-get install jugglingelephants
```

I can't think of any reason why you'd want to run wine with sudo.  So *don't* type in the command

```
sudo wine
```

and you should experience no problems.

---

### Post by Silent Warrior on 2010-09-04
The original poster knows that full well. What he/she is concerned about is whether sudo-privileges might carry over to other processes started after a sudo-command is run.

---

### Post by da burger on 2010-09-04
I don't think sudo will give root to any application unless that application is prefaced with sudo or gksudo when started.

```
&#9484;&#9532;&#9472;&#9532;&#9472; angus @ angus-laptop &#9472;&#9508;&#9500;&#9472; 12:34:53 Sat Sep 04 &#9472;&#9508;&#9500;&#9472; ~ &#9472;&#9508; 
&#9492;&#9532;&#9472;$&#9472;&#9508;&#9654;sudo echo stuff
[sudo] password for angus: 
stuff
&#9484;&#9532;&#9472;&#9532;&#9472; angus @ angus-laptop &#9472;&#9508;&#9500;&#9472; 12:35:02 Sat Sep 04 &#9472;&#9508;&#9500;&#9472; ~ &#9472;&#9508; 
&#9492;&#9532;&#9472;$&#9472;&#9508;&#9654;apt-get install cowsay
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
&#9484;&#9532;&#9472;&#9532;&#9472; angus @ angus-laptop &#9472;&#9508;&#9500;&#9472; 12:35:14 Sat Sep 04 &#9472;&#9508;&#9500;&#9472; ~ &#9472;&#9508; 
&#9492;&#9532;&#9472;$&#9472;&#9508;&#9654;

```

You may have had an application that "asks" for sudo, which achieves it through relaunching it self with gksudo if it detects it is not being run as root (unetbootin does this). I don't think wine will do this as I can see no reason for it to want to.

Angus


EDIT: Something else I thought I'd mention although you don't really need it (explained above). If you want to force sudo to ask for a password you can do the following: ```
&#9484;&#9532;&#9472;&#9532;&#9472; angus @ angus-laptop &#9472;&#9508;&#9500;&#9472; 12:49:19 Sat Sep 04 &#9472;&#9508;&#9500;&#9472; ~ &#9472;&#9508; 
&#9492;&#9532;&#9472;$&#9472;&#9508;&#9654;sudo echo
[sudo] password for angus: 

&#9484;&#9532;&#9472;&#9532;&#9472; angus @ angus-laptop &#9472;&#9508;&#9500;&#9472; 12:49:27 Sat Sep 04 &#9472;&#9508;&#9500;&#9472; ~ &#9472;&#9508; 
&#9492;&#9532;&#9472;$&#9472;&#9508;&#9654;sudo -k
&#9484;&#9532;&#9472;&#9532;&#9472; angus @ angus-laptop &#9472;&#9508;&#9500;&#9472; 12:49:32 Sat Sep 04 &#9472;&#9508;&#9500;&#9472; ~ &#9472;&#9508; 
&#9492;&#9532;&#9472;$&#9472;&#9508;&#9654;sudo echo
[sudo] password for angus: 


```

As you can see when I ran sudo -k, sudo forgot the password it had remembered.

---

