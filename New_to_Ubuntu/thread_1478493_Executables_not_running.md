---
title: "Executables not running"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by BT1 on 2010-05-09
Okay so when I try to install games in 10.04, I get this error:

> The file '/media/RA1/AUTORUN.EXE' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Now this is straight off the install disk, so I can't go in and click to run it as an executable in the permissions because it reports "this is read only"blah blah blah. I want to know if anyone has a way to make all .exes run as executables without the ubuntu executable bit stopping me. Here's a link to the official page about it:

[https://wiki.ubuntu.com/Security/ExecutableBit](https://wiki.ubuntu.com/Security/ExecutableBit)

Thanks for the assist!

---

### Post by tica vun on 2010-05-09
To make it executable just run 

```
chmod a+x filename
```

---

### Post by Method X on 2010-05-09
hello.
Don't know about disabling sticky bit, but try to copy all files to your pc and execute them from there :)

---

### Post by _0R10N on 2010-05-09
> **BT1 said:**
> Okay so when I try to install games in 10.04, I get this error:



Now this is straight off the install disk, so I can't go in and click to run it as an executable in the permissions because it reports "this is read only"blah blah blah. I want to know if anyone has a way to make all .exes run as executables without the ubuntu executable bit stopping me. Here's a link to the official page about it:

[https://wiki.ubuntu.com/Security/ExecutableBit](https://wiki.ubuntu.com/Security/ExecutableBit)

Thanks for the assist!

Are you trying to run this with WINE?

---

### Post by HotShotDJ on 2010-05-09
Comment deleted by author.  Based on the OP's subsequent comment, my comment is not relevant.

---

### Post by BT1 on 2010-05-09
> **_0R10N said:**
> Are you trying to run this with WINE?

Tried to install it through "PlayOnLinux" but it isn't in the list of approved stuff. I then tried to do the "install unsupported program" option, and it got me further than right clicking the install .exe and picking "open with wine..etc.". Whenever I do that, it gives me all the stuff up there.

How else would I install through wine?

---

### Post by BT1 on 2010-05-09
> **HotShotDJ said:**
> Comment deleted by author.  Based on the OP's subsequent comment, my comment is not relevant.

Because of this comment, you are literally a lot cooler to me lol.

---

### Post by cgroza on 2010-05-09
Right click on the executable and select properties the search something like allow execute  this file as a program and check it.

---

### Post by cogadh on 2010-05-09
What game are you trying to run? Not everything will work with Wine (POL is actually Wine).

---

### Post by themusicalduck on 2010-05-09
All exe files are disabled by default. Like cgroza said you need to right click on the file, Properties, Permissions tab and check the box Allow executing file as program.

---

### Post by BT1 on 2010-05-09
> **themusicalduck said:**
> All exe files are disabled by default. Like cgroza said you need to right click on the file, Properties, Permissions tab and check the box Allow executing file as program.

Yeah, the issue is that the files are on a CD which means the properties can't be changed, so when I try to check the box it refuses to do so and tells me "this is read only" blah blah blah. If it's a file that's not on CD, you can alter this but since it's CD it won't let me.

> What game are you trying to run? Not everything will work with Wine (POL  is actually Wine).A mixture of games, mostly the old command and conquer games but a more recent one (the one I'm working on now) is Command and Conquer 2 Red Alert. Installing other games don't give me such an issue because Halo installs through PlayOnLinux as a pre-set install option. Since Command and Conquer 2 isn't on the pre-set list, I tried to install it without POL. THAT is where I run into the .exe issue.

All I need to know is how to set all .exe files to executable by default. I don't need the additional protection that ubuntu has by default, I just need my stuff to work in a logical fashion, not in "kiddie-safe" mode. Anyone know a command, or a menu option?

---

### Post by themusicalduck on 2010-05-09
In that case, you could copy the contents of the CD into a folder somewhere on the harddrive. Then you can change the permissions and then run the exe from there. I'm not sure if there is a way of enabling it by default.

---

### Post by faldore on 2010-05-10
This really really really sucks.  I can not run any windows game cd's any more.  Time to roll back to previous version.  *sigh*

---

