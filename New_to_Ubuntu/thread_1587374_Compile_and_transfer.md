---
title: "Compile and transfer"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by masque7 on 2010-10-03
I've got a laptop and a netbook with Ubuntu 10.04 and the Netbook Edition installed with i686 versions respectively. If I compile software on one box, how do I copy it to the other? The netbook doesn't have the build/dev tools installed, so I don't want to compile twice -- or on an Atom CPU.

Is the easiest way to make a .deb, or is there a better way to transfer a successful build onto the netbook? Thanks

---

### Post by Darkness Des on 2010-10-03
When you do *sudo make install* in the compiling process, change that to *sudo make checkinstall* and it will build a .deb

---

### Post by andrewthomas on 2010-10-03
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by masque7 on 2010-10-03
Thanks. It's just *sudo checkinstall* to make a deb

---

### Post by Darkness Des on 2010-10-03
That would explain quite a bit... Please mark your thread as Solved, using the thread tools button at the top.

---

### Post by masque7 on 2010-10-04
Have done. Where's the place to go to upload successful deb builds? If anyone is curious it's Handbrake 0.9.4 for x86/i686

---

### Post by Darkness Des on 2010-10-04
To remix a bad commercial, "There's a repo for that". Literally. I get daily updates. But are you asking where to store files on the internet? Sendspace works good, Megaupload, Flash Drives, anything.

---

### Post by masque7 on 2010-10-05
If you mean Handbrake, this is from the [website]("http://handbrake.fr/downloads.php") 
> 0.9.4 is no longer available due to compatibility issues with the newer version of gnome.And then there are unstable pre-release builds, so I figured compiling 0.9.4 was the best option.

---

### Post by JohnAStebbins on 2010-10-05
> **masque7 said:**
> If you mean Handbrake, this is from the [website]("http://handbrake.fr/downloads.php") 
And then there are unstable pre-release builds, so I figured compiling 0.9.4 was the best option.

Um, those 'unstable' pre-release builds are almost always better than 0.9.4.  0.9.4 is stable in the sense that it is not changing.  Not in the sense that it is free of bugs.  The nightly builds have far fewer bugs than 0.9.4, but since they change nightly, you never know when a show stopper bug might arise.  But such show stoppers are fixed before the next nightly if not within minutes of being discovered.

---

