---
title: "Watching Movies"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by Timoteo32 on 2009-12-24
I tried to watch a DVD on my laptop and it says i need to install a plugin. I clicked "search for suitable plugins" it came back empty :/  I'm still new to Ubuntu and not sure where to go now to get the update I need.  Or can't I watch movies on here?  For the record, it's a legal DVD that I purchased :P

---

### Post by taurus on 2009-12-24
Here's a link for you.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by hansdown on 2009-12-24
Hi Timoteo32.

Not sure which version of ubuntu you have, but this should help for 9.04 and 9.10.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Haha. taurus is fast!

---

### Post by Timoteo32 on 2009-12-24
okay, so i'm blindly following stuff i read :P  Mostly cause I trust you guys and everyone here has been very nice.  I can't get any viruses on here tho right?  I am running 9.04

Also, I don't know where else to turn when I have questions so I just post here.  Is that cool or am I violating some unwritten rule?

---

### Post by taurus on 2009-12-24
No virus to worry about and if you have questions, just create new threads.

---

### Post by howefield on 2009-12-24
> **Timoteo32 said:**
> okay, so i'm blindly following stuff i read :P  Mostly cause I trust you guys and everyone here has been very nice.  I can't get any viruses on here tho right?  I am running 9.04

If you can't trust staff at ubuntuforums, who can you trust ?

You'll be safe following those links.

But, you are very right to be cautious ;) keep it up.

---

### Post by cartisdm on 2009-12-24
Yes, always use your brain when taking advice but rest assured the people of these forums are very trustworthy.

As for having to install those plugins, Ubuntu doesn't supply those out-of-the-box due to legal reasons.  Let us know if you have any problems installing those plugins

---

### Post by Timoteo32 on 2009-12-24
well i copied the code from the first link into Terminal (I feel like I'm back in Dos lol) and it ran a bunch of stuff but it still didn't play my movie. I got the same message about not having the right plugins.  The laptop came with Dell PowerDVD and that seems to be playing it fine tho, just not in Totem.

---

### Post by greyfox1 on 2009-12-24
Try running this command in Terminal:

```
sudo sh /usr/share/doc/libdvdread4/install-css.sh
```

The guides posted above are useful because they will help you get other things working, but this command is specific to getting DVD playback working. [Here]("http://ubuntuforums.org/showthread.php?t=1306282&highlight=install-css.sh") is another thread where others are talking about it (including a certain Fox you may recognize).

Also, get used to the Terminal now, trust me. It will be your best friend eventually, like it or not, so you might as well get used to the idea. ;)

---

### Post by Timoteo32 on 2009-12-24
Terminal doesn't scare me as I did grow up using Dos and still remember a surprising amount of commands. I'm just not enthused about learning a whole new language. :/

So I paused and minimized the movie to do a few things online and when I opened it up, it was locked up.  Now I can't unfreeze it or close it. Is there something like Task Manager in Windows where I can force quit and/or see if it's actually responding? I'm sure there is cause they have one in the Mac OS and Windows but I have no clue how to get to it here.

Also, I was unable to use that link above :(
> sh: Can't open /usr/share/doc/libdvdread4/install-css.sh

---

### Post by Geoff918 on 2009-12-24
> **Timoteo32 said:**
> Terminal doesn't scare me as I did grow up using Dos and still remember a surprising amount of commands. I'm just not enthused about learning a whole new language. :/

So I paused and minimized the movie to do a few things online and when I opened it up, it was locked up.  Now I can't unfreeze it or close it. Is there something like Task Manager in Windows where I can force quit and/or see if it's actually responding? I'm sure there is cause they have one in the Mac OS and Windows but I have no clue how to get to it here.

Yeah, you can do a ton of different things here.

The easiest is probable Alt-F2

Type xkill into the box

you will get an 'x' cursor. It will kill whatever window you click on.

---

### Post by cartisdm on 2009-12-24
> **Geoff918 said:**
> Yeah, you can do a ton of different things here.

The easiest is probable Alt-F2

Type xkill into the box

you will get an 'x' cursor. It will kill whatever window you click on.

You can also add the Force Quit app to your panel, which is pretty handy at times

Right-click on a Panel ---> Add to Panel ---> Add Force Quit

---

