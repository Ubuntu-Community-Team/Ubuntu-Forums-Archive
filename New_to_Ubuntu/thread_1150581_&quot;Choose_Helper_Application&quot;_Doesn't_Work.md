---
title: "&quot;Choose Helper Application&quot; Doesn't Work"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Bezmotivnik on 2009-05-06
When downloading with Firefox (which seems to be crash-prone, but that's another issue) I want to open a torrent with Vuze, and I am given a GUI to choose a helper application to open the file with -- and it shows no helper applications, just irrelevant files.

Apparently this is a common problem as I see lots of questions about it on Google, but no answers.

Thanks for any help on this.

---

### Post by mcduck on 2009-05-06
> **Bezmotivnik said:**
> When downloading with Firefox (which seems to be crash-prone, but that's another issue) I want to open a torrent with Vuze, and I am given a GUI to choose a helper application to open the file with -- and it shows no helper applications, just irrelevant files.

Apparently this is a common problem as I see lots of questions about it on Google, but no answers.

Thanks for any help on this.

What do you mean with "irrelevant files"? 

If Firefox opens a file browser to find the app, then it needs you to find the executable for the program you want to use. In most cases you will find the executable file in /usr/share/bin.

---

### Post by glotz on 2009-05-06
Drop to a terminal and type ```
which vuze
```

---

### Post by blueridgedog on 2009-05-06
I too have noticed the latest update of firefox seem to be unable to open files I download.  I have taken to saving items to the desktop and then opening them.  I suspect that the issue will be resolved with the next update and have not really searched for a solution.

---

### Post by Bezmotivnik on 2009-05-06
> **mcduck said:**
> In most cases you will find the executable file in /usr/share/bin.
I don't see this path in the available file system.

---

### Post by Bezmotivnik on 2009-05-06
> **glotz said:**
> Drop to a terminal and type ```
which vuze
```

Whoa!

anonymous@BELTFEED:~$ which vuze
/usr/bin/vuze

That was easy!  Thanks!

---

### Post by glotz on 2009-05-06
No worries! :)

---

### Post by mcduck on 2009-05-06
> **Bezmotivnik said:**
> I don't see this path in the available file system.

Sorry, what I meant was "/usr/bin".. :)

---

### Post by Bezmotivnik on 2009-05-06
Yeah, that kind of threw me because a similar situation actually presentled me with the possible programs directly.

Anyhow...I got Vuze in and it works fine.  Now...for MoBlock (or whatever it's calling itself this week :rolleyes:).

---

