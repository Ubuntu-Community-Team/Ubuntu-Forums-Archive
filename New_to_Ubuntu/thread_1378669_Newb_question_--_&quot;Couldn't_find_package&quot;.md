---
title: "Newb question -- &quot;Couldn't find package?&quot;"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by enjoytrees on 2010-01-11
This has happened a couple of different times for different packages. b43-fwcutter, ndiswrapper, and a few others perhaps that I can't remember... and now with fortune-mod.

I am trying to get fortune-mod because every time I try to run Wanda the Fish, a prompt appears that reads "Unable to locate the command to execute". 

As per the advice in this thread ([http://ubuntuforums.org/showthread.php?p=8077345](http://ubuntuforums.org/showthread.php?p=8077345)), I opened my terminal and typed the following: 

sudo apt-get install fortune-mod

which yielded the following: "Couldn't find package fortune-mod"

Why can't I ever find any packages???! :(

---

### Post by Sef on 2010-01-11
What version of Ubuntu are you using?

---

### Post by tom.swartz07 on 2010-01-11
> **enjoytrees said:**
> This has happened a couple of different times for different packages. b43-fwcutter, ndiswrapper, and a few others perhaps that I can't remember... and now with fortune-mod.

I am trying to get fortune-mod because every time I try to run Wanda the Fish, a prompt appears that reads "Unable to locate the command to execute". 

As per the advice in this thread ([http://ubuntuforums.org/showthread.php?p=8077345](http://ubuntuforums.org/showthread.php?p=8077345)), I opened my terminal and typed the following: 

sudo apt-get install fortune-mod

which yielded the following: "Couldn't find package fortune-mod"

Why can't I ever find any packages???! :(

if you ever run into this problem, you have 2 options.
type ```
apt-cache search "name"
``` where 'name' is the name of the package that you are looking for


ORR

open synaptic package manager system>admin>synaptic
and search for it there in the box


That being said- ill show you a little trick= hit ALT and F2 type ```
free the fish
``` that should have your little trick. :D

Hope this helps!

---

### Post by howefield on 2010-01-11
Fortune-mod is available with synaptic, didn't check the others you mention. This link is for Karmic, but it exists in all the others.

[http://packages.ubuntu.com/sl/karmic/fortune-mod](http://packages.ubuntu.com/sl/karmic/fortune-mod)

Try opening Synaptic Package Manager, in Settings > Repository > Ubuntu Software tab, ensure main, universe, restricted, and multiverse are all checked.

---

### Post by enjoytrees on 2010-01-11
9.10 ...

---

### Post by enjoytrees on 2010-01-11
> **howefield said:**
> Fortune-mod is available with synaptic, didn't check the others you mention. This link is for Karmic, but it exists in all the others.

[http://packages.ubuntu.com/sl/karmic/fortune-mod](http://packages.ubuntu.com/sl/karmic/fortune-mod)

Try opening Synaptic Package Manager, in Settings > Repository > Ubuntu Software tab, ensure main, universe, restricted, and multiverse are all checked.

Just tried searching for it using Synaptic and it "fortune-mod" didn't even show up. Also, all four of the repositories are checked.

I don't know what I'm doing wrong :(.

As a side note, I did the "free the fish" thing. THAT worked. Now I can't make her go away! :P

---

### Post by howefield on 2010-01-11
> **enjoytrees said:**
> Now I can't make her go away!

Doesn't clicking on the fish make it go away ?

Haha, no it doesn't... it comes back.

Edit.

This does it :)
killall gnome-panel

---

### Post by Sef on 2010-01-11
From the terminal copy and type this code:

```
sudo apt-get update &&  sudo apt-get install fortune-mod
```

What does it say if it does not install.

---

### Post by albert s on 2010-01-11
> **tom.swartz07 said:**
> if you ever run into this problem, you have 2 options.
type ```
apt-cache search "name"
``` where 'name' is the name of the package that you are looking for


ORR

open synaptic package manager system>admin>synaptic
and search for it there in the box


That being said- ill show you a little trick= hit ALT and F2 type ```
free the fish
``` that should have your little trick. :D

Hope this helps!


I just had to do that free the fish thing,   :D:D:D:D:D
I LOVE it, 
made me laugh out loud

---

### Post by enjoytrees on 2010-01-11
> **howefield said:**
> Doesn't clicking on the fish make it go away ?

Well, yes, temporarily. Then after about a minute she swims back on screen o.O

My biggest concern is not being able to use Synaptic or find packages, though :(

---

### Post by wojox on 2010-01-11
```
sudo apt-get update && sudo apt-get install fortune-mod
```

---

### Post by enjoytrees on 2010-01-11
> **Sef said:**
> From the terminal copy and type this code:

```
sudo apt-get update &&  sudo apt-get install fortune-mod
```What does it say if it does not install.

I think it worked! I am downloading 180 updates presently, maybe that was my problem lol. Just did a fresh install today.

Also, it appears that fortune-mod installed from the command line as well. I am cautiously optimistic at this point... :)

SUCCESS! Thank you all so much for your help.

---

