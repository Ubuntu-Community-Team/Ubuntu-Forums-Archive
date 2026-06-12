---
title: "How to uninstall Songbird?  Installed via .deb"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Timzor on 2009-02-07
Hello, I am sure that this is a simple question, but I am very inexperienced.

I'd like to uninstall songbird, an ipod manager I downloaded, but I'm not sure how to do it because rather than using synaptic or add/remove programs, I installed it using a .deb file.  The only way I know to uninstall programs is via synaptic or add/remove, but it doesn't show up in their lists.

Can you help?

---

### Post by abn91c on 2009-02-07
in a terminal try sudo apt-get remove songbird

---

### Post by Crafty Kisses on 2009-02-07
If you want to remove Songbird and all the configuration files run the following:
```
sudo apt-get remove --purge songbird
```

---

### Post by Timzor on 2009-02-07
@abn91c:  Thanks so much, that worked perfectly!

I feel like I should know this sort of thing already.  Where can I read up on basic things like this?

@Codename:  Oh, I already tried it the other way.  Does that mean there are still songbird files on my computer?

---

### Post by Crafty Kisses on 2009-02-07
Here are a couple good links my friend: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal). Then there is PsychoCats, great tutorials there: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php).

---

### Post by Timzor on 2009-02-07
Thank you for the study material.  I'll do my best to become more self-sufficient.

---

### Post by kostkon on 2009-02-07
> **Timzor said:**
> Hello, I am sure that this is a simple question, but I am very inexperienced.

I'd like to uninstall songbird, an ipod manager I downloaded, but I'm not sure how to do it because rather than using synaptic or add/remove programs, I installed it using a .deb file.  The only way I know to uninstall programs is via synaptic or add/remove, but it doesn't show up in their lists.

Can you help?
Strange, because every .deb file that you install should appear in *Synaptic* (not in *Add/Remove* though).

Are you sure that you used the *search* facility in Synaptic and not the *quick search* one (assuming that you have 8.10)?

---

### Post by Timzor on 2009-02-07
I suppose I used the quick search.  Thanks for the tip; I'll be sure and use the full search next time.

---

### Post by fleasbaby on 2009-06-23
Hi all,

I installed Songbird by placing the .tar file in my home folder and double-clicking the executable. Now I can't seem to uninstall it using synaptic or add/remove...I tried the command lines above, but all I get is "couldn't find package songbird"...

Any advice?

---

### Post by Celauran on 2009-06-23
It doesn't actually install anything. You untar to a directory and it's ready to go. That said, just remove the directory to uninstall it. It also creates ~/.songbird2 which you may want to remove.

---

### Post by fleasbaby on 2009-06-23
Thanks Celauran. So, just to be sure I have this right, I go to the "Home" folder and just delete the Songbird folder?

How do I find and delete "~/.songbird2"?

(Sorry, I am a complete newbie and am still taking baby-steps)

---

### Post by treesurf on 2009-06-23
Directories that have a "." in front of them are hidden.  To find the /.songbird2 folder you will need to type ctrl+h in your file browser to view hidden files.  Then you will find that folder in your home directory and can simply toss it in the trash.  Type ctrl+h again and all those hidden files will dissapear from view again.

---

### Post by fleasbaby on 2009-06-24
NICE! Thanks Treesurf!

---

