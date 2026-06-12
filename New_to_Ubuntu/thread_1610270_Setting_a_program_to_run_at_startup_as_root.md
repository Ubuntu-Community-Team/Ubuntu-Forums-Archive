---
title: "Setting a program to run at startup as root"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by d58e7 on 2010-10-31
I want to run wondershaper at startup but it requires that I run it as sudo. So how would I go about having the command run at startup?

ie. sudo wondershaper eth1 x x

---

### Post by TeoBigusGeekus on 2010-10-31
Add the command to /etc/rc.local

---

### Post by I'mGeorge on 2010-10-31
> **d58e7 said:**
> I want to run wondershaper at startup but it requires that I run it as sudo. So how would I go about having the command run at startup?

ie. sudo wondershaper eth1 x x

Go to your terminal and type sudo visudo. A text file will pop out in your terminal, go to the line where's  

```

root    ALL=(ALL) ALL    

```

in ubuntu under 'root    ALL=(ALL) ALL' there should be a line like 'user.name    ALL=(ALL) ALL' probably looking like this

```

root    ALL=(ALL) ALL
user.name    ALL=(ALL) ALL    

```

anyway under the line 'root    ALL=(ALL) ALL' you should write a line that would look like this

```

root    ALL=(ALL) ALL
user.name   ALL=NOPASSWD: /path_to_your_program_bin_file

```    

where user.name it's the name u are using to log in. After editind press F2 and enter to confirm saving. What this will do it's that when you will use sudo no password will be required and this will help you to run that program of yours at startup.

!!! I've modified my post 'cause I have to agree it's not safe to advise anybody to do that. So the proper way to do this would be "user.name   ALL=NOPASSWD: /path_to_your_program_bin_file" so only that program could be executed with sudo without the use of a password. Sorry for doing a post that could had endangered your PC especially if you're connected at a local network> I didn't thought much at that moment 'cause I have this bad habit to believe most people have the same Internet connection as I do, the same PC configurations and so on, though I know this it's impossible that's my first impressiom he he :-) Cheers

---

### Post by TeoBigusGeekus on 2010-10-31
> **I'mGeorge said:**
> Go to your terminal and type sudo visudo. A text file will pop out in your terminal, go to the line where's  

```

root    ALL=(ALL) ALL    

```

in ubuntu under 'root    ALL=(ALL) ALL' there should be a line like 'user.name    ALL=(ALL) ALL' probably looking like this

```

root    ALL=(ALL) ALL
user.name    ALL=(ALL) ALL    

```

anyway under the line 'root    ALL=(ALL) ALL' you should write a line that would look like this

```

root    ALL=(ALL) ALL
user.name   ALL=NOPASSWD: ALL 

```    

where user.name it's the name u are using to log in. After editind press F2 and enter to confirm saving. What this will do it's that when you will use sudo no password will be required and this will help you to run that program of yours at startup.

Won't this compromise his whole system?

---

### Post by holiday on 2010-10-31
Look into changing the permissions on the executable. Applications should not be running as root, however you can create a special user that has the permissions required for the application. Look through the /etc/passwd file and you'll see many "users" with specific permission sets. That's the way we do it. 

Having said that, I do run some applications as root, but I understand that if I were doing it right, I would never have to.

---

### Post by JKyleOKC on 2010-10-31
Yes, it will. Preferable solution is to add the command to /etc/rc.local, just in front of the line in that file that reads "exit 0" and without the "sudo" at the front. The rc.local file runs at boot time, as root. Also, if the program is not in the "usual" program locations known to the boot process, it will need its full pathname rather than just "wondershaper" so that the process can find it.

---

### Post by I'mGeorge on 2010-10-31
> **TeoBigusGeekus said:**
> Won't this compromise his whole system?

It depends, but mostly it should be alright

---

### Post by Morbius1 on 2010-10-31
Since I had no idea what wondershapper was I googled it and it sent me back here:
[http://ubuntuforums.org/showthread.php?t=25911](http://ubuntuforums.org/showthread.php?t=25911)

See if that makes any sense.

If not and since this is a networking application you might consider creating a script and adding it to:
```
/etc/network/if-up.d
```Any script added to that directory will be run (by root so you don't need the "sudo" part) only after the network is up.

---

### Post by AngusH on 2010-10-31
> **holiday said:**
> Look into changing the permissions on the executable. Applications should not be running as root, however you can create a special user that has the permissions required for the application. Look through the /etc/passwd file and you'll see many "users" with specific permission sets. That's the way we do it. 

Having said that, I do run some applications as root, but I understand that if I were doing it right, I would never have to.

Surely you need root to run some applications? That's the entire reason root is there... so you can do stuff that needs root privs (like install software).
Angus

---

### Post by ayenack on 2010-10-31
> **Morbius1 said:**
> Since I had no idea what wondershapper was I googled it and it sent me back here:
[http://ubuntuforums.org/showthread.php?t=25911](http://ubuntuforums.org/showthread.php?t=25911)

See if that makes any sense.


+1

This seems like the best solution to me and it'll work.

Don't change permissions as indicated earlier.

If you want to run an sudo command at startup use crontab. This would run RKHunter.

[B]sudo crontab -e

@reboot /usr/bin/sudo rkhunter -c -sk[/B]

Here's an excellent crontab guide.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by holiday on 2010-10-31
> **AngusH said:**
> Surely you need root to run some applications? That's the entire reason root is there... so you can do stuff that needs root privs (like install software).
Angus

You may be right. You are absolutely right that root is required to install an operating system, but it is possible to install applications to a user's home directory and only that user and root can execute that application.

Root has access to everything, but there is no application that requires access to everything. An image viewer does not need access to your sound card - unless it's also a video player, in which case,yes, it needs access to the sound card. 

But it doesn't need access to everything. 

For good security you want to make sure that an application has access to only those resources that it needs. Determining that access can be a lot of work, but so is taking care of the backyard.

---

### Post by d58e7 on 2010-10-31
Thanks for your help, everyone :)

---

### Post by anewguy on 2010-10-31
> **holiday said:**
> You may be right. You are absolutely right that root is required to install an operating system, but it is possible to install applications to a user's home directory and only that user and root can execute that application.

Root has access to everything, but there is no application that requires access to everything. An image viewer does not need access to your sound card - unless it's also a video player, in which case,yes, it needs access to the sound card. 

But it doesn't need access to everything. 

For good security you want to make sure that an application has access to only those resources that it needs. Determining that access can be a lot of work, but so is taking care of the backyard.

And......that's the reason the folks behind Ubuntu have decided to not have the root login enabled by default and instead have us use "sudo" when we need such priviledges.  Provides that one little extra layer of protection that stops someone from just always (or for that matter, ever) logging in as root and doing something they don't realize compromises the entire system - be it security, messing up of files/folders, etc..

Dave ;)

---

