---
title: "vi and vim.tiny - strange behavior?"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by BugBuster on 2010-09-14
I have noticed on this on Ubuntu as well as on Debian Testing.
Both these distros have vim.tiny installed by default and vi is provided via the alternatives system so vi actually is just a symlink to vim.tiny.
```
vi -> /etc/alternatives/vi -> /usr/bin/vi -> /usr/bin/vim.tiny
```

But the behavior is totally different when using these two. When you launch vim.tiny directly like 
```
$vim.tiny test.file 
```
it behaves perfectly like the old vi, however when we use it like
```
$vi test.file
```
it does not enter the insert mode easily. Also backspace does not work as it works in vim.tiny.

Have you guys noticed this? Is there a way we can make these two work alike?

---

### Post by BugBuster on 2010-09-14
OK...I figured it out. In /etc/vim there are two files vimrc and vimrc.tiny.

vimrc.tiny is used when vim.tiny is launched as vi through the alternatives system. I backed up the original vimrc.tiny and then copied vimrc as vimrc.tiny

Now both commands give the same behavior.

---

