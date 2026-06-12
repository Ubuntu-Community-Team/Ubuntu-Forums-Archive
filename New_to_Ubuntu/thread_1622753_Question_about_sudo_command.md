---
title: "Question about sudo command"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by ericstrom on 2010-11-15
Running 10.04 , Lucid. 

If I type sudo into the terminal, I get the following message :

usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
            username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...

What is this message telling me ? Since it is not prompting me for a password, do I assume the system is setup without the need for a password ?

---

### Post by yetiman64 on 2010-11-15
> **ericstrom said:**
> Running 10.04 , Lucid. 

If I type sudo into the terminal, I get the following message :

usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
            username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...

What is this message telling me ? Since it is not prompting me for a password, do I assume the system is setup without the need for a password ?

sudo is placed before another command in terminal to raise the commands privileges to that of root for a short period of time (gksudo should be used when the command is a graphical application). I think the timeout period for sudo is about 5 minutes before the password is again required in that instance of the terminal.

You will need to enter your password, but note the terminal won't show it being entered, then press enter.

---

### Post by MSPdwalt on 2010-11-15
sudo by itself is not a complete command.  Sudo essentially means "do this as root".

Example: ```
sudo apt-get update
```

---

### Post by IkeFalson on 2010-11-16
What was said above, SUDO translates roughly as Super User DO I think.  Note also if you are going to run a graphical program you should use  "gksu" instead of "sudo".

Ike

---

### Post by Rubi1200 on 2010-11-16
For more information, please read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2010-11-16
> **ericstrom said:**
> Running 10.04 , Lucid. 

If I type sudo into the terminal, I get the following message :

usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
            username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...

What is this message telling me ? Since it is not prompting me for a password, do I assume the system is setup without the need for a password ?

Although cryptic at first, often Linux will provide informative error messages.

In addition to the above comments, take the time to read and understand the output.

The output is telling you how to use sudo, more specifically what the options are. For details , I urge you to learn to read the man pages

[http://manpages.ubuntu.com/manpages/maverick/en/man8/sudo.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/sudo.8.html)

I understand the messages are cryptic at first, but it is well worth the effort to take the time to learn to interpret what they are telling you.

+1 for using gksu for graphical applications.

---

### Post by mcduck on 2010-11-16
> **IkeFalson said:**
> What was said above, SUDO translates roughly as Super User DO I think.  Note also if you are going to run a graphical program you should use  "gksu" instead of "sudo".

Ike

That would be *Substitute User Do*, just like "su" stands for "Substitute User". 

It can be used to execute commands as any user, not just root. It's just that it defaults to root if you don't specify any user.

```
sudo -U user somecommand
```

---

### Post by IkeFalson on 2010-11-16
Thanks mcduck! Though I'm kinda sad to find out it doesn't stand for super user, I took great pleasure in being able to be the super user! :-)

---

### Post by mcduck on 2010-11-16
> **IkeFalson said:**
> Thanks mcduck! Though I'm kinda sad to find out it doesn't stand for super user, I took great pleasure in being able to be the super user! :-)

No need to be sad, root *is* a [superuser]("http://en.wikipedia.org/wiki/Superuser"), so you can be one too, albeit only temporarily. :)

---

