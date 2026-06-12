---
title: "Can't update (Xauthorization issue?)"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by pyrofyr on 2008-12-31
I tried running the update and keep getting this error. I like 'just' installed Ubuntu dual boot last night (Other OS is Vista/Longhorn).

Read around but the other problems don't seem to be related to mine, tried looking up the error and get no information.

```
Failed to run /usr/sbin/synaptic --dist-upgrade-mode --non-interactive --hide-main-window -o Synaptic::AskRelated=true as user root.

Unable to copy the user's Xauthorization file.
```

---

### Post by adult swim on 2008-12-31
go to a terminal and enter in ```
ls -la | grep .Xauthority
``` and paste the results here.

---

### Post by pyrofyr on 2008-12-31
Gonna probably have to reinstall. Not sure what's up but now it keeps telling me to make /home/pyrofyr/desktop before running Nautilus so I can't even get to the terminal.. (unless there is some other shortcut way), I can't run anything that uses it because of it, and Firefox stuff is gone.

I'm guessing I'd have to re-install Ubuntu to do this? I don't mind, because of the lack of changes I've made to it so far.

---

### Post by adult swim on 2008-12-31
the only thing i saw that would cause this problem was .Xauthority being owned by the wrong group/user.  did you do any permissions changes on anything?  
try hitting ctrl+alt+f2  and then login.  enter in ```
sudo chown pyrofyr:pyrofyr .Xauthority
``` if your username is not pyrofyr, change it to your username
to get back to X youll need to hit ctrl+alt+f7.  let me know how it works out.

---

### Post by pyrofyr on 2009-01-01
I'll restart now and try that. Just to let you know however, I haven't messed with any properties.

I had tried taking a screenshot and moved the screenshot from /pyrofyr to /pyrofyr/pictures, maybe somehow it messed up and moves the wrong thing? /hmm

I'll try what you said now.

---

### Post by pyrofyr on 2009-01-01
It's telling me that the file cannot be found. /hmm

I'm guessing in some crazy awkwardness that I don't know of AT ALL I apparently deleted import stuff? No one touched my PC, and I was careful not to screw with stuff (Don't wanna mess nothin' up!) so yeah... not sure how this happened either way, bleh.

---

### Post by pyrofyr on 2009-01-01
Purely out of curiosity and to get this resolved quicker, is there a way to just like restore normal settings, or re-install right over where it was or something?

---

### Post by pyrofyr on 2009-01-01
Okay, tried reinstalling, having the same problem, hahaha.

Did the terminal thing you said, here are the results:
-rw-------  1 pyrofyr pyrofyr   125 2009-01-01 14:27 .Xauthority

---

### Post by adult swim on 2009-01-01
what happens when you run ```
sudo apt-get update

sudo apt-get upgrade
```

---

### Post by pyrofyr on 2009-01-01
I just tried again and was able to do the updates, it's downloading them now anyway.

I checked my Desktop and it's back, so Nautilus works now...
The only thing (and I plan on trying to fix it asap) is that Firefox won't save any bookmarks, they decide to die every time I restart, and also for some reason the back button never lights up, as in it's unusable, not sure what's up with that -scratches head again-

---

### Post by adult swim on 2009-01-01
thats weird.  close firefox, go to to your home folder, hit ctrl+h and then delete the folder .mozilla
then open firefox back up and add a bookmark, close/open firefox back up and see if it saved

---

### Post by pyrofyr on 2009-01-02
Well, bleh seems like I'm running into so many issues! Now everytime I try and do everything (even save an mp3 or something) it's telling me I'm out of space, and when I click on File System it tells me 0 bytes leftover, but the awkward thing is that I had given it 16GB of space, I'm not sure if the update or reinstalling it messed it up.

When I reinstalled everything seemed fine. Now that I updated when I get to the boot screen it gives me 2 ubuntu options (not counting memtest86+, or the secondary ones under each one), for 2 different versions.

--
I read in the thing that 5GB would be sufficient which l is why I gave it 15GB, and I checked it out, and it has taken the whole 15GB! D=

How much should I give it so that it can be 'happy'? I'm guessing I'll need to toss a good deal of my music on an external again, even though I have 70GB of space right now.

--
Okay, I've looked up some stuff, and it looks like I made a mistake by installing it before getting a lot more information. I'm going to go ahead and play with the Live CD a bit more, but things like making a seperate partition from both of the OSes to share files, etc I should have known before hand and would have been nice to, but I followed an ubuntu wiki guide.

In any case, it's also probably better if I wait till I get my new desktop setup (later this month, probably third week)

I'll just search around for a guide to uninstall now.

---

### Post by adult swim on 2009-01-02
if you are dualbooting with windows, when you delete the ubuntu parition, you will have a grub error on a reboot.  if you have your windows install cd its easy to repair the mbr.  if you dont have the windows install cd, it is still easy to repair the mbr.

---

### Post by pyrofyr on 2009-01-02
I was just about to ask that, because my searches led me to horror.

How do I go about repairing that? I have other PCs in the house, and I have the CDs, but I'd have to head out back to find the CDs.

--
Would I need a second PC present to fix the mbr error?

---

### Post by adult swim on 2009-01-02
not at all.  if you have an xp install cd, boot it and go to the recovery console.  then enter in ```
fixboot

fixmbr

exit
```
if it is vista, boot the vista cd, get to the command prompt and run ```
bootrec /fixboot

bootrec /fixmbr

exit
```

if cant find them and have a blank cd, get super grub disk, [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) burn it to a cd and boot off of it.  then i think you go to windows in the menu and then choose fix mbr

---

