---
title: "line 59 error in update manager"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by juano_1987 on 2010-12-02
When I tried to update my system package manager I get the following error.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 59 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Any ideas as to what I have corrupted

---

### Post by sikander3786 on 2010-12-02
Welcome to forums :-)

As it suggests, there is some problem in line 59 in your sources.list and this probably is something like an extra "

Lets see. Go to Applications > Accessories > Terminal and post the output of this command. Copy/paste from terminal into your post here.

```
cat /etc/apt/sources.list
```

---

### Post by juano_1987 on 2010-12-02
juan@juan-MM061:~$ cat /etc/apt/sources.list
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
“deb  
“deb  
“deb  
deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) maverick restricted main multiverse universe
deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) maverick restricted main multiverse universe
deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) maverick-updates restricted main multiverse universe
deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) maverick-updates restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe
  
juan@juan-MM061:~$

---

### Post by sikander3786 on 2010-12-02
Edit your sources.list by,

```
gksudo gedit /etc/apt/sources.list
```

Delete these 3 lines completely.

```

&#8220;deb
&#8220;deb
&#8220;deb 
```

And comment this one with a # in the beginning,

```
deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
```

So that it looks like,

```
#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
```

You can also try to remove all the free space on top of all those lines and bring the newly commented line to line no. 1 in that file. It would only clean up the file. No problem if you don't do that.

Now save and close that file and run this command.

```
sudo apt-get update
```

Good Luck!

---

### Post by e79 on 2010-12-02
All the credits should go to 'sikander3786' but I'll throw in my $0.02. Simply delete the first 3 lines that has nothing else than **&#8220;deb**; it should solve your problem.

Hope this helps

EDIT * Posted it 5 seconds after sikander3786 answer lol...follow his advice  =P

---

### Post by juano_1987 on 2010-12-02
Thanks a lot [sikander3786]("http://ubuntuforums.org/member.php?u=806649") i resolve the problem with you help +10

---

### Post by sikander3786 on 2010-12-02
> **juano_1987 said:**
> Thanks a lot [sikander3786]("http://ubuntuforums.org/member.php?u=806649") i resolve the problem with you help +10
You are Welcome :-)

Now you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

> All the credits should go to 'sikander3786' but I'll throw in my $0.02. Simply delete the first 3 lines that has nothing else than &#8220;deb; it should solve your problem

Correct but the CD-ROM was added as a repository in the OP's sources.list and it'd have thrown an error message every update/upgrade unless the Maverick CD-ROM was inserted in the drive.

Regards.

---

