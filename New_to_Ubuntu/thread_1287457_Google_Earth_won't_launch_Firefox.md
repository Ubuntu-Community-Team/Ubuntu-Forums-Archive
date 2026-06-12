---
title: "Google Earth won't launch Firefox"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by RobHK on 2009-10-10
Google Earth is giving me this error message:

> Could not launch any web browser. Please make sure you have set the $BROWSER environment variable to the filename of the web browser we should launch.

I found this:[http://ubuntuforums.org/showthread.php?t=907185](http://ubuntuforums.org/showthread.php?t=907185)

but I don't understand the advice given. Can someone explain what I actually can do, please?

---

### Post by kiridude on 2009-10-10
Ok, type

```
gksudo nautilus
```

then hit ctrl h

then click on "filesystem"

then double click "home" then "username" then scroll down to .bashrc

double click .bashrc and then copy past 

```
export BROWSER=/usr/bin/firefox
```

on a new line at the end of the text.

Close the page and click "save."

That should do it.

---

### Post by howefield on 2009-10-10
That thread is telling you to open the bashrc file by typing the following into a terminal.

```
gksu gedit /etc/bash.bashrc
```

type in your password and append the following text to the end of it and save.
```

export BROWSER=/usr/bin/firefox
```

---

### Post by kiridude on 2009-10-10
Yes, that would be the simplest way to do it, but I laid out the graphic way because the OP was confused and I thought he would better understand what he was doing like that.

---

### Post by RobHK on 2009-10-11
> **kiridude said:**
> Yes, that would be the simplest way to do it, but I laid out the graphic way because the OP was confused and I thought he would better understand what he was doing like that.Thanks, guys. I had a bash.bashrc in /etc but not in /home/username.

Can you help with another Google Earth issue? When I look at a photo I see it OK and if I click it, it opens in Firefox, but if I try to save it, FF crashes. It doesn't happen when using FF in other contexts. neither does it happen in my Windows XP installation.

---

