---
title: "rc.local doesn't really work, huh?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by zeeple on 2009-01-23
I am running Ubuntu 8.10.  This file exists: /etc/rc.local, and that file I do not believe had existed in previous versions of ubuntu.  I am guessing that this was added to silence the undying complaints that while getting a command to run at boot was trivial in other distros, getting a command to run at boot in ubuntu is a challenge.

Regardless, according to the comments in this file you can add commands that will be run at boot, after everything else had started, but I find that on my system this is not the case.  For example, I added the simple:

echo "isengard has booted" | mail [email]me@domain.com[/email] -s 'izzy booted'

to the rc.local file and this email did not go out upon reboot.  (I tried the command at the prompt first to make sure it worked and it did.)  So I figured, okay, maybe the problem is that eth0 was not up yet and so the mail couldn't go out.  So I added the even simpler:

echo "hello" > /root/boot.greeting

to rc.local and I find that this also does not run, leading me to conclude that this file is not being included in the myriad of startup scripts during my systems boot process.

What do I need to do to get this to work?  Thanks!

---

### Post by kerry_s on 2009-01-23
> that file I do not believe had existed in previous versions of ubuntu

it's been there. is the file executable? did you modify it in some other way?

---

### Post by cariboo on 2009-01-23
Adding programs to start on boot is pretty easy. Have a look at update-rc.d, you can get the basic commnds at the prompt by typing:

```
sudo update-rc.d
```

for more indepth info type:

```
man update-rc.d
```

Jim

---

### Post by albinootje on 2009-01-23
> **zeeple said:**
> leading me to conclude that this file is not being included in the myriad of startup scripts during my systems boot process.


I'm using /etc/rc.local since quite a while (years), with various success.
The success things were things like :

```

killall -9 mysqld safe_mysqld
/etc/init.d/mailman restart
echo "nameserver 10.1.1.1 > /etc/resolv.conf
/etc/init.d/networking restart

```

while other things refused to work, don't remember specific examples right now, but /etc/rc.local should usually work, at least for certain things.

---

### Post by zeeple on 2009-01-23
hi, thanks for the reply.  The file is indeed executable, in fact an ls -l on it reveals:

-rwxr-xr-x 1 root root 502 2009-01-23 17:17 /etc/rc.local

I have not changed it in any other way, yet I have fairly conlcusive evidence it is not running. In order for it to run it has to be linked somewhere, right?  Perhaps the link is missing??

---

### Post by albinootje on 2009-01-23
> **zeeple said:**
>  I have not changed it in any other way, yet I have fairly conlcusive evidence it is not running. In order for it to run it has to be linked somewhere, right? 

You only need to properly fill in the commands in /etc/rc.local
(Properly as in leaving the last line as it is)
That's all.

---

### Post by sdennie on 2009-01-23
Try:

```

ls -l /etc/rc5.d

```

At the bottom you should see 99rc.local symlinked to ../rc.local.

---

### Post by zeeple on 2009-01-27
> **sdennie said:**
> Try:

```

ls -l /etc/rc5.d

```

At the bottom you should see 99rc.local symlinked to ../rc.local.

Hi sdennie, I see you are from Buenos Aires.  My wife grew up in Argentina and we have friends from Buenos Aires.  BA is very close to our hearts.

ls'ing the dir you suggested, as well as rc3.d and rc4.d revealed that rc.local was indeed symlinked.  FYI I ran a bunch of system updates and now 

/etc/init.d/local

seem to be executing the simple command:

echo "hello" >> /root/boot.greeting

but rc.local will not execute the same command.

I would like to solve the mystery of rc.local, though, since that seems to be set up explicitly for running miscellaneous boot time commands.

---

### Post by albinootje on 2009-01-28
> **zeeple said:**
>  I would like to solve the mystery of rc.local, though, since that seems to be set up explicitly for running miscellaneous boot time commands.

I just tested the following :
1) Had a completely empty /root/boot.greeting 
   (not sure whether that's needed, but FYI)
2) My /etc/rc.local looks like this :
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/bin/echo "hello" >> /root/boot.greeting

exit 0

```

3) Tested it, and it works!

---

