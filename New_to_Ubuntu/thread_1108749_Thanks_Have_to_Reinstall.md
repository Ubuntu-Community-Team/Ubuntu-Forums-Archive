---
title: "Thanks Have to Reinstall"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by chris reid on 2009-03-28
As many new users are trying to figure stuff out I ran into a huge problem. I know half of it is stupidity, but the wording on this link still gives hope when you have searched the entire internet for how to uninstall python.

[http://ubuntuforums.org/showthread.php?t=404591](http://ubuntuforums.org/showthread.php?t=404591)

since I am a new user I cannot post on the thread. I ran the command and now have to reinstall ubuntu. Yes I thought he was warning at first, but it is still a bit vague with his explanation on "this is how to uninstall python". I don't know what all the things are in the remove section he posted. If someone would have posted below his post that this will really mess up your system... I would never have clicked it. 

Anyways, just as a concerned idiot hoping to save another idiot from clicking on this. Thanks whomever does the deed.

---

### Post by asmoore82 on 2009-03-28
You never really **have** to re-install; but sometimes a re-install is just quicker and easier...

You should be able to get your system back to the minimum requirements for a working desktop with a
```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---

### Post by lovinglinux on 2009-03-28
The question in that thread was "How do I uninstall older python versions", which means the user already had another version installed, thus removing python does not damage the system.

I had python 2.4 automatically removed other day when I removed apache, mysql and php, because the package wasn't needed anymore. But the package manager automatically configured other programs that use python 2.5 version. No harm done.

What I think is odd is the *autoremove*, which is used to clean up packages not required by other applications. I'm not an expert, but I thought *autoremove* was supposed to be used alone, without the program option. I guess this could be your problem. Since you didn't have another python version installed and used the *autoremove* option, it remove not only python, but other important stuff.

Would be nice if someone could confirm this.

---

### Post by Elfy on 2009-03-28
> Anyways, just as a concerned idiot hoping to save another idiot from clicking on this. Thanks whomever does the deed.

@chris reid - You can't post in there because it is in the Archive - neither can I. If you feel that there should be something written in the thread to warn others then report it - in the left panel of the usder information - at the bottom are 2 icons - one with notepad with a body on it is the report post button.

Personally I wouldn't have relied on a thread with 2 posts by the same person unless it was in the Tutorial Forum as they get checked.

I also am a bit confused by the use of apt-get autoremove.

---

### Post by 3rdalbum on 2009-03-28
When you try to remove Python by using that command, it gives you a warning message that it also has to remove 100 packages or something like that. Whenever I see a large number of packages that are going to be removed by any operation, I check myself and make sure that what I'm doing is correct.

Reinstalling is not necessary after removing Python, anyway. You can just tell Synaptic to install the "ubuntu-desktop" package and any Python-dependent programs that you manually installed earlier, and that will bring things back to normal.

---

### Post by t0p on 2009-03-28
That post you decided to follow up on is clearly a warning.  It starts with the words **This is a warning to all that want to uninstall python** and goes on to list a hundred-odd packages that will be removed if you run that command.  I think it's clear that post is not advising you to remove python that way.

---

### Post by lovinglinux on 2009-03-28
> **t0p said:**
> That post you decided to follow up on is clearly a warning.  It starts with the words **This is a warning to all that want to uninstall python** and goes on to list a hundred-odd packages that will be removed if you run that command.  I think it's clear that post is not advising you to remove python that way.

I don't think is clear enough. I think the OP found that command somewhere and messed up with his installation, so he decided to post a warning. But the way it is posted, it looks like the correct solution to the previous post. It should have something like "DON'T RUN THIS COMMAND" in the text. The word "warning" in that context, conveys the idea of the correct solution, not a stop sign. Additionally, when he says "now I got to uninstall the ****" I guess he did a mistake and replaced *install* with *uninstall*. Otherwise i doesn't make any sense.

IMO, that thread should be deleted.

---

### Post by hyper_ch on 2009-03-28
> **asmoore82 said:**
> You never really **have** to re-install; but sometimes a re-install is just quicker and easier...

well, I'd disagree here... if your system was compromised then you can't trust it any longer. Reinstallation is the only way. Except for that I agree that a reinstall is not necessary (just quicker sometimes)

---

### Post by ugm6hr on 2009-03-28
> **chris reid said:**
> ...when you have searched the entire internet for how to uninstall python...

Why would you be removing python?

If you are a new user, there is no reason why you would want to remove it.

PS: You do not have to reinstall at all.

---

### Post by bapoumba on 2009-03-28
I have moved the thread from OP to jail where it will not be indexed by search engines.

---

