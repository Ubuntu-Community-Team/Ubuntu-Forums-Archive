---
title: "Booting ubuntu 9.10 &quot;Mount of filesystem failed&quot;"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by enetic on 2010-04-11
I just updated my parents computer yesterday to 9.10.. everything worked perfectly yesterday, and then i turned it off last night, and today ubuntu has trouble mounting the filesystem... theres also a commandline so i can try to apply some commands, but what should i write?

thanks 

Enetic.

---

### Post by SwatKat on 2010-04-11
I had a similar problem once. 
```
fsck
```in the maintainence shell fixed it. But I guess it would be easier for others to help you if you told what the error message is, exactly. Hope this helps. Good luck!

---

### Post by Bob Bertrands on 2010-04-11
Hey 

First thing you have to do is post your dmesg-file:

```

dmesg>dmesg.txt

```then, assuming you don't have internet acces on the pc, plug in an usb-stick and

--just press the tab-key a few times after you've typed in /media/ to find out what to put instead of (mountpoint usb stick)

```

cp dmesg.txt /media/ (mountpoint usb stick)

```

and post the dmesg.txt file here

---

### Post by freesitebuilder on 2010-04-11
Here's the thread:
[http://ubuntuforums.org/showthread.php?t=1305434&highlight=fsck](http://ubuntuforums.org/showthread.php?t=1305434&highlight=fsck)

I still haven't fixed it completely - I'm hoping a clean install in a couple of weeks will fix it. :(

---

### Post by enetic on 2010-04-11
"fsck" that solved it :) thanks

---

### Post by enetic on 2010-04-12
It seems that im having some trouble with the gdm (gnome desktop manager) after this upgrade. after the computer has been running for a while, i cant open any of the installed programs, and the window manager is just showing me wierd letters and pictures.. it also seems that im still having some slight issues with the fsck command, because sometimes i have to apply it again. i have never experienced this after all these years with ubuntu, so im not that familiar with it.. i hope somebody could still help?

thanks.. 
enetic.

---

### Post by deadramonesxx on 2010-07-14
i'm having the same problem and i can't figure out how to get it to work. when typing fsck i get
 
Error reading black 1606906 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error<y>?
 
Force rewriting<y>?
 
i hit Y after both and i get the same message and i just keep hitting Y. then i try doing CTRL-D, does nothing. this happened yesterday morning after i shut it down for about an hour. i've had 9.10 for months and this is the first time it's happened. can anyone help me out?

---

### Post by freesitebuilder on 2010-07-15
Upgrading to 10.04 (I did a clean install) has cured it for me.

---

### Post by deadramonesxx on 2010-07-15
but how do i upgrade if i can't get out of this menu? i really don't know what to do and there's a lot of files i haven't saved on my external. i'm worried and i don't want to buy a new one.

---

### Post by freesitebuilder on 2010-07-16
Have you got a LiveCD? You could boot from that and copy your files off before reinstalling. :(

---

