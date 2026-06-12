---
title: "Automation software - suggestions wanted"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by peterrudin on 2010-11-16
Hi all,

What I would like to be able to do is open a webpage, select all the text, copy it to the clipboard and then paste it into a form on a second page and then submit the form.

Under windows there are several macro recording tools that could do this and repeat the precess at scheduled times.

Can anyone suggest a tool I could use to achieve this under unbuntu. I am using 10.10

Thanks in advance.

---

### Post by cavh on 2010-11-16
Have a look at Deixto

[http://www.deixto.com/]("http://www.deixto.com/")

Haven't used it myself but ran across it while researching something else.

---

### Post by peterrudin on 2010-11-16
Thanks, I will check it out.

I had a look this morning and it falls foul of the same issues that my existing screen scrapper written in php.

What I want to grab is selectable text on screen but is not in the source code. The page source has a stack of regex expressions that pull the individual digits of a set of floating point numbers out of a block of strings. This means that the user can see the text and can select the text and copy/paste it, but the text is not present in the source code. I can extract it easily using a windows macro recorder but I don't want to use windows.

I will try and run one of these windows tools under WINE that may be a solution.

---

### Post by cavh on 2010-11-17
Cool, please let us know how the Wine alternative works, so other forum users running into this can learn :)

---

### Post by peterrudin on 2010-11-17
AutoHotKey works perfectly under wine on ubuntu 10.10,
it doesn't appear to do what I want, but it looks generally quite good.
AceMacro 2.1 installs and runs, but has an error about not finding data
MagicMacro installs but doesn't run.

I will feedback as I investigate further.

---

### Post by cavh on 2010-11-20
Maybe some research on the Mono project website would be useful?

[http://www.mono-project.com/Main_Page]("http://www.mono-project.com/Main_Page")

---

### Post by peterrudin on 2010-11-20
I have found 2 answers to my question

* AutoHotKey runs under Wine so gives you cross platform macros. On my system it has a few issues but there is forum devoted to getting AutoHotKey running.

* Xnee is native Linux. It can be installed easily from the Ubuntu software centre. I just did not know it existed when I asked my question here originally.

I am using Xnee.

---

