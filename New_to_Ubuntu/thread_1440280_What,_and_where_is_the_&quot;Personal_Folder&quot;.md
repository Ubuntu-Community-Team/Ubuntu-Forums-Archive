---
title: "What, and where is the &quot;Personal Folder&quot;?"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by Sentoguy on 2010-03-27
Hello,

First let me say thank you for this very helpful forum.

Was wondering if anyone could tell me exactly what the "personal folder" is, where I can find it, and how I can download things through it?

I'm currently trying to upgrade my sound drivers (Alsa 1.0.20 to Alsa 1.0.22.1) and am following this tutorial guide:
[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

I've already installed the necessary tools to compile along with the kernel headers, but then it says "Then, we go in our personal folder and download alsa-driver, alsa-lib and alsa-utils"

I've done several searches for the term "personal folder", but have come up with nothing actually telling me what, or where I can find this personal folder or how I can download those files through it.

Is the tutorial maker using terminology not commonly used? Is there another name for this "personal folder"? Is there a glossary of terms thread which explains what different technical terms mean and/or where to find specific folders?

Thanks in advance for any help anyone can offer.

---

### Post by nothingspecial on 2010-03-27
It means home folder

```
cd ~
```

~ is linux shorthand for home.

You don`t even need the ~ a plain old

```
cd
```

Will take you there

---

### Post by Chronon on 2010-03-27
The term you want is "home folder".  

Your home folder is located at the path: /home/*username*/

If you open the file manager (Nautilus by default) you should be able to easily navigate to this directory.

---

### Post by r-senior on 2010-03-27
It just means your home directory:

Note the first line of their directions:

```
cd ~
```

The tilde "~" is shorthand for home directory, these are all equivalent for user "sentoguy":

```
$ cd ~
$ cd $HOME
$ cd /home/sentoguy

```

---

### Post by Sentoguy on 2010-03-27
Thanks everyone.

Ok, so now I know what and where the file is, but I'm still confused as to how I download through that file.

The code provided in the tutorial looks like something that I'd enter in the terminal/shell, but it sounds like I should be entering it in my home folder?

Or, am I supposed to enter the code"
cd~

in the terminal, and that will somehow bring me to my home folder?

Thanks again, and sorry, I'm pretty new at this stuff.

---

### Post by nothingspecial on 2010-03-27
Just copy and paste the code in the tutorial. I`ve looked through it and it is fine.

The reason I say copy and paste is that a missplaced space in a few of those commands could end up devastating.

On the other hand I`ve no idea if manually compiling alsa is going to solve whatever difficulties you are having.

---

### Post by Sentoguy on 2010-03-27
> **nothingspecial said:**
> Just copy and paste the code in the tutorial. I`ve looked through it and it is fine.

The reason I say copy and paste is that a missplaced space in a few of those commands could end up devastating.

On the other hand I`ve no idea if manually compiling alsa is going to solve whatever difficulties you are having.

Thanks.

Ok, so I followed your advice and finished the tutorial. I'm now upgraded to the ".22.1" version of alsa. But, I've still got no sound (the original reason for upgrading the drivers in the first place). 

I know that the speakers work, since they work with the Windows 7 that came with the computer, but for whatever reason Ubuntu is not responding to them.

Just for reference (in case it helps any of you with advising me) I'm using a new Dell Inspiron Zino and the sound cards found by the "sudo alsaconf" command are:
hda-intel ATI Technologies Inc sBx00 Azalia (Intel HDA)
hda-intel ATI Technologies Inc RS780 Azalia controller
legacy   Probe legacy ISA (non-PnP) chips 

Thanks again for the help and any help you can give me on the above question/problem.

---

### Post by nothingspecial on 2010-03-27
I`ve not got a lot of time to look into this tonight, although I will if I can.

My advice would be to mark this thread solved (through the thread tools button) and start a new thread about your sound card.

Someone who knows exactly what to do may be browsing the forum right now but might skip a thread entitled "Where is the personal folder" if you see what I mean.

---

### Post by nothingspecial on 2010-03-27
You could try [[COLOR="Magenta"]this[/COLOR]]("http://swiss.ubuntuforums.org/showpost.php?p=8753917&postcount=1")

Looks like overkill to me but it shouldn`t do any harm.

---

### Post by Sentoguy on 2010-03-27
> **nothingspecial said:**
> I`ve not got a lot of time to look into this tonight, although I will if I can.

My advice would be to mark this thread solved (through the thread tools button) and start a new thread about your sound card.

Someone who knows exactly what to do may be browsing the forum right now but might skip a thread entitled "Where is the personal folder" if you see what I mean.

Yes, I see what you mean. Thanks again for the help.

---

### Post by Sentoguy on 2010-03-27
Sorry, can't figure out how to mark this thread "solved". Maybe one of the mods can do so for me, or someone can tell me how to do it.

---

### Post by lswartz on 2010-03-27
I got it for you, it is edit tags (near the lower right hand corner) for the next time you need it.

---

### Post by Sentoguy on 2010-03-27
Thanks.:D

---

### Post by Chronon on 2010-03-27
That just adds a tag.  I believe you can mark it solved by going to "Thread Tools".

---

