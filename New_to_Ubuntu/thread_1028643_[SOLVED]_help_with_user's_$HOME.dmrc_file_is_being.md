---
title: "[SOLVED] help with: user's $HOME/.dmrc file is being ignored..."
date: 2009-01-02
forum: New to Ubuntu
---

### Post by egalvan on 2009-01-02
I just started receiving this message when I get to the log-on screen...

```
user's $HOME/.dmrc file is being ignored.
This prevents the default session and language from being saved.

File should be owned by user and have 644 permissions.

User's $HOME directory must be owned by user and not writable by others.

```

This machine has run fine for more than six months.


I've attached screen-shots that may be helpful.

edited to add code to correct this problem,
'sudo' may or may not be needed...

```
sudo chmod 644 ~/.dmrc
sudo chmod 755 ~
```

---

### Post by bump_ on 2009-01-02
The permissions are not right on the file. They should be rw-r--r-- to be 644. To change it, type the following into a terminal

```
chmod 644 ~/.dmrc
```

and that should fix the permissions.

---

### Post by dwasifar on 2009-01-02
> **bump_ said:**
> The permissions are not right on the file. They should be rw-r--r-- to be 644. To change it, type the following into a terminal

```
chmod 644 ~/.dmrc
```

and that should fix the permissions.

That's half of it.  The other half is this:

```
sudo chown ernest:ernest ~/.dmrc
```

...to set the ownership correctly.  (Note that ernest is the OP's username.  If you're not him and your username is not ernest, use your own username instead.)

He might have to sudo your chmod statement as well, now that I think of it.

---

### Post by bump_ on 2009-01-02
I believe that the owner is already correct judging from the screenshots. And if he is indeed the owner, then sudo isn't neccessary.

I may be wrong though

---

### Post by dwasifar on 2009-01-02
> **bump_ said:**
> I believe that the owner is already correct judging from the screenshots. And if he is indeed the owner, then sudo isn't neccessary.

I may be wrong though

No, you're absolutely right.  I didn't notice that in the first screenshot and I stand corrected.  :)

However, the chown may still be useful to others reading this thread.  I had the same issue crop up with no warning on my system a few months ago, and both the permissions and the ownership needed to be reset.

---

### Post by egalvan on 2009-01-02
> **bump_ said:**
> The permissions are not right on the file. They should be rw-r--r-- to be 644. To change it, type the following into a terminal

```
chmod 644 ~/.dmrc
```

and that should fix the permissions.

Sorry for the delay,

OK, i ran that command, and here is a new screenshot...

does it look better?

---

### Post by egalvan on 2009-01-02
> **dwasifar said:**
> That's half of it.  The other half is this:

```
sudo chown ernest:ernest ~/.dmrc
```

...to set the ownership correctly.  (Note that ernest is the OP's username.  If you're not him and your username is not ernest, use your own username instead.)

He might have to sudo your chmod statement as well, now that I think of it.

Yes, I can earnestly say that it is very important to be Ernest.

I am ernest, the only user on this machine....

All files are either owned by ernest, or by root.
this seems (to my limited knowledge) to be the correct situation.
Right?

ErnestG

---

### Post by bump_ on 2009-01-02
Yes the permissions look fine now

As for owners, a file can be owned by any user on the machine. So if the only users on your machine are root and ernest, then those will the only owners.

---

### Post by egalvan on 2009-01-02
Now what about the second part...

**User's $HOME directory must be owned by user and not writable by others.**

here is the screenshot again...

---

### Post by bump_ on 2009-01-02
Sorry i already edited my previous post. I missed the second part the first time around and only saw it right after I posted

---

### Post by egalvan on 2009-01-02
> **bump_ said:**
> Yes the permissions look fine now

As for owners, a file can be owned by any user on the machine. So if the only users on your machine are root and ernest, then those will the only owners.

OK, re-booted and same error message popped up.

the permissions for .dmrc stayed the same

-rw-r--r--

I'm now lost.


EDIT: gotta go eat dinner. back in two hours...
ernestG

---

### Post by bump_ on 2009-01-02
Ahh I made a mistake. I read the error message you orignially posted too fast. It clearly states you should be the only one able to write to your home directory.

```
chmod 755 ~
```

should do the trick

---

### Post by egalvan on 2009-01-03
> **bump_ said:**
> It clearly states you should be the only one able to write to your home directory.

```
chmod 755 ~
```

should do the trick

And it surely did. Everything is back to "normal" on my boxen.

Many thanks!

:KS:KS

---

### Post by dondad on 2009-01-03
> **dwasifar said:**
> No, you're absolutely right.  I didn't notice that in the first screenshot and I stand corrected.  :)

However, the chown may still be useful to others reading this thread.  I had the same issue crop up with no warning on my system a few months ago, and both the permissions and the ownership needed to be reset.

Sometimes this can be caused by using sudo rather than gksudo on a graphical program such as gedit. Sometimes it will change ownership of the entire/home directory and you also have to fix that.

---

### Post by dwasifar on 2009-01-03
> **bump_ said:**
> Yes the permissions look fine now

As for owners, a file can be owned by any user on the machine. So if the only users on your machine are root and ernest, then those will the only owners.
I have had files appear with owner of "1000".  Seems like that happens when the ownership is not properly specified.

---

### Post by Francewhoa on 2009-10-08
Tutorial to fix this can be found at [http://swiss.ubuntuforums.org/showthread.php?t=976610](http://swiss.ubuntuforums.org/showthread.php?t=976610)

---

