---
title: "Do I really have to use gksu instead of sudo???"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by diablo75 on 2009-01-18
Every now and then I see some people make corrections like,

"You're supposed to be typing gksu gedit, instead of sudo gedit."

My reply:  Doesn't seem to make a damn bit of difference.  In the above example, typing sudo still works (for me anyway).  Gedit loads as root.  What's the big fuss about if it works either way?

---

### Post by Bachstelze on 2009-01-18
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by theozzlives on 2009-01-18
sudo gedit works, but gksu is supposed to be for GUI apps.

---

### Post by diablo75 on 2009-01-18
> **theozzlives said:**
> sudo gedit works, but gksu is supposed to be for GUI apps.

Like what?

---

### Post by mjheagle8 on 2009-01-18
in short, sudo runs the program with your profile and root priveleges. gksudo runs the program with the root profile.

---

### Post by diablo75 on 2009-01-19
I just saw someone tell someone else to use gksudo on dpkg.  That's not a GUI program, right?

---

### Post by Bachstelze on 2009-01-19
> **diablo75 said:**
> I just saw someone tell someone else to use gksudo on dpkg.  That's not a GUI program, right?

Indeed, in the case of dpkg, using sudo or gksudo makes no difference.

---

### Post by mjheagle8 on 2009-01-19
yeah, it is. you have the gui to install the package.

---

### Post by diablo75 on 2009-01-19
> **mjheagle8 said:**
> yeah, it is. you have the gui to install the package.

The terminal is a GUI?

---

### Post by pansz on 2009-01-19
sudo uses user's profile and root's previledge.
gksu uses root's profile and root's previledge.

Some applications works fine, but some applications will *only* work when your profile is root's profile. Especially, some gui-applications need root's profile. And it is always much safer to use root's profile when running root gui applications. (in order not to damage your users profile environment)

gksu is not meant to run gui or cli applications, it is meant to use the root profile, when you wan to use root profile you use gksu instead of sudo, if your user profile is the same as your root profile you will not notice much differences.

---

### Post by mjheagle8 on 2009-01-19
dpkg has a gui.

---

### Post by Bachstelze on 2009-01-19
> **mjheagle8 said:**
> dpkg has a gui.

And how is it called, please?

---

### Post by mjheagle8 on 2009-01-19
gdebi package installer?

---

### Post by Vantrax on 2009-01-19
> **pansz said:**
> sudo uses user's profile and root's previledge.
gksu uses root's profile and root's previledge.


What about gksudo compared to gksu? Wouldnt they have the same relationship as sudo and su

---

### Post by kerry_s on 2009-01-19
use what you want, if it breaks it's on you.

---

### Post by overdrank on 2009-01-19
> **diablo75 said:**
> Every now and then I see some people make corrections like,

"You're supposed to be typing gksu gedit, instead of sudo gedit."

My reply:  Doesn't seem to make a damn bit of difference.  In the above example, typing sudo still works (for me anyway).  Gedit loads as root.  What's the big fuss about if it works either way?

Are you speaking of [My Post]("http://ubuntuforums.org/showthread.php?p=6573469#post6573469") :)

---

### Post by mcduck on 2009-01-19
> **mjheagle8 said:**
> gdebi package installer?

Well, then you'd run "gksudo gdebi" to start it.

Running "gksudo dpkg" will not magically start gdebi instead of dpkg.. ;)

Anyway, starting GUI apps with "sudo" instead of "gksudo" means you take the chance of breaking your user's home directory's ownership/permissions, just because you didn't want to type the extra 2 letters. Rather stupid risk to take, if you ask me.

---

