---
title: "faliure with x server probs"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by skeebs on 2009-04-16
Hi all,

I'm so spanking new to all this... but really keen to learn and become competent at it!

Ok, I'm having a prob much like this user:

[http://ubuntuforums.org/showthread.php?t=1077378&highlight=failed+to+start+the+x+server](http://ubuntuforums.org/showthread.php?t=1077378&highlight=failed+to+start+the+x+server)


I've upgraded my pc and have a new motherboard and new hard drive with no OS installed on it. I've tried booting it up from my old hard drive (which has a problematic version of Mandriva 08 on it) but it wasn't recognising my hard drive even though the BIOS is set up ok.

So now trying to boot up by using ubuntu and installing it on to my new hard drive. I've tried booting up from the disk, tried runnin it from the cd without installing it, anything I do throws the "faliure with the x server" problem message up. I've searched around past forums but not found a solution to this.

The above thread is very close to my problem, but isn't resolved on here.

I tried a few things as suggested by various users on other threads/forums. I don't know what they all mean yet and can't quite remember everything as been trying this for a good few hours now!! So here are some of the things, hope it's helpful to anyone who wants to answer....

my original message, after following diagnostic promts, gives:

[B]log fie: "/var/log/Xorg.o.log
using config file: "/etc/xll/xorg.conf"

Fatal server error: no screens found[/B]

"xstart" gives:

[B]no screens found
XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.[/B]

sudo X -configure gives

[B]using config file: "/home/ubuntu/xorg.conf.new"
X org is not able to detect your mouse
edit the file and correct the device
your xorg.conf file is /home/ubuntu/xorg.conf.new
to test the server, run '/home/ubuntu/xorg.conf.new'[/B]

so I typed that in and got:

[B]Invalid argument for -config
For non-root users, the file specified with -config must be a relative path and must not contain any ".." elements using default xorg.conf search path[/B]

So don't know what that was about :(

I can't remember what command it was but somewhere along the line I was told I wasn't in root so couldn't do it...

There we go. Hope someone can be patient enough to help out!! Please please do and I will pass on the knowledge to other newbies when I finally have it :D

---

### Post by Hospadar on 2009-04-16
On a more basic level, what kind of video hardware are you using?

---

### Post by skeebs on 2009-04-16
I've not got any fancey additions, just whats built into my mother board which is an "amd athlon"... Is that what you mean? :?

---

### Post by skeebs on 2009-04-16
...oh hold on it says my in motherboard info that it has NVIDIA Geforce75050PV/nForce 630a integrated chipset and uses NVIDIA PureVideo... think that answers it!

---

