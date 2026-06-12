---
title: "Changed Home Directory"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-01-19
Hi, I installed ibex on my desktop last week. I tried to change my username, but ended up only changing the home directory so when I try and log in, I get an error saying that my home directory doesn't exist. So it makes me log in with the root directory. After that it says "User's $Home/.dmrc file is being ignored." When I finally log in, I get another error saying "could not update ICEauthority file /.ICEauthority" 

"there is a problem with the configuration server. (/user/lib/libgconf2-4/gconf-sanity-check-2 excited status 256)"

"there was an error starting up the screensaver:

Failed to change directory '/home/directory name' (NO such file or directory)

Screensaver functionality will not work in this session."

"Cannot create the directory "/home/directory name/.gnome2/share/fonts".
This is needed to allow changing the mouse pointer theme"

I click ok and close for everything and then I'm left with just the wallpaper and none of the toolbars.

---

### Post by emarkd on 2009-01-19
The path to your home directory is stored in the /etc/passwd file.  You can edit that file using:

```
gksu gedit /etc/passwd
```

You can run that from the <ALT>F2 dialog.  Be very careful, though.  Saving a backup is a good idea in case you make a mistake and make things worse.

---

### Post by Sup3r3g0 on 2009-01-19
When do I press alt f2? Also when I do, will that open up the terminal? Do I fill in etc with the name of my home directory and passwd with my root password? Sorry for all the questions.

---

### Post by Sup3r3g0 on 2009-01-19
bump

---

### Post by lovelyvik293 on 2009-01-19
No the Alt f2 does not open the terminal.but you can run the commands here.
This line in /etc/passwd you have to change
```


vikas:x:1000:1000:vikas,,,:/home/vikas:/bin/bash


```

---

### Post by yeats on 2009-01-19
If your GUI isn't loading, you can drop to a regular login shell by typing

```
Crtl-Alt-F1
```

then try logging in from there to try the command suggested, though you would want do to:

```

cd /etc
sudo cp passwd passwd.copy [*to create a backup copy*]
sudo pico /etc/passwd      [*pico is a simple text editor*]

```

That way if you make things worse you can do this:

```

cd /etc
mv passwd.copy passwd

```

and you'll be back to square one.

You can return to your X screen by typing "Alt-F7"

---

### Post by Sup3r3g0 on 2009-01-19
Okay so I can use alt f2 when it's booting up or ctl alt f1 after I'm forced to login to root so I can start using commands?

Thanks everyone for helping.

---

### Post by yeats on 2009-01-19
If your graphical interface isn't loading, you can skip the Alt-F2 suggestion altogether.  Just do Ctrl-Alt-F1 once you're booted up.  You can actually do that at any time when you're running - no specific timing involved.

---

### Post by yeats on 2009-01-19
I'll also mention this.  The reason your GUI isn't loading is that it uses some of the hidden files in your home directory (.gnome, etc.) to configure itself.  Since you changed the name, the computer no longer knows where to look.  My advice would be to attempt to UN-do what you've done and live with your original user name until you've done more research about it. :-)

---

### Post by Sup3r3g0 on 2009-01-19
Thanks I'll try it out

---

### Post by doooley on 2009-02-08
ive had the same problem, i tried making user accounts and ended up switching around home directories in the process. sorry for bringing the whole thing up again but theres something im missing.  i went into ctrl alt f1....i can log into one user account there out of the 3 user accounts i made. where do i go from there? again sorry for brining it up but im totally confused.

---

### Post by Sup3r3g0 on 2009-02-08
I just reinstalled it. I didn't have much on there

---

### Post by doooley on 2009-02-11
i managd to fix it pretty handily actually by just using

sudo usermod -d /home/username username

that fixed the original mistake of changing the home directory. im back on track now.

thanks anyway.

---

