---
title: "Termianl traning.."
date: 2009-05-11
forum: New to Ubuntu
---

### Post by qjmoss on 2009-05-11
I'm interested in learning the terminal, in depth, does anyone have any references that I could read, or could someone give me some tips.

My knowledge is limited to an extent. 

:guitar:


excuse the typo in the subject line.
; )

---

### Post by Kosimo on 2009-05-11
You can start here

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

[http://ubuntuforums.org/showthread.php?p=990636](http://ubuntuforums.org/showthread.php?p=990636)

---

### Post by qjmoss on 2009-05-11
When I said that my experience is limited, I meant, i want to learn giving permissions, and being able, in a sense to not use my GUI and use the terminal.


Leon.. Well, I guess he thinks he's funny..


but thank you so much!

---

### Post by tarps87 on 2009-05-11
> **qjmoss said:**
> When I said that my experience is limited, I meant, i want to learn giving permissions, and being able, in a sense to not use my GUI and use the terminal.


Leon.. Well, I guess he thinks he's funny..


but thank you so much!

Just reading your latest post
```
man chmod
man chown
```

Quick refernce

```
sudo chmod ugo+rwx file
```
u = user
g = group
o = other
a = all

+ = add
- = remove/deny

r = read
w = write
x = execute

```
sudo chown you:me file
```
changes the owner to *you* and the group to *me*
Note: You don't need to use sudo for file you own

common options

-r = recursive (Act on a file and folders within the give folder)
-f = force

That should get you going

---

### Post by qjmoss on 2009-05-11
Thank you so much, I just got enrolled to get my bachelors in Internet security/Cisco computer networking/Unix management.

So I'm trying to get ahead of the game, my instructor said that there is a lot of terminal commands that i should be getting used to before starting my courses.

You can see why I'm a little annoyed of the smart *** remarks from some people.

Thank you so much for your time.:P

---

### Post by Skrynesaver on 2009-05-11
The unix permissions system is quite simple.
Every file/directory has three levels of access

[LIST]
[*]    Owner - the owner of the file
[*]    Group - other users in the same group of as the file is created with
[*]    World - everyone else
[/LIST]
 when you ls -l you see something like
```

me@home$ ls -l ~/tmp
-rwx------  1 root root       108 Apr  6 14:43 MENU.pl
drwxr-x---  1 me users        56 May  7 10:55 data
-rw-r-----  1 me users      6172 Mar 23 10:28 URLMod.pl.diff

```The first is the special features of the file(eg. d => directory) then the following groups of three are the read, write and execute permissions for each of the above.

Now it gets messy, each of the access levels can be summed up as an octal (base 8 ) number.

[LIST]
[*]4->read
[*]2->write
[*]1->execute
[/LIST]
so if I wish to set a file so that I have all permissions, anyone in my group can read and execute and anyone else can't access the file, i can set the permissions by changing the mode thus.```
chmod 750 filename.sh
``` Never mind this is in danger of becoming an eassay, here's [a tutorial on permissions]("http://www.webmonkey.com/tutorial/Modify_User_Permissions")

Hope that clarifies

---

### Post by AXeS on 2009-05-11
was gona suggest g0ogle,but kosimo is the man. n0 sud0 pun intended. ss64 seems to help me alot.

d0nt know h0w u pe0ple feel ab0ut it but the man pages are al0t t0 take in yet d0nt give en0ugh examples 0n h0w t0 use the flags 0r h0w t0 pipe pr0perly. and thanx tarp.

sudo rm -f LeonBlade

---

### Post by SunnyRabbiera on 2009-05-11
Lucky for you the terminal is almost a thing of the past in linux, there are a lot of tools and stuff to make Linux easier.
Though it seems in many ways Ubuntu is becoming more terminal reliant, especially when trying to get better screen resolutions on certain cards/monitors.
I miss displayconfig-gtk.

---

### Post by Bodsda on 2009-05-11
Hi, heres a link to an amazing cli resource, its soooo long! :)

[http://ubuntuforums.org/showthread.php?t=842307](http://ubuntuforums.org/showthread.php?t=842307)

That should keep you busy for a while :)

Hope this helps,

Bodsda

---

### Post by Wiebelhaus on 2009-05-11
A simple google search will provide you with such results:

[The best of all:]("http://gd.tuwien.ac.at/linuxcommand.org/")

[https://help.ubuntu.com/7.04/basic-commands/C/](https://help.ubuntu.com/7.04/basic-commands/C/)

and here's some cheet sheets:

[Ubuntu]("http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/")

[Linux]("http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/")

[Ubuntu guide]("http://www.ubuntupocketguide.com/index_main.html")

Be a sport and buy the last one!

---

### Post by qjmoss on 2009-05-11
Thank you everyone, so much


If anyone/or if you know anyone that has got there CCNA, or in the process please let me know.. 

I would like to talk with some networking specialists.. =)

Get me started on this journey

---

### Post by tarps87 on 2009-05-11
> **qjmoss said:**
> Thank you so much, I just got enrolled to get my bachelors in Internet security/Cisco computer networking/Unix management.

So I'm trying to get ahead of the game, my instructor said that there is a lot of terminal commands that I should be getting used to before starting my courses.

You can see why I'm a little annoyed of the smart *** remarks from some people.

Thank you so much for your time.:P

That's ok.

A couple of useful commands for networking:

ifconfig = list/manage lan interfaces
iwconfig and iwlist for wlan interfaces

I've done the first to semesters of the cisco qualification, I may be worth looking a using hyper terminal, at the time this was used to talk to the routers. I don't know what is used now though.

Edit: Why do I type so slow, in answer to the post above, I have CCNA1 and 2, or that's what they were referred to it a couple of years ago. I haven't had a chance to do any work with Cisco equipment for a while so am some what rusty but am willing to help where I can. If you are enrolled of the Cisco cause you should be given access to their academic site, this is probably the best sauce of information when it comes to the Cisco part

---

### Post by qjmoss on 2009-05-11
How did you like the classes, i hear they're pretty tough.

---

### Post by qjmoss on 2009-05-11
Well, could I just add you to my contacts list and maybe we could chat a little on the subject?

---

### Post by tarps87 on 2009-05-11
> **qjmoss said:**
> How did you like the classes, I hear they're pretty tough.

I didn't find them to bad, there is a lot to take in a first. It was unfortunate that the option was only available for my last year of collage so didn't get a chance to finish the second two semesters. I had a chance to start it again at uni but decided on a different networking option.

I have just thought of a couple of other bit for the Cisco, the [OSI model]("http://en.wikipedia.org/wiki/OSI_model") is bound to come up.
It is also likely that there will be some binary conversions and possibly some hex
Also [IPv4 classes]("http://en.wikipedia.org/wiki/Subnetwork#IPv4_classes")
These may not all be looked at but were some of the things involved when took the Cisco course.

> **qjmoss said:**
> Well, could I just add you to my contacts list and maybe we could chat a little on the subject?

Sure, I can only tell you what happened for the Cisco part when I took it.

---

### Post by steviefordi on 2009-05-11
When I first installed Ubuntu I went looking for a good command line tutorial. The best one I found, and I highly recommend is at:

[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

It starts off with the real basic stuff and moves on to writing bash shell scripts - unlocking the real power of the command line.

After following the tutorials on this site I went from feeling like a green newbie to a confident command line user. I pretty much use the command line for anything I can now, and I always point people wishing to learn at this site.

A couple of extra things not covered in the tutorial but which are really useful, especially when trawling log files are 'regexp', 'grep' and 'sed'. I'll let you look them up, but I would do the tutorials first.

Good luck with everything and if you get stuck you'll usually find help in these forums (you may just have to ignore the occaisional person who thinks he's funny).

---

