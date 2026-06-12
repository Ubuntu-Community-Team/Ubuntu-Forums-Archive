---
title: "Cannot set CVS directory"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by ssubluesman on 2009-07-18
I have tried setting the CVS directory many times and many ways, yet I can't seem to get it to work. I searched here and based off this topic ([http://ubuntuforums.org/showthread.php?t=1106099&highlight=cvs](http://ubuntuforums.org/showthread.php?t=1106099&highlight=cvs)) tried different commands (I obviously changed directory locations) but nothing worked. I tried this tutorial ([http://www.gentoo.org/doc/en/cvs-tutorial.xml](http://www.gentoo.org/doc/en/cvs-tutorial.xml)) and I still can't get it to work. After each attempt I try 'cvs init' and end up with:

> cvs init: No CVSROOT specified!  Please use the `-d' option
cvs [init aborted]: or set the CVSROOT environment variable.

I have no doubt it's something simple, but I'm fairly new to Ubuntu and even newer to CVS (I've played around with it a bit in Netbeans). Please help.

---

### Post by ssubluesman on 2009-07-19
anyone?

---

### Post by unutbu on 2009-07-19
Are you planning on using CVS on your local machine and just trying to set it up, or are you trying to download source code from the internet?

---

### Post by ssubluesman on 2009-07-19
I would like to be able to do both.

---

### Post by unutbu on 2009-07-19
ssubluesman, I am more familiar with bazaar (bzr) than cvs, so be aware I'm not speaking from experience. I'm drawing my info from here:

[http://www.cs.brandeis.edu/~guru/cvs.html](http://www.cs.brandeis.edu/~guru/cvs.html)

Since Ubuntu users (by default) use bash, not csh for the user's shell,
instead of editing .cshrc as suggested in the link above, you should edit ~/.bashrc.
```

gedit ~/.bashrc

```
Add this to the end of your .bashrc:
```

export CVSROOT=$HOME/.cvsroot

```
Save and exit the text editor, gedit. Close your terminal and open a new terminal window. Each time you open a terminal window, ~/.bashrc is read. Thus your change to ~/.bashrc should become effective. You can check that it worked by typing

```
echo $CVSROOT
```

in the terminal. You should see something like
```

/home/user/.cvsroot
``` in response. If the echo command returns nothing, then something went wrong.

Make the .cvsroot and .cvsroot/CVSROOT directories:
```

mkdir -p ~/.cvsroot/CVSROOT

```
Now try
```

cvs init
```

---

### Post by ssubluesman on 2009-07-19
It won't work. At the top of my command shell I get:

> bash: export: `/home/derek/.cvsroot': not a valid identifier


I've tried playing around with a bunch of different possible locations (although that is a valid location, I checked it in the shell). I tried going through the rest of the steps anyways and end up with the "NO CVSROOT specified..." bit that I posted earlier.

---

### Post by unutbu on 2009-07-19
Sorry, I got the syntax wrong. Try
```

export CVSROOT[COLOR="Red"]=[/COLOR]"$HOME/.cvsroot"

```
(Note the equals sign.)

---

### Post by ssubluesman on 2009-07-20
It works! Thank you very much.

---

