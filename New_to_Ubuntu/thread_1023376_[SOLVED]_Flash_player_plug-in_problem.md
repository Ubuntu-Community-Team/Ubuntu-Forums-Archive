---
title: "[SOLVED] Flash player plug-in problem"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by mariane_08 on 2008-12-27
After using Hardy for several month I did a clean install of Intrepid. So far so good. Except for one thing...

On one website I regularly visit Firefox prompted me to download a plug-in. Specifically Abobe macromedia Flash. It gave me 3 options:
Adobe Flash itself
SWF-DEC player for flash
and a third option that I dont exactly remember.

I chose the second, i.e. the swf-dec player. 

However, now when I visit the above site and try to use the built in player it freezes and the screen goes grey. I can only get out by force closing. It would seem that this is all caused by Flash. 

How do I remedy this? did I choose the wrong plug-in? I can easilly do a fresh install tomorow but I will still need to know what to avoid!

---

### Post by appi2012 on 2008-12-27
type this in the terminal:
```
sudo apt-get uninstall swf-dec
```

then type
```
sudo apt-get install flashplugin-nonfree
``` or just [click here]("apt:flashplugin-nonfree") in firefox to do the same thing.

That should switch the flashplayer to the adobe version

---

### Post by dtrot55 on 2008-12-27
ummmmm....i keep getting 

dtrot@ubuntu:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for dtrot: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree


from both terminal and clicking on that link...any idea?

---

### Post by Miljet on 2008-12-27
Go to System-> Administration-> Software Sources. Make sure that all entries are ticked except Source code. Click on Third-Party Software tab and tick the entry for medibuntu.

Then go back to the terminal and try the install again.

---

### Post by mariane_08 on 2008-12-28
OK I did the radical thing since I woke early and couldn't sleep and just reinstalled. So when I'm prompted for this again I take I should choose the first  option, i.e. flash player-non free. 

For some reason  was inclined to avoid that. But is known problem with swf-dec and similar plug-ins or was it just my bad luck? I know under windows somepeople have trouble with flash player

---

### Post by mariane_08 on 2008-12-28
OK the options Plugin Finder lists are:

Adobe Flash (thats the non free right?)
SWF-DEC
Gnash

Must admit I'm a little concerned it will screw me up again! But I brave up and try it later!

---

### Post by appi2012 on 2008-12-28
I haven't tried the others, but i'm sure that adobe flash has the best compatibility. Here, non free means non free as in speech, meaning the software is closed source, so ubuntu can't fix any bugs with it, only Adobe can. But it is still 0$, so you don't have to pay  for it.

---

### Post by kansasnoob on 2008-12-28
I'd just install ubuntu-restricted-extras. It's in synaptic or just go to terminal and:

```
sudo apt-get install ubuntu-restricted-extras
```

I also find that flashblock improves overall flash performance and saves system resources. It's also in synaptic or:

```
sudo apt-get install flashblock
```

Restart Firefox after installing new add-ons.

---

### Post by zvacet on 2008-12-28
@ **mariane_08**

In terminal type

```
gksudo gedit /etc/apt/sources.list
```

and add this line to your source list

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

save and close file.

```
sudo apt-get update
```

In synaptic search box type **adobe-flashplugin** and when you find it just install.

---

### Post by mariane_08 on 2008-12-28
> **appi2012 said:**
> I haven't tried the others, but i'm sure that adobe flash has the best compatibility. Here, non free means non free as in speech, meaning the software is closed source, so ubuntu can't fix any bugs with it, only Adobe can. But it is still 0$, so you don't have to pay  for it.

Yes you're probably right. Maybe the fact that it's not open source made me avoid it initially! Anyway I installed it and it works just fine with no problems. 

Thanks!

---

