---
title: "Terminal prompt reset to default"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by thomas37 on 2010-10-29
Guys, a friend worked on my Ubuntu system (I am a newbie) and now my terminal prompt behaves strange and looks weird. If I use the up and down arrow keys to scroll through last typed commands, I get gibberish on screen that does not work, and the prompt output is now "[\u@\H \W \@]$
"

How do I reset the terminal to it's default settings and behaviour? My friend did something with VI, not sure if this affects my prompt or not.

---

### Post by darkhelmetchris on 2010-10-29
Your friend has probably messed up your ~/.bashrc file.  If you create a new user, log in as that one, it will create a new .bashrc in that user's home folder.  You can copy that back to your user profile, chown it to you, log out and log in.

For example:

(back up first, in your normal user profile)
```
cp ~/.bashrc ~/.bashrc-backup
```(in the new user, copy the .bashrc file to somewhere like /home)
```
sudo cp ~/.bashrc /home
```(log out and in to your regular user, copy the file back to your profile)
```
sudo cp /home/.bashrc ~
sudo chown yourusername:yourusername .bashrc
```(log out and log back in)

That should restore a default .bashrc file

If that all works nicely, remove the /home/.bashrc file, as it is a left over.  You might also remove the ~/.bashrc-backup file, when you're sure you're happy again.

---

### Post by thomas37 on 2010-11-01
Fantastic, let me try that :-)

---

### Post by thomas37 on 2010-11-01
Ok, not having much luck getting this done. While the logical flow makes sense to me, I suspect several detailed little steps are missing, as the new used did not have "sudoers" access etc. I cannot seem to get the .bashrc file copied from the new user to my default user. Any ideas?

---

### Post by gmargo on 2010-11-01
The default .bashrc file is in **/etc/skel/.bashrc**.  Copy that one.

```

$ cd $HOME
$ mv .bashrc .bashrc.old
$ cp -p /etc/skel/.bashrc .

```

---

### Post by darkhelmetchris on 2010-11-01
> **gmargo said:**
> The default .bashrc file is in **/etc/skel/.bashrc**.  Copy that one.

Nice, gmargo, I didn't know that's where the default one was.  That's probably a better solution.

thomas37, all your new user needed was to be a member of the "admin" group.  But, I like gmargo's solution.

---

### Post by thomas37 on 2010-11-03
Thanks guys, Gmargo's solution helped, this is now solved :-)

---

### Post by Quackers on 2010-11-03
Sorry wrong thread!

---

