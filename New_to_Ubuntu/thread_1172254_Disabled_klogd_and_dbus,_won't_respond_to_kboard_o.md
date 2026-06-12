---
title: "Disabled klogd and dbus, won't respond to kboard or mouse"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by zcacogp on 2009-05-28
Chaps, 

Get ready to laugh. 

I have been having problems with my laptop, newly-installed with 9.04. The problems involve the CPU usage being very high, so I installed Bootup-Manager to look at the processes being started at boot. 

I tried stopping them in turn to see which would bring the CPU usage down. I stopped both klogd and dbus, clicked "confirm", and the machine re-started. More worryingly, when it had restarted, it would respond to neither the keyboard nor the mouse. 

I have tried running the recovery version of ubuntu from GRUB, and tried both "Repair broken packages" (dpkg) and "Try to auto repair graphic problems" (xfix), but neither of them have solved the problem. 

When it boots, it gets to the 'login' screen just fine, but won't respond to either the keyboard or mouse. 

What do I need to do to fix this? (Presumably re-enable klogd and dbus, but I don't know how to do this.) 

Thanks for any help anyone can offer!


Oli.

---

### Post by regala on 2009-05-28
> **zcacogp said:**
> Chaps, 

Get ready to laugh. 

I have been having problems with my laptop, newly-installed with 9.04. The problems involve the CPU usage being very high, so I installed Bootup-Manager to look at the processes being started at boot. 

I tried stopping them in turn to see which would bring the CPU usage down. I stopped both klogd and dbus, clicked "confirm", and the machine re-started. More worryingly, when it had restarted, it would respond to neither the keyboard nor the mouse. 

I have tried running the recovery version of ubuntu from GRUB, and tried both "Repair broken packages" (dpkg) and "Try to auto repair graphic problems" (xfix), but neither of them have solved the problem. 

When it boots, it gets to the 'login' screen just fine, but won't respond to either the keyboard or mouse. 

What do I need to do to fix this? (Presumably re-enable klogd and dbus, but I don't know how to do this.) 

Thanks for any help anyone can offer!


Oli.

1) you disabled dbus, which disabled hald (because it needs dbus to run), which is needed by the X server to enumerate the input devices (keyboard and mouse)
so
2) you need to reenable it: either remotely or locally in a "rescue". try to connect to your machine with ssh, if impossible, go for the "single" session.

3) either way, to reenable the services, you won't be able to use BootManager (which is crap letting you disable such things as dbus or worse, klogd) because you can't use X. you have to use update-rc.d on the cmdline.

to reenable dbus and klogd at their defaults, you have to run these:
# update-rc.d klogd start 11 3 4 5 . stop 89 1 .
# update-rc.d dbus start 12 3 4 5 . stop 88 1 .

if needed, precede each command with sudo (in single mode, won't be)

then reboot.

4) by the way, most CPU time on Desktops are wasted on screenlets :)
and BootManager shouldn't be so much advertised without warning. So easy to break a config, especially when the gentle community tells you how :D

5) I think you should open a bug on Launchpad against BootManager, which should warn with big /!\ /!\ fat /!\ /!\ warning when asked to stop some special services, even tell specifically the risks of stopping dbus.

br, mathieu

PS: if you are able to remotely log on your box using ssh from another Ubuntu/Linux/whatever box with X, you can try with -Y or -X options to ssh, which let you run BootManager remotely (runs there but appears on the display here)

---

### Post by zcacogp on 2009-05-28
mathieu, 

Thanks for your reply. 

I can access the machine via the recovery console, whereby I can login (type "login", and then it asks for a login name and password. This gets me to a familiar looking prompt.) 

I can then put in the two commands you gave me, like this: 

```
# update-rc.d klogd start 11 3 4 5 . stop 89 1 .
# update-rc.d dbus start 12 3 4 5 . stop 88 1 .
```

I then logout (type "logout"), and use "shutdown now" to re-start things. 

BUT, when I get back to the normal login screen the keyboard and mouse still don't respond - i.e. no change. 

I do have another machine (the one I am typing this on, funnily enough!), which is also running 9.04. How do I remotely log into the broken machine using this machine? I know that the ip address of this machine is 192.168.10.6, but I don't know what ip address the other (broken) machine has taken. 

If I call up a terminal and type: 

```
ssh
```

... what do I follow it with? 


Oli.

---

### Post by regala on 2009-05-28
> **zcacogp said:**
> mathieu, 

Thanks for your reply. 

I can access the machine via the recovery console, whereby I can login (type "login", and then it asks for a login name and password. This gets me to a familiar looking prompt.) 

I can then put in the two commands you gave me, like this: 

```
# update-rc.d klogd start 11 3 4 5 . stop 89 1 .
# update-rc.d dbus start 12 3 4 5 . stop 88 1 .
```

I then logout (type "logout"), and use "shutdown now" to re-start things. 

BUT, when I get back to the normal login screen the keyboard and mouse still don't respond - i.e. no change. 

I do have another machine (the one I am typing this on, funnily enough!), which is also running 9.04. How do I remotely log into the broken machine using this machine? I know that the ip address of this machine is 192.168.10.6, but I don't know what ip address the other (broken) machine has taken. 

If I call up a terminal and type: 

```
ssh
```

... what do I follow it with? 


Oli.


For ssh:

when/if you manage to get the ip address (maybe from your router, I don't know, or the boxen are on the same network, with the cache arp on your "not broken" box), you need to do:

ssh -X -l your_login remote_ip, then type your password.

then, on this terminal, any command you run that usually creates a window will create a window on the working display, but running on the other box. This way you can run BootManager remotely and undo what you've done.
(if you get some errors with ssh -X, try ssh -Y, it will soften the security checks on the X server side)

to get your ip, you can boot in recovery mode, and check the ip assigned (if assigned). if not assigned, try on the admin console, dhclient ethX (with the relevant digit instead of X).

another thing: when in recovery mode, can you issue the command "mount" alone and post here the line about "/" ? (maybe the failure in recovery mode, is you have / read-only mounted, or maybe it is mounted elsewhere in the minimal system set up by recovery mode)

anyway, I will try to follow you to help you as problems, obstacles arise; there shouldn't be any need to reinstall, and if so, this is a MAJOR bug. expect me to not be able to reply for a moment, in a while (commute time).

---

### Post by zcacogp on 2009-05-28
Mathieu, 

Thanks. 

The ip address of the remote (broken) machine is 192.168.10.7, according to the display when I boot in as root with networking enabled. 

But, when I use the command you gave: 
```

ssh -X -l ogp 192.168.10.7
```

... it comes back with "Connection refused". 

And the same happens if I use -Y instead. 

(Clearly, ogp is my login and 192.168.10.7 is the ip address.) 

I can ping 192.168.10.7 from the working machine just fine - lots of responses. 

On the broken machine, I have logged in from the root command line, and typed "mount", as you suggested. It produced a screenful of information, but I can't see which bit you mean by 'post the line about "/"'. If you mean the various mounts listed, they are as follows: 
```

/dev/sda7 on / type ext3
tmfps on /lib/init/rw type tmpfs
proc on /proc type proc
sysfs on /sys type sysfs
varrun on /var/run type tmpfs
```

There are more ... do you want the rest? 


Oli.

---

### Post by regala on 2009-05-28
> **zcacogp said:**
> Mathieu, 

Thanks. 

The ip address of the remote (broken) machine is 192.168.10.7, according to the display when I boot in as root with networking enabled. 

But, when I use the command you gave: 
```

ssh -X -l ogp 192.168.10.7
```

... it comes back with "Connection refused". 



means openssh-server is not running :/

> 

On the broken machine, I have logged in from the root command line, and typed "mount", as you suggested. It produced a screenful of information, but I can't see which bit you mean by 'post the line about "/"'. If you mean the various mounts listed, they are as follows: 
```

/dev/sda7 on / type ext3
tmfps on /lib/init/rw type tmpfs
proc on /proc type proc
sysfs on /sys type sysfs
varrun on /var/run type tmpfs
```

There are more ... do you want the rest? 


well it's weird...
stay in recovery mode.
try a simple "touch /hello", does it return an error, a message ? you can get the error code with "echo $?", if it is not 0, there was an error (telling us it is effectively ro mounted)

while you're at it, can you ls -l /etc/rc2.d and post the output, as for the contents of /etc/init.d ?

---

### Post by zcacogp on 2009-05-28
Mathieu, 

I get two different results depending upon whether I am logged into the machine. 

I am booting into Recovery Mode. I am given a number of options, one of which is (something like) "Drop into root prompt with networking". This is the one I am trying, and it gives me a prompt like this: 

```
root@ogp-laptop:~#
```

If I type: 

```
Touch /hello
```at this point, I don't get any result at all - it just gives me the prompt again. 

And if I type 

```
echo $?

```at this point I get a result of 0. 


If I login using 

```
login ogp

```

it asks me for my password, and the prompt changes to 

```
ogp@ogp-laptop:~#
```

Once I have this prompt, the command 

```
touch /hello
```

tells me 

```
touch: cannot touch '/hello': Permission denied". 

```

Also, 

```
echo $?
```gives a result of 1. 


```
ls -l /etc/rc2.d
```gives a page full of results, all in the form 
```
lrwxrwxrwx 1 root root <number> 2009-05-23 <time> <filename>

```

```
/etc/init.d
```also gives a page full of items, from apparmor to x11-common (although there may be more off the top of the page, and I don't know how to make the list pause so I can see a pageful at a time.) 


Oli.

---

### Post by zcacogp on 2009-05-28
Another thought ... is there such a thing as a "repair" option when you use the Ubuntu install disk? I suspect not, or else someone would have suggested it by now. 

Is the ultimate 'silver bullet' to re-install? 

What about copying files from the operational machine to the broken one? Would that help? (Probably not - I'm clutching at straws a bit here.) 


Oli.

---

### Post by zcacogp on 2009-05-29
Anyone? 

I guess I'll have to rebuild if it can't be fixed ... all assistance welcome. 

Thanks. 


Oli.

---

### Post by JKyleOKC on 2009-05-29
> **zcacogp said:**
> mathieu, 

Thanks for your reply. 

I can access the machine via the recovery console, whereby I can login (type "login", and then it asks for a login name and password. This gets me to a familiar looking prompt.) 

I can then put in the two commands you gave me, like this: 

```
# update-rc.d klogd start 11 3 4 5 . stop 89 1 .
# update-rc.d dbus start 12 3 4 5 . stop 88 1 .
```

I then logout (type "logout"), and use "shutdown now" to re-start things. 

BUT, when I get back to the normal login screen the keyboard and mouse still don't respond - i.e. no change. 


If you typed those two lines exactly as shown, with the "# " as the first two characters, try again but leave those two out for each line. The "#" is usually used when showing commands, since it's the standard prompt when in "root" or "su" mode -- but it's also a "comment" character that stops the command shell from paying attention to anything that follows it!

Hope this helps.

---

### Post by zcacogp on 2009-05-31
JKyleOKC, 

Thanks ... wish I had known that before! Pretty stupid mistake to make, I guess. 

As it is, I've rebuilt it now, so it's not relevant. But thanks for answering anyway - it was appreciated. 


Oli.

---

### Post by chrisr710 on 2009-07-28
I had made the same mistake, on Ubuntu 9.04. This thread fixed the issue for me:
[http://ubuntuforums.org/showthread.php?p=7570259](http://ubuntuforums.org/showthread.php?p=7570259)

---

