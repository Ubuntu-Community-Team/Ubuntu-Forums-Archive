---
title: "Changing File Permissions"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by JonathanDS on 2010-08-13
I recently reinstalled Lucid. Before the reinstall, I stored all of my data on a separate, encrypted partition. I have moved all of my media back to my home directory, though I had to use a root nautilus, running on Live CD, to access the encrypted partition. This was all done without issue, but now all of my media is unaccessible. My question is: What terminal command can give me access to all files within my home directory. I've tried chmod and chown, but I think I'm misusing them.

Thanks,
Jon

---

### Post by hishamnajam on 2010-08-13
try using chmod with the -R switch 

> sudo chmod 666 -R <home-directory>

---

### Post by mapes12 on 2010-08-13
Use the ```
gksudo nautilus
```as before.

Now, navigate to the stuff that you want to change permissions and right click: Properties>Permissions and then set the permissions in the GUI.

---

### Post by JonathanDS on 2010-08-13
> **hishamnajam said:**
> try using chmod with the -R switch
Terminal returned the following error:

chmod: cannot access `/home/jonathan/.gvfs': Permission denied

---

### Post by Calcipher on 2010-08-13
First, let me say be careful doing this, blindly changing file permissions is not a good idea.  That being said there are generally two things you need to do using the tools chmod (to change the access permissions) and chown (to change the owner of the files).  Let's assume that you are in your media folder in the command line, the first thing you'll want to do is this:
```

ls -al

```
You might also want to throw a -R to make sure that you are only messing with files you care about.  Now, the first thing you'll want to do is change the access list to these files.  For media files, permissions of 755 are usually appropriate (this give the owner full access and everyone else read and execute).  Do this as follows:
```

sudo chmod -R 755 *

```
Next, you'll want to set yourself as the owner.  You should know your user name, but if not run:
```

whoami

```
Assuming you didn't set anything up in a weird way, your username is likely also your group name.  With this information in had run the following:
```

sudo chown -R username.groupname *

```
WARNING: Make absolutely sure you are not changing the permissions on system files (i.e. make sure there are no system files inside the folder (or sub folders) that you are changing permissions in).

---

### Post by Calcipher on 2010-08-13
> **JonathanDS said:**
> Terminal returned the following error:

chmod: cannot access `/home/jonathan/.gvfs': Permission denied
Don't worry about the .gvfs file, it is a fake filesystem that always has permission issues.
Edit: I'd also not suggest doing your entire home directory at once as some files need different permissions.  If, however, you are in your home directory most this should probably be owned by you and your group (jonathan.jonathan).

---

### Post by JonathanDS on 2010-08-13
OK, now I cannot access anything... and I cannot find my home directory... and I can no longer open nautilus...

---

### Post by JonathanDS on 2010-08-13
Scrap that, it's all still there, but I have no access what so ever to my home directory, outside of root nautilus.

---

### Post by uRock on 2010-08-13
> **JonathanDS said:**
> OK, now I cannot access anything... and I cannot find my home directory... and I can no longer open nautilus...
Are you still using the LiveCD or are you using the install? My luck has been better when changing permissions within the installed system.

Also, changing file permission within sudo changes them for root, not the user. Use the sudo chown command listed above for this.

---

### Post by Calcipher on 2010-08-13
Your home directory is going to be at /home/jonathan.  Do you think you could open a terminal and do the following:
```

cd /home
ls -al

```
Paste the output in the code tags so I can see what is going on.

---

### Post by JonathanDS on 2010-08-13
Alright, everything is fine, and permissions have been satisfactorily edited. Sorry for the melodrama, it was my mistake, and has been solved. Thanks for all the help.

---

### Post by uRock on 2010-08-13
> **JonathanDS said:**
> Alright, everything is fine, and permissions have been satisfactorily edited. Sorry for the melodrama, it was my mistake, and has been solved. Thanks for all the help.
Could you post which command did it for you for future references? 

Please don't forget to mark thread as solved.

Thanks,
uRock

---

### Post by Calcipher on 2010-08-13
> **JonathanDS said:**
> Alright, everything is fine, and permissions have been satisfactorily edited. Sorry for the melodrama, it was my mistake, and has been solved. Thanks for all the help.
Glad to hear it.  Cheers!
Edit: You might consider changing this thread to SOLVED.

---

### Post by JonathanDS on 2010-08-13
> **uRock said:**
> Could you post which command did it for you for future references? 

Please don't forget to mark thread as solved.

Thanks,
uRock

It was actually root nautilus. I used the UI Permissions editor, under "Properties".

---

### Post by uRock on 2010-08-13
> **JonathanDS said:**
> It was actually root nautilus. I used the UI Permissions editor, under "Properties".
Awesome, glad it worked.

---

### Post by mapes12 on 2010-08-13
> It was actually root nautilus. I used the UI Permissions editor, under "Properties".and that's where the Gnome desktop project helps the world use Linux without having to remember command lines.

Brilliant!

---

