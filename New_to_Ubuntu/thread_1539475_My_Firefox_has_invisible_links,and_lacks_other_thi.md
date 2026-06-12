---
title: "My Firefox has invisible links,and lacks other things"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by Ben_222 on 2010-07-26
Anyone else have this problem?Am I lacking Java or what?I have links on some pages that are invisible:I can move the cursor over the space where they SHOULD be visible.Also, there are some web pages where you put in usernames and passwords to join a site, and even THAT did not show up.I had to go to my Windows computer to join a forum.Also, the graphics on some pages are not as good....and it is not a video card issue,cause I switched video cards on these computers, and nothing changed.Any help would be appreciated!

---

### Post by collinp on 2010-07-26
Try running Firefox in a terminal session (just open a terminal, type firefox, then hit enter) and paste the output from that to here. If it is an issue with Firefox itself, there will be some form of output on the terminal because of it.

---

### Post by Ben_222 on 2010-07-26
Ok,collinp,I did that,and it just opened Firefox;no output at all in the terminal.

---

### Post by collinp on 2010-07-26
> **Ben_222 said:**
> Ok,collinp,I did that,and it just opened Firefox;no output at all in the terminal.

Hrm, that's odd.

Do you have any extensions or Firefox settings that you're worried about losing?

---

### Post by Ben_222 on 2010-07-26
collinp.No,actually right now the only thing I have is plugins.But one of them are under 'extensions" and it it the QuakeLive game launcher,and also "Ubuntu Firefox Modifications".QuakeLive game Launcher is also listed under plugins. I do not want to lose QuakeLive

---

### Post by collinp on 2010-07-26
> **Ben_222 said:**
> collinp.No,actually right now the only thing I have is plugins.But two of them are under 'extensions" and it it the QuakeLive game launcher,and also "Ubuntu Firefox Modifications".QuakeLive game Launcher is also listed under plugins. I do not want to lose QuakeLive

If it was necessary, could you reinstall QuakeLive?

---

### Post by Ben_222 on 2010-07-26
collinp,Sure,I could do that

---

### Post by jtarin on 2010-07-26
What version of Firefox are you running? What version of Ubuntu?

---

### Post by Ben_222 on 2010-07-26
jtarin,Firefox3.6.7   and Ubuntu9.10

---

### Post by jtarin on 2010-07-26
> **Ben_222 said:**
> jtarin,Firefox3.6.7   and Ubuntu9.10
I've had some issues with my mouse in Firefox, same version since I upgraded, but I also have the same problems in a recent new install of Chromium. Very errtic mouse behavior at times....jumps around, starts scrolling, does its own right-click and some links and ads show as gray blocks.

---

### Post by wojox on 2010-07-26
Scroll down through here. It may help [Common Issues & Solutions]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html")

---

### Post by lidex on 2010-07-27
Use the Alt+F2 run dialog and enter this:
```
firefox -ProfileManager
```
Start a new profile and see if you get the same behavior.

---

