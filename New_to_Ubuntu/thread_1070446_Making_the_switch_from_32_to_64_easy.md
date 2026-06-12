---
title: "Making the switch from 32 to 64 easy"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by jou770d on 2009-02-15
I know there's an awful lot of threads asking about switching from 32bit to 64bit. However, all of those ask about whether the switch is a good idea or not.
What I want to ask is how to keep this switch as automated as possible.

1) I already have /home/ on a partition of it's own, should I keep it as it is? Will programs be able to use their settings from the old installation or will this cause problems?

2) Would something like [this]("http://ubuntuforums.org/showpost.php?p=1521615&postcount=1") help me get back whatever packages I already had (or at least most of it)? or is the difference between 32 and 64 to big to rely on such simple methods? (I realise I wouldn't get exact the same packages but their 64 equivalents).

3) Will copying the significant folders from /usr/share work in order to keep my themes, fonts, icons and cursors?

4) Just to make sure. Beside giving /home/ it's own partition I also gave one to /boot/ (that was recommended in a couple of guides I started learning from). Nothing there is worth keeping, right? 

I'm guessing the performance gain won't be that great as I only have 4GB of rams but I want to give this a shot (unless someone can give me a solid reason why not to do it). Plus I could only hope that this will solve my only issue with Ubuntu ([http://ubuntuforums.org/showthread.php?t=1067898](http://ubuntuforums.org/showthread.php?t=1067898)).

At any rate I'm gonna start by using remastersys to backup in case anything goes wrong...

---

### Post by shifty_powers on 2009-02-15
1) They should do, yeas.

2). It can work, yes, but it's not perfect. Certainly worth a go, especially if you are going to be using exactly the same distor and version, just 64-bit.

3). Don't know.

4). Nope, it is just the boot files, nothing essential, they'll get replaced by the new install.

---

### Post by jou770d on 2009-02-15
Thanks for the quick answer!
I'll give it a shot and report back for future reference.
By the way, loved the VG Cats avatar :)

---

### Post by 3rdalbum on 2009-02-15
For #3, you can copy your icons, themes and cursors over and they will work on 64-bit. If you have any themes that require a custom theme engine, they of course won't work unless you install the 64-bit version of the theme engine.

---

### Post by Paqman on 2009-02-15
> **Amarus said:**
> 
1) I already have /home/ on a partition of it's own, should I keep it as it is? Will programs be able to use their settings from the old installation or will this cause problems?


Yes, that will work fine. The settings stored in your /home are just text files.

> 
2) Would something like [this]("http://ubuntuforums.org/showpost.php?p=1521615&postcount=1") help me get back whatever packages I already had (or at least most of it)? or is the difference between 32 and 64 to big to rely on such simple methods? (I realise I wouldn't get exact the same packages but their 64 equivalents).


Yes, apt will pick that up fine. Again, all your feeding it is a text file with the package names. It'll download the 64-bit versions.

> 
3) Will copying the significant folders from /usr/share work in order to keep my themes, fonts, icons and cursors?


Yep, stuff like that is all the same on 64-bit. It's really only apps that are different.

> 
4) Just to make sure. Beside giving /home/ it's own partition I also gave one to /boot/ (that was recommended in a couple of guides I started learning from). Nothing there is worth keeping, right? 


No, you can choose to use a /boot partition on your 64-bit install if you want. Just follow the same procedure you used when you set it up on 32-bit.

> 
Plus I could only hope that this will solve my only issue with Ubuntu ([http://ubuntuforums.org/showthread.php?t=1067898](http://ubuntuforums.org/showthread.php?t=1067898)).


I wouldn't hold out too much hope, really. Looks like a hardware compatibility issue. You never know though.

---

### Post by jou770d on 2009-02-18
Thanks for the support! Made the switch and everything went smoothly.

> **Paqman said:**
> 
I wouldn't hold out too much hope, really. Looks like a hardware compatibility issue. You never know though.
Somehow this seems to have fixed my issue!
However it might not be because of the 64 version, it might be cause this time I made grub the default bootloader instead of keeping Vista's and adding Ubuntu there.

Edit: yep, just as I thought. Using GRUB fixed it. If I restarted from windows the issue is back if I started ubuntu from a shutdown (or a restart from ubuntu) I don't have the problem with my cdrom.

---

