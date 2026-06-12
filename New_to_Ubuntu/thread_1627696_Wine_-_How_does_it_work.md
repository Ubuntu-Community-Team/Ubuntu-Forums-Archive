---
title: "Wine - How does it work?"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by schwaigern on 2010-11-21
Greetings Community,

I've been running Ubuntu for 2 days now, and I can't figure out how to use wine.

I right click on the .exe that I want to run, then select "Open with Wine" and get this message:

The file '/home/schwaigern/Desktop/SoftonicDownloader_for_pivot-stickfigure-animator.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

I have no idea what to do, and I have searched the forums/internet for an answer. Can anyone help?

Thank you in advance,
schwaiger

---

### Post by Naitsirhc Hsem on 2010-11-21
right click on the file and select properties
go to the permissions tab
and check allow executing file as a program
tada

---

### Post by blancoisgod on 2010-11-21
I had this problem.

right click the file you want to run, hit properties. From there, go to the permissions tab, and make sure the box fro running the executable file is checked

---

### Post by schwaigern on 2010-11-21
You guys are heroes, thanks!

---

### Post by Hippytaff on 2010-11-21
or if you want to you can open a terminal (CTRL+ALT+T) and
```

cd /path/to/exe

```ie
```

cd /Downloads

```then
```

chmod +x filename

```to change the file to executable...but I do love the command line and[ [COLOR=Black]Naitsirhc Hsem[/COLOR]]("http://ubuntuforums.org/member.php?u=1044364")[COLOR=Black]'s[/COLOR] suggestion suits most people better :-)

---

