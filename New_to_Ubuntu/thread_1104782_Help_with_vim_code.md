---
title: "Help with vim code"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by NeedingHelp on 2009-03-23
Hi

I need some code using vim to search for files created on a specified day and month in the current directory.

eg.

./file <March> <24>

If anyone could help me it would be appreciated.

---

### Post by yeats on 2009-03-26
As far as I know, Linux systems do not store the creation time, just the "last edited" time, which ls -l can get you.

---

### Post by KIAaze on 2009-03-26
I don't understand what you mean by "vim code".
You want to write a macro for vim?
Or do you just want one command-line opening all files from a given date in vim? (I'd rather do that with gedit or kate. :s )

edit: cf:
[http://www.unix.com/unix-dummies-questions-answers/14722-files-between-any-two-given-dates.html](http://www.unix.com/unix-dummies-questions-answers/14722-files-between-any-two-given-dates.html)
[http://www.unix.com/sun-solaris/28331-list-files-specific-date.html](http://www.unix.com/sun-solaris/28331-list-files-specific-date.html)
[http://www.unix.com/shell-programming-scripting/42573-search-files-excluding-binary-files.html](http://www.unix.com/shell-programming-scripting/42573-search-files-excluding-binary-files.html)

Then you can use something like:
```

#open results of find command with vim
findcommand | xargs vim
#to avoid binary files and directories:
findcommand -type f | xargs file | grep ASCII | cut -d: -f1 | xargs vim

```

---

### Post by albandy on 2009-03-26
stat filename

---

