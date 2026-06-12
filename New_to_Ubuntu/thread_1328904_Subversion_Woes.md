---
title: "Subversion Woes"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by anothrguitarist on 2009-11-16
I'm working on a project on both Windows and Linux. I checked out and commited a repository on Windows, and it worked great. On Linux, however, it says that it is unable to open ra_local session. Does anyone have a solution?

---

### Post by anothrguitarist on 2009-11-17
Bump

---

### Post by snl2587 on 2009-11-17
What version of svn are you using (for both)?

---

### Post by anothrguitarist on 2009-11-18
Windows: 1.6.6
Linux:   1.6.5 (r38866)

---

### Post by snl2587 on 2009-11-18
What happens if you start off the repository in Linux (the older version)?

---

### Post by anothrguitarist on 2009-11-18
The repository didn't work on windows that time, but I found the source of the problem. The path to the repository changes. On Linux, it's file:///media/... On Windows it's file:///C:\Documents\ and\ Settings\...

Any idea how to make it work from both Windows and Linux?

---

### Post by snl2587 on 2009-11-18
> **anothrguitarist said:**
> The repository didn't work on windows that time, but I found the source of the problem. The path to the repository changes. On Linux, it's file:///media/... On Windows it's file:**///C:\**Documents\ and\ Settings\...

Any idea how to make it work from both Windows and Linux?

Note where I bolded part of the string for Windows. I would recommend trying simply "file:///Documents\ and\ Settings\... " and seeing if that works, or else try something on this page: [http://www.svnforum.org/2017/viewtopic.php?t=1081](http://www.svnforum.org/2017/viewtopic.php?t=1081)

Hopefully either the path change or something there will fix your problem.

---

### Post by snl2587 on 2009-11-26
Did that work for you?

---

