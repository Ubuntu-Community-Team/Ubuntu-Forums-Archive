---
title: "help: I've lost my python!"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by bebops_lost on 2009-06-12
ok, so I am running jaunty (9.04) on my hp1314 laptop, and I was trying to run a program with a known bug due to Python2.6 (the latex gedit plugin.) 
I opened up synaptic and installed Python 3.0, but the problem persisted (I imagine because something about my system was still reverting to python 2.6 by default) So that's when I decided to remove Python2.6 
-BIG MISTAKE!- (stupid, I know, but I thought I'd at least get a warning message if I was about to cripple my system -apparently not.)

Now basically nothing works. I can't access the internet (I'm writing this from my desktop) can't access my home directory, can't open terminal, etc. I'm using the ctrl-alt-F1 trick to at least use bash. since I can't use apt-get install from the web to get python2.6 back because I have no internet access, so I burned another cd and am trying to get the packages from the cdrom.

this is how I'm trying to do it:
I go to /etc/apt/ and move the sources.list file to some other name (so it doesn't try looking on the internet) and then I type
```
 $sudo apt-cdrom add
```
which adds a line to sources.list telling apt-get to look in the cd that I've popped in the drive.
after that I go with ```
$sudo apt-get install python2.6
```

and it tells me that it is only available from another package, and suggests python2.6-minimal. So I think "ok, install that", but then it tells me that python2.6-minimal is already the newest version. I'd like to reinstall python2.6-minimal, but when I try to remove it (and then install again), it says 

"You are about to do something potentially harmful"
"This should NOT be done unless you know exactly what you are doing"

and a bunch of other ominous-sounding warning messages (which I really would have appreciated *_before_* I removed python 2.6 in the first place:mad:.) Should I do it anyway ? I feel like I have nothing to lose.

I can't upload my data, because I can't mount anything, so repartitioning and installing from scratch means losing a lot of data and about a week of work. Am I boned? any ideas on how I can get the python back in its cage?
any help you can offer sincerely appreciated.
-B

---

### Post by furialis on 2009-06-12
Since no one else has a suggestion, I'll try.

I would boot to a LiveCD and move everything I wanted to save to a USB drive. Then, ignore the warning and plow through. How much more damage can you do?

I have borked my system at least a 100 times trying things I had no ideas about. Then I learned about [remastersys.](http://www.remastersys.klikit-linux.com/ubuntu.html") I make a backup whenever I make some major changes, that way if I break something, I don't have to go that far back and I can reinstall in about 15 mins without losing anything.

Good Luck.

---

### Post by bebops_lost on 2009-06-13
Hi furialis
Thanks for the tip. I booted with the live cd and got all my data off of the HD, so at the very least, I haven't lost any work.

after plowing through with the command:
```
sudo apt-get remove python2.6-minimal
```
I lost no functionality from before, (I had little to lose) but when I try to install it again I get:

```
Package python2.6-minimal [*or 3.0-minimal when I try that*] is not available, but is referred to by another package [*though they don't suggest any*] 
...
E: Package python2.6-minimal has no installation candidate

```

So it seems I will have to at least go through reinstallation and remount/reinstall all my programs/etc :roll: (but thanks for suggesting remastersys -that'll avoid this problem in future) 

I'll hold off reinstalling for the moment in case anyone else can suggest a reason why apt-get doesn't seem to want to grab packages from the cd.
in any case, thanks furialis.

---

