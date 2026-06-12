---
title: "Windows 7 boot option gone, Direct boots to ubuntu 10.10"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by nicedevil on 2011-04-23
Hello......
 I'm new to this forum and ubuntu too....... yesterday night i installed ubuntu 10.10 netbook edition, after installation windows 7 booting option gone my netbook direct boots the ubuntu gives me no other option..
Is there anyone who can help me up solving this problem.. i tried running boot info script but i failed in that one too.....

---

### Post by cobra1984 on 2011-04-23
this thread may help:

[http://ubuntuforums.org/showthread.php?t=158075](http://ubuntuforums.org/showthread.php?t=158075)

---

### Post by fabricator4 on 2011-04-23
> **nicedevil said:**
> Hello......
 I'm new to this forum and ubuntu too....... yesterday night i installed ubuntu 10.10 netbook edition, after installation windows 7 booting option gone my netbook direct boots the ubuntu gives me no other option..
Is there anyone who can help me up solving this problem.. i tried running boot info script but i failed in that one too.....

When you installed Ubuntu did you tell it to install alongside another OS, or did you tell it to use the whole disk?

We really need the information from the boot info script to help you.  You just need to make the script executable and run it with bash.  If you used the defaults you probably downloaded it to your Downloads directory.  Us the following commands to run the script. Change the first command in you saved it to some other directory or moved it somewhere:


Open a terminal window:  <ctr><alt>t
```

# this line changes from ~/ to ~/Downloads where the script should be
cd Downloads

# this line changes the file permissions so that it is an executable script
chmod +x boot_info_script055.sh

# this line executes the script
sudo bash boot_info_script055.sh 


```

You should now have a file called RESULTS.TXT with the information to copy for us.

Chris

---

### Post by varunendra on 2011-04-23
> **nicedevil said:**
> i tried running boot info script but i failed in that one too.....
Well maybe you missed the instructions on the boot info script's description page. There's a pretty good stepwise detail with example on how to use it. Please read them top to bottom, it'll take less than two minutes:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If the normal steps don't work (which is quite unlikely), try including the steps [fabricator4]("http://ubuntuforums.org/member.php?u=761043") suggested above.

And the RESULTS.txt file would definitely be needed to properly understand the current layout of operating systems on your HDD.

---

