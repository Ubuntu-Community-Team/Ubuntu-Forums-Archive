---
title: "Setting PATH for new TexLive installation"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by dawrobel on 2011-01-18
Hi, I'm very new to ubuntu and am trying to installing the TexLive distribution on my computer. I followed the instructions on [http://www.tug.org/texlive/quickinstall.html](http://www.tug.org/texlive/quickinstall.html)

but am now stuck on what to do with setting the PATH :-(

I tried looking online for some help but I don't quite understand some of the other posts that I've seen. Am I supposed to edit the hidden file in my home directory named .bashrc?

---

### Post by TheWeakSleep on 2011-01-19
To add a directory to the PATH, edit the file called .bashrc in your home folder and append something similar to

```
export PATH=$PATH:/path/to/directory
```

---

