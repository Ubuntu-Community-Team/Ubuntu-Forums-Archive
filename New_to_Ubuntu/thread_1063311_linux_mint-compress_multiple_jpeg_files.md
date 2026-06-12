---
title: "linux mint-compress multiple jpeg files"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by irish66 on 2009-02-07
cancelled

---

### Post by hansdown on 2009-02-07
Hi irish66.

Here are some good choices.

[http://www.google.ca/search?q=compress+multiple+jpeg+files+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=compress+multiple+jpeg+files+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by irish66 on 2009-02-07
oh. that was quick. I found that the program I was using could do the job, i was looking for. BUt thanks for replying.
M

---

### Post by krzysz00 on 2009-02-07
_Underlined text can possibly be ignored, but contains detailed info about some Terminal tricks_
Yes.  But it involves the terminal. The instructions go like this. (assuming your pictures are in [your home directory]/Pictures/somedir
1. Type cd Pictures/somedir
Of course, you can, for example start typing Pictures and somewhere in the name , hit _TAB. Either the name of the directory will be completed and you can do the same with somedir, or you will hear a beep. If you hear a beep, hit TABB again. If a list of files and directories comes up, keep typing until that doesn't happen. If nothing comes up there may be a spelling error earlier in the name or your two TAB presses weren't close enough._
2. Once you are in whatever directory the pictures are in type (or copy-and-paste):
```
tar -cvzf pictures.tar.gz *
```This will creata a file named pictures.tar.gz with every file in that directory, the .tar.gz can be opened on any Linux of UNIX system. (Windows users will need to download something).
**They beat me to it, but this stuff might be well worth reading.**

---

